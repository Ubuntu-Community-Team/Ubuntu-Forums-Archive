---
title: "[SOLVED] AppArmor for Ubuntu 7.04"
date: 2007-08-28
forum: General Help
---

### Post by PmDematagoda on 2007-08-28
I just installed apparmor through Synaptic Package manager but i don't know how to bring up it's user interface, does anyone who uses apparmor know how to do this?

---

### Post by yopnono on 2007-08-28
[http://www.linuxalert.org/ubuntu/apparmor/README](http://www.linuxalert.org/ubuntu/apparmor/README)
[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)
[http://en.opensuse.org/Apparmor](http://en.opensuse.org/Apparmor)

---

### Post by yopnono on 2007-08-28
More:
[http://outflux.net/blog/archives/2007/04/02/apparmor-now-in-feisty/](http://outflux.net/blog/archives/2007/04/02/apparmor-now-in-feisty/)

---

### Post by PmDematagoda on 2007-08-28
Now i heard about Skype and that it invades your privacy, if i wanted to set up Apparmor against it how would you do that?(I read yopnono's last link and know that to confine a program you must define what the program cannot access).

I would appreciate any help.:popcorn:

---

### Post by nowshining on 2007-08-28
lolz I got the Gutsy Version altho it didn't show in the gutsy updates somehow something invoked it to download, lolz.. :) i installed some gutsy stuff thru the gutsy packages for feisty - some work with ubuntu...

---

### Post by PmDematagoda on 2007-08-28
> lolz I got the Gutsy Version altho it didn't show in the gutsy updates somehow something invoked it to download, lolz..  i installed some gutsy stuff thru the gutsy packages for feisty - some work with ubuntu...

Forgive me for asking but what does this mean?

---

### Post by nowshining on 2007-08-29
oh a m miss edit i meant works for feisty 7.04....

[http://ubuntuforums.org/showthread.php?t=511974&highlight=xserver-xgl](http://ubuntuforums.org/showthread.php?t=511974&highlight=xserver-xgl)

for the Gutsy Devlopment kernel for Feisty but do not update any update as it MAY break your system and after you do the reboot at the end... you will have to when asked to do a partial update - click close - right click on an update and select uncheck all now you have to be VERY careful when updating stuff so be prepared for a re-install if it finally comes down to that, but some things shouldn't be checkmarkeable..but again I updated to a bunch of libs, iptables to the gutsy version..and when you do the update to see the updates files open up update manager.. ;)


in other words you GOTTA be VERY SELECTIVE on that stuff as the intel drivers for my video card made games go slow - a few supertuxkart comes to mind and somewhat messed the screen up.. and you'll need to reboot even if not asked to to make some stuff work..

---

### Post by southernman on 2007-08-29
*Back on topic*

I've started looking into apparmor myself and started by using this guide. Hope it will benefit you as well PmDematagoda.

[https://help.ubuntu.com/community/AppArmor]("https://help.ubuntu.com/community/AppArmor")

SuSe has a nice howto written up here... [http://en.opensuse.org/AppArmor_Geeks]("http://en.opensuse.org/AppArmor_Geeks")

As for a gui to use apparmor, I don't think it has a gui. As I've read through so far, it seems to be a command line application.

---

### Post by WinterWeaver on 2007-08-29
Soo, lol... excuse me for asking... this is the first I head of AppArmor. I read a bit about what it does. Doesn't the IPTables/Firestarter take care of these things?

sorry if it's a noobish question, I'm not too familliar with security on linux etc. and I thought that I only need firestarter to take care of the majority security issues?

Also... what exactly are these privacy issues with skype? I use it everyday O.o ... does anyone have a linky ??

ta,

WW

---

### Post by southernman on 2007-08-29
Don't know if you don't ask... or research... right? ;)

Basically, AppArmor is an added layer of security similar to the way Bastile, SELinux, and GRSecurity are - just addtional layers of security to harden your system.

Yes, a good set of IPTable rules, either hand written or setup by a gui frontend such as firestarter or numerous other frontends, can pretty well lock down your box (in fact, can stop your box dead in it's tracks with bad rules). These other methods just add to that

---

### Post by WinterWeaver on 2007-08-29
thanks for the info... yeah... I was too lazy to do proper in depth research... I just quickly googled, and read the first 2 pages that came up... which didn't really say much :P

Cool... So I don't reeaaally need the extra layer?

---

### Post by southernman on 2007-08-29
I certainly didn't mean to imply you being lazy WinterWeaver. Research is also asking questions... right? 

Whether you *need* an extra layer is something each individual has to decide for themselves. It is my opinion that all aforementioned layers are (or have been in the past) considered more directed at the server markets. Though that may be a bit of a misunderstanding on my part since I don't think these things would be offered to the *johndoe desktop user* if the developers didn't see a need.

---

### Post by WinterWeaver on 2007-08-29
lol... I guess your right... personally... I dont think I can be bothered trying to install setting up more security lol...

---

### Post by PmDematagoda on 2007-08-30
Thanks for everyone's help including southernman, managed to install apparmor and works great!:)

---

