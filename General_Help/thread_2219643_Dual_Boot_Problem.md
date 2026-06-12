---
title: "Dual Boot Problem"
date: 2014-04-24
forum: General Help
---

### Post by lonewolf262 on 2014-04-24
Hello, 

I'm new to Ubuntu (just installed it) and after watching a few guides and reading up a bit on the process I tried my hand at installing Ubuntu through Windows 7 dual boot. It worked and now Ubuntu is working, but when I start up my computer it doesn't let me choose to start up in Wondows 7 or Ubuntu. It just automatically starts in Ubuntu. 

I partitioned my harddrive and went through the usb installation. I can still access my Windows desktop files and everything is still there, but I would like to be able to access my Windows side. 

Is there any way I can fix this?

---

### Post by oldfred on 2014-04-24
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
    

 Boot-Repair for 14.04 trusty not yet released
 ----------- WORKAROUND 0 sandyd  compiled it
 [https://launchpad.net/~sandyd/+archive/boot-repair](https://launchpad.net/~sandyd/+archive/boot-repair)
 ----------- WORKAROUND 1
+ You can download the DEBs packages here: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)
+ First install the 'glade2script' DEB, then 'boot-sav', then 'boot-repair'.
+ 
+ ----------- WORKAROUND 2
+ Use Boot-Repair-Disk [https://sourceforge.net/p/boot-repair-cd/home](https://sourceforge.net/p/boot-repair-cd/home)
+ ----------- WORKAROUND 3
[https://bugs.launchpad.net/boot-repair/+bug/1307218](https://bugs.launchpad.net/boot-repair/+bug/1307218)
Workaround. Change ppa from trusty to saucy.
[http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335](http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335)
gksudo gedit /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages)'
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages)'

---

### Post by martin92 on 2014-04-25
Hello!
 I have similar problem: I have dual boot Windows 7 and Ubuntu 14.04 LTS and when I start my computer it loads grub2 and by default runs Ubuntu. The problem is that I want to run Windows by default. I've tried fixing the problem with Boot-Repair, but it doesn't worked. So could someone please give me an advice what to do?

My BootInfo summary is here: [http://paste.ubuntu.com/7328071/](http://paste.ubuntu.com/7328071/)

---

### Post by dragonfly41 on 2014-04-25
I would use grub-customizer to change your grub menu order

[https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

---

### Post by martin92 on 2014-04-25
[**[COLOR=#000000]dragonfly41[/COLOR]**]("http://ubuntuforums.org/member.php?u=1261878") Thank you very much! :D I used the grub-customizer and solved the problem!

---

