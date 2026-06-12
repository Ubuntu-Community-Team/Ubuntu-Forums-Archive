---
title: "Problem with permissions"
date: 2016-08-09
forum: General Help
---

### Post by sc00rpy on 2016-08-09
Hello, I'm new to linux and want to host a website on dedicated server, I put the php files in the public "www" directory along with private folder that should be accessed only by the server itself (I mean php scripts writing and reading files in the folder). I read that the Apache server operates under account "www-data", so I set that account as folder owner with permissions 700, but I can still access this folder from web browser at home, until I remove the www-data permissions. Is it normal that the website visitors use the same account as web server? If so, how can I configure the permissions correctly so only PHP script can access the files within dir?

Here's my test file and it's permissions

[http://5.39.78.24/prywatny/test.txt](http://5.39.78.24/prywatny/test.txt)
-rwx------ 1 www-data www-data 4 sie  9 08:28 test.txt


Best regards

---

### Post by SeijiSensei on 2016-08-09
Yes, it's perfectly normal and reflects the way Apache (and many other server daemons) is designed.  The server process runs as www-data so that any compromises would also have just www-data permissions and not be able to do much to damage the server.  Thus any files displayed by the web server must have permissions allowing the www-data user to read them.

That said, I'm not certain I understand the rest of your question.  PHP scripts have the same permission issues as any file you might store in /var/www/html.  If you are worried that someone can read the code, that's not possible with just a web browser.  Apache+PHP send just the rendered page to the browser hiding all the code.  If that's not what concerns you, you need to ask the question again.

In practice I put nearly all the code for the sites I build into separate directories outside the web root.  The publicly-visible index.php page uses the require() and include() functions in PHP to incorporate the code into the rendered page. The code files use ".inc" as their extension.  Even if someone could find such a page, it cannot be downloaded because I have the rule
```

<Files ~ "\.inc$">
    Order allow,deny
    Deny from all
    Satisfy All
</Files>

```
in my Apache configuration.  [More details here](https://ubuntuforums.org/showthread.php?t=2317080&p=13455297&viewfull=1#post13455297).

---

### Post by sc00rpy on 2016-08-10
Thank you very much, I followed your advice and placed the files outside  root directory, I just wanted make sure that no one could access them  directly via http request, but they could be reached by PHP scripts in  root dir, and this solution seems to work great.

---

