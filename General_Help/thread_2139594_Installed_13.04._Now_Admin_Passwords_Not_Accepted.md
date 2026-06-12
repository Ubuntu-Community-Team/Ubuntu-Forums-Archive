---
title: "Installed 13.04. Now Admin Passwords Not Accepted"
date: 2013-04-27
forum: General Help
---

### Post by Mr Fredrick on 2013-04-27
Hi All,

I have successfully ugraded to Raring Ringtail and so far all is well. However some applications, such as Gnome Commander and hp-setup, that request my admin password, do not accept my input. How can I solve this problem, please note that I can log in OK using the same password and apps like Synaptic accept it.
Thanks in advance,

Mr Fredrick.

---

### Post by coffeecat on 2013-04-27
It sounds as though you need to set sudo mode from gksu-properties. Run this from a terminal:

```
gksu-properties
```

If authentication mode is set to "su", change this to "sudo" and you should be OK. If this doesn't work, post back.

Background: there's been a change in Raring. It doesn't come with gksu pre-installed - it's on the live session but doesn't get to be installed to the permanent installation. If you install the package gksu it defaults to su mode and needs to be changed to sudo as above. It's likely that you didn't install gksu yourself, but that it was brought in as a dependency with another package that you have installed. That's if su/sudo mode is the problem here.

---

### Post by timgood on 2013-04-27
Yes, that is the problem. Why gksu has been left out is anyone's guess. Not mine. Particularly as many forum posts and Howtos rely on the editing of files owned by root and tell you to use 'gksu gedit filename'. Leaving it out was a big mistake.

---

### Post by coffeecat on 2013-04-27
Guessing is not necessary, and no mistake. It's a policy decision to replace gksu with pkexec. This is the best explanation I could find in a hurry:

[http://askubuntu.com/questions/284306/why-is-gksu-no-longer-installed-by-default-in-raring-13-04/284717#284717](http://askubuntu.com/questions/284306/why-is-gksu-no-longer-installed-by-default-in-raring-13-04/284717#284717) 

No doubt there is more background to this thinking in the dev mailing lists somewhere.

---

### Post by Mr Fredrick on 2013-04-27
Thank you for your replies, it solved my problem, otherwise I thought I would have to do a complete upgrade, and is very much appreciated.

---

### Post by Amleth C on 2013-05-23
Useful, thanks.

---

### Post by RWEW on 2013-05-30
Timely & needed info.  Thanks
:KS

---

