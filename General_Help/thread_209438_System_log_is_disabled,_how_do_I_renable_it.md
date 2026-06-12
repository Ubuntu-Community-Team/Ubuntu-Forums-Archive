---
title: "System log is disabled, how do I renable it?"
date: 2006-07-05
forum: General Help
---

### Post by matrooswolf on 2006-07-05
Well, the title says it all ;)

In more words:

My system log (in /var/log/messages) is disabled I think.
I get no new entries since 4th februari.

And I need it because I have NXserver problems (see my other thread Nx key problem? [http://www.ubuntuforums.org/showthread.php?p=1215930#post1215930](http://www.ubuntuforums.org/showthread.php?p=1215930#post1215930)) which generate error codes that point to /var/log/messages, but there is nothing new in it since 4th februari ...

and I am hoping to find more info in there about what is wrong with my NXserver

---

### Post by Ramses de Norre on 2006-07-05
```
sudo ln -s /etc/init.d/sysklogd /etc/rc2.d/S10sysklogd
```

---

### Post by matrooswolf on 2006-07-05
Hi Ramses de Norre,
tried that (I don't understand what it does), 
but no new messages.  (And I tried my NXserver error thing, which should have generated a new error ...)

I try to access the log with System > administration > systeemlogboek (I don't know this in english, but you understand I think ;)
Or directly form /var/log/messages

but only messages from the 4th februari :confused:

---

### Post by Ramses de Norre on 2006-07-05
The command I gave you makes a symlink so that the service starts on bootup, so it's normal that it doesn't start untill your next reboot. do ```
sudo /etc/init.d/sysklogd start
``` to start it immediately.
(and dutch is my native language so no problem understanding you;))

---

### Post by matrooswolf on 2006-07-05
Hi Ramses di Norre,
thanks!! 
That did it!
I finally have error messages! :grin: 

I never thought I would be so happy to view error messages ;))

(yes, i knew, from antwerpen myself ;))

---

