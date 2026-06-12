---
title: "Logging in Problem plz HELP!"
date: 2008-01-07
forum: General Help
---

### Post by renzo461 on 2008-01-07
this is my first time using Xubuntu linux i was messing around with it and went to users and deleted my user account and i only saw the root account now i dont know how to get into Xubuntu i type root as username and put my password and it ddin't work and i dont know what to do if someone can help me pls i would really appreciate it.:)
i would like ot know how to get into terminal pls too :)

---

### Post by renzo461 on 2008-01-07
come on guys pls help me i am a noobi1 [-o<

---

### Post by PeterJS on 2008-01-07
The root account is 1) disabled by default for security purposes 2) explicitly disallowed from logging in graphically (even if enabled) because that's a more dangerous idea than logging in as root in general. 3) Doesn't and shouldn't have the same password as your user account.

To get back in to your system load up in recovery mode, create a new user and add them to the admin group. After that reboot and login as your new user. First thing you're going to want to do is right click on the users widget in the top panel and select Edit Users and Groups, select properties for your new user and re-add privileges on the user privileges tab as needed.

---

### Post by Seisen on 2008-01-07
You can boot into recovery mode which is the second kernel option and says recovery mode. Once that boots up you will be root enter this command 

```
adduser newuser
``` change newuser to whatever you want your username to be then 
```
passwd newuser
``` to add a password. Once you are done with that reboot.

---

### Post by renzo461 on 2008-01-07
how do i go to kernel options i just installed Xubuntu yesterday so i am very noobie only used it for 1 hour pls help thnx :)

---

### Post by p_quarles on 2008-01-07
When the "GRUB loading" notice comes up on your screen (right after the BIOS) press the escape key, and you'll see the menu. Select "Recovery mode."

---

### Post by slackerov on 2008-01-09
> **Seisen said:**
> You can boot into recovery mode which is the second kernel option and says recovery mode. Once that boots up you will be root enter this command 

```
adduser newuser
``` change newuser to whatever you want your username to be then 
```
passwd newuser
``` to add a password. Once you are done with that reboot.

I was having the same problem and that worked great!  Thank you!  How do I add the new account to the administrators group?

Thanks in advance!

---

### Post by slackerov on 2008-01-09
Figured it out.  For anyone else that needs it:

adduser username admin

That will add you to the admin group.:guitar:

---

