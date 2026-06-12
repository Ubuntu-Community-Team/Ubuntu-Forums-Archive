---
title: "Setting up apache and digest"
date: 2008-07-10
forum: General Help
---

### Post by hoooootz82 on 2008-07-10
Hello, I'm trying to set up an apache webserver to use the digest authorization module, and I'm having trouble setting up the username and password file.
```
sudo htdigest -c /var/www/digest realm username
```
I've tried to figure out what the "realm" argument is, but I still haven't figured it out. If anyone can give me a more detailed explanation other than "The realm name to which the user name belongs." I would be very thankful. Any help would be appreciated. Wasn't sure where to post this, feel free to move this post..

---

### Post by cariboo on 2008-07-10
It's not a lot but this may help:

[http://httpd.apache.org/docs/2.0/programs/htdigest.html](http://httpd.apache.org/docs/2.0/programs/htdigest.html)

Jim

---

### Post by master_kernel on 2008-07-27
[http://httpd.apache.org/docs/2.2/howto/auth.html](http://httpd.apache.org/docs/2.2/howto/auth.html)

The realm must match whatever AuthName is for digest to work.

---

### Post by webwolf_3000 on 2009-05-11
Hear Hear, the description isnt great.

Realm is whatever you define for "AuthName" in your .htaccess or <Directory> statements.

so for example:

		AuthType Digest
		AuthName "RealmFTL"
		AuthUserFile /secure/directory/passwd
		Require user userlogin

you would run from the command line:
"sudo htdigest -c /secure/directory/passwd RealmFTL userlogin"

Note that not all browsers support Digest, Online docs suggest that IE above v5 does, I can confirm IE8 Does NOT! support Digest... FireFox3 does Support Digest :)

Hope this helps somebody.

:guitar:

---

