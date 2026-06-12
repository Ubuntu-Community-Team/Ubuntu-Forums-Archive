---
title: "free talk configuration, help needed"
date: 2008-06-03
forum: General Help
---

### Post by ramkumail on 2008-06-03
I wanted to try freetalk, a console based jabber client with gmail id for chat because the developer promises voice support and file transfer for gtalk very soon. the configuration file(home/.freetalk/freetalk.scm) of mine looks like this.
> ; (ft-set-jid! "uname@gmail.com")
; (ft-set-server! "talk.google.com")
; (ft-set-password! "psswd")
; (ft-set-prompt! "~\\/~ ")
; (ft-set-sslconn! #t)
; (ft-set-port! 5222)
; (add-hook! ft-login-hook
; 	   (lambda (status)
; 	     (if status
; 		 (ft-set-status-msg! 
; 		  "i use freetalk http://freetalk.nongnu.org"))))
I changed the port from 5223 to 5222 after seeing the configuration in my pidgin(see screen shot). There is something about ssl while ssl is not selected in pidgin settings. There is something else selected in pidgin. Is there a mistake here for the following problem.
[[IMG]http://img217.imageshack.us/img217/8530/screenshotmodifyaccountar7.th.png[/IMG]](http://img217.imageshack.us/my.php?image=screenshotmodifyaccountar7.png)

After changing and saving the file, If i start freetalk and give username as 'uname@gmail.com' and pssword, it gives me the following output.
> goal@goal-desktop:~$ freetalk
Loading dictionary [/usr/share/dict/words]... [98569] words
Jabber ID: [email]uname@gmail.com
Password: 
Connecting ...
Failed to resolve server: No such file or directory
~\/~ 

What am i missing to get it working. by the way i have never used a console chat client. Please help. Thanks in advance.

---

### Post by ramkumail on 2008-06-04
bump

---

