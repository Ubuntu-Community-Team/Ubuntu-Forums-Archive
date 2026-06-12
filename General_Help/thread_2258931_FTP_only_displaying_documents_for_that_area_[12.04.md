---
title: "FTP only displaying documents for that area [12.04]"
date: 2014-12-31
forum: General Help
---

### Post by Lawrence_Macmillan on 2014-12-31
Hello,

I have googled this for ages, not really seeing a concise answer so I posted here, basically I have a root user and a ftpuser account (latter is indeed for FTP) basically I want to upload a theme via wordpress... yes thats it!

However, when connecting via FTP I can only see folders I have manually created, how do I grant ftpuser access to all files? I literally only need this for a wordpress theme and nothing else, even contacted my VPS provider with no concise answer. I assume its something basic I've missed however I would appreciate the help,

Cheers

---

### Post by nerdtron on 2014-12-31
FTP is unsecure. And granting write permissions on on system folders is also unsecure.

Can you SSH to the server? Just zip your theme first. Then use Filezilla (or WinSCP) to upload the theme on the server.
Next ssh on the server and put the theme on it's correct directory, and extract it.

---

### Post by Lawrence_Macmillan on 2014-12-31
Thanks for the reply,

Problem is I've already done this several times, yet it doesn't appear in Wordpress, I'm not bothered about the security of FTP because I plan to scrap it after this anyway, just a pain for a simple theme for a wordpress site :mad:

---

### Post by nerdtron on 2014-12-31
> **Lawrence_Macmillan said:**
> 
Problem is I've already done this several times, yet it doesn't appear in Wordpress,

If the theme is already on the correct location on the server, and wordpress still doesn't recognize it, ftp won't fix anything. 
Changing the method of upload will result on the same thing. So if wordpress doesn't detect the theme that is already on the server, that is the one we need to fix.

What are the requirements for installing the wordpress theme? What folder should you put your theme? what are the folder permissions are the other themes that wordpress detects?

---

### Post by Lawrence_Macmillan on 2014-12-31
Hello,

I would asume by uploading it into WP using their upload method (ftp) would help, I hate wordpress.

To install a wordpress theme it needs to be uncompressed (done) and have /theme name/contents of theme, and not /theme name/theme name/contents which is also done.

Themes should be in "/wp-content/themes" which is done

Permissions are 755 which mine are, however it won't recognise the theme, nothing ever works does it!

Thank you

---

### Post by nerdtron on 2014-12-31
Hmmm.. seeing at my test install of wordpress and it themes.. here is the location and the permissions.
```
me@test-pc:/var/www/html/wp-content/themes$ pwd
/var/www/html/wp-content/themes
me@test-pc:/var/www/html/wp-content/themes$ ll
total 20
-rw-r--r-- 1 www-data www-data   28 Jun  5  2014 index.php
drwxr-xr-x 8 www-data www-data 4096 Dec 10 11:24 minamaze/
drwxr-xr-x 9 www-data www-data 4096 Nov 20 09:42 twentyfourteen/
drwxr-xr-x 8 www-data www-data 4096 Nov 20 09:42 twentythirteen/
drwxr-xr-x 7 www-data www-data 4096 Nov 20 09:42 twentytwelve/

```

Are you sure you uploaded on correct directory and the correct permissions? Also, are you sure that your theme is compatible with wordpress?

---

### Post by Lawrence_Macmillan on 2014-12-31
Okay,

I don't have anywhere else to put the themes, the default themes were in the directory my theme is now (I have deleted them, yet they still show up?) I really wish I could do this in traditional HTML it is so much easier.

---

