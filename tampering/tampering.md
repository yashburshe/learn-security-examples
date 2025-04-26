# Tampering

This example demonstrates tampering through script injection.

## Steps to reproduce

1. Install all dependencies

    `npm install`

2. Start the **insecure.ts** server

    `npx ts-node insecure.ts`

3. In the browser, type a potentially malicious script in the name field of the form

    ```
        <script> document.body.innerHTML = "<a href='https://google.com'> Gotcha </a>"</script>
    ```

4. Do you see the potentially malicious hyperlink being injected into the form?

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**

Since the input is unsanitized, there are a lot of potential vulnerabilities on the sever relating to code injecting and remote code execution. Namely in this case, the vulnerability being exploited is tampering where the attacker changes the website content through the input field.

2. Briefly explain how a malicious attacker can exploit them.

In insecure.ts we take an input from the user. But this input is not sanitized which means that the user can type anything and we take the input as it is before doing any pre-processing. This opens up the website to injection vulnerabilities where a user can input malicious text such as javascript code which is then directly executed on the server and can tamper with the website.


3. Briefly explain why **secure.ts** does not have the same vulnerabilties?

In secure.ts we sanitize the input before we "execute" it by replacing the special characters with their character reference which would change something like "\<script\>" to "\&lt;script\&gt;" which turns it into a harmless string.