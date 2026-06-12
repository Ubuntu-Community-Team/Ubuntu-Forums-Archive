---
title: "Help deal with &quot;init&quot; issue of Ubuntu 10.04"
date: 2012-12-06
forum: General Help
---

### Post by pellyhawk on 2012-12-06
My laptop is dial boot OS(Windows XP & Ubuntu 10.04). Maybe many people will tell me to upgrade to 12.04. But what OS is used is not decided by me but my company's IT engineers.

However, I met an issue while every time I start ubuntu. I get a message "init: ureadahead main process (***) terminated with status 5"

What's wrong with ubuntu?

Especially, if I hope to restart ubuntu, the command:```
[COLOR="Red"]init[/COLOR] 1
``` always failed.

Ubuntu is able to shut down successfully but not restart. My screen will show different colors and flick ceaselessly. Thus I have to power off my laptop and then power on.

I guess the 2 issue is related since they are all "[COLOR="Red"]init[/COLOR]" issues.

How to fix my issues? Many thanks.

---

### Post by pellyhawk on 2012-12-08
bump

---

### Post by rnerwein on 2012-12-08
> **pellyhawk said:**
> My laptop is dial boot OS(Windows XP & Ubuntu 10.04). Maybe many people will tell me to upgrade to 12.04. But what OS is used is not decided by me but my company's IT engineers.

However, I met an issue while every time I start ubuntu. I get a message "init: ureadahead main process (***) terminated with status 5"

What's wrong with ubuntu?

Especially, if I hope to restart ubuntu, the command:```
[COLOR=Red]init[/COLOR] 1
``` always failed.

Ubuntu is able to shut down successfully but not restart. My screen will show different colors and flick ceaselessly. Thus I have to power off my laptop and then power on.

I guess the 2 issue is related since they are all "[COLOR=Red]init[/COLOR]" issues.

How to fix my issues? Many thanks.
hello
as i know is:      init 1  = single user
and to reboot: init 6 = reboot

this are the known from DEC, SOLARIS and HP ( in former times)
but in ubuntu is the default runlevel 2 (with everything - net,nfs ....)

the version 12.04 is know changing to "upstart" why i don't know. there is now no inittab in /etc present ( i found this old version easy to handle).
the reason to change is that 10.04 is out of service. 12.04 is a LTS ( how long ??? )
if they want to change i hope they are clever enough to run the 12.04 or higher parallel on one box for a time (what's new on new software --> new errors :-)   )
cheers

---

### Post by pellyhawk on 2012-12-09
> **rnerwein said:**
> hello
as i know is:      init 1  = single user
and to reboot: init 6 = reboot

this are the known from DEC, SOLARIS and HP ( in former times)
but in ubuntu is the default runlevel 2 (with everything - net,nfs ....)

the version 12.04 is know changing to "upstart" why i don't know. there is now no inittab in /etc present ( i found this old version easy to handle).
the reason to change is that 10.04 is out of service. 12.04 is a LTS ( how long ??? )
if they want to change i hope they are clever enough to run the 12.04 or higher parallel on one box for a time (what's new on new software --> new errors :-)   )
cheers

Thank you for your reply:). But I still have several questions.

1) While running VMWare Ubuntu 10.04, "init 1" is OK and I was surprised.

2) "init 6" is reboot indeed. However, I type "man init" in terminal and cannot look up init's options, such as 0, 1, 2, 3, 4, 5, 6. 

3) How to deal with "init: ureadahead main process (***) terminated with status 5", and is this an important bug needed to be fixed?

---

### Post by johnycsf on 2012-12-09
a small problem with that is ....
10.04 is VERY outdated!!

---

### Post by pellyhawk on 2012-12-09
> **johnycsf said:**
> a small problem with that is ....
10.04 is VERY outdated!!

Yeah, I know. However, which OS is used is not decided by me but my company's IT administrators. 

Would you please clarify my questions?

1) While running VMWare Ubuntu 10.04, "init 1" is OK and I was surprised.

2) "init 6" is reboot indeed. However, I type "man init" in terminal and cannot look up init's options, such as 0, 1, 2, 3, 4, 5, 6. 

3) How to deal with "init: ureadahead main process (***) terminated with status 5", and is this an important bug needed to be fixed?

Thanks.

---

### Post by claracc on 2012-12-09
Looking for a little you can find very good information here.

[http://ubuntuforums.org/showthread.php?t=1423305](http://ubuntuforums.org/showthread.php?t=1423305), this is a thread where the problem you report is explained and various working workarounds propossed.

Ubuntu 10.04 lucid lynx is a solid rocks system, which is supported till april 2013. So no outdated yet but very reliable and working.

---

