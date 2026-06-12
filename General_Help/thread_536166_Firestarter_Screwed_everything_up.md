---
title: "Firestarter Screwed everything up"
date: 2007-08-27
forum: General Help
---

### Post by towersoft on 2007-08-27
Hi,
     I am hoping that someone out there can help me. I stupidly installed Firestarter and I have had nothing but problems since. I really don't want firestarter installed anymore as all it seems to do is cause problems. The major problem is that when I remove it with sudo apt-get remove firestarter it appears to be leaving the IP table rules in place so I am then no longer able to connect to the internet so I have to re-install it and then stop the firewall to be able to browse. I have been looking for ways to edit the IPtables but its a bit beyond me yet. Firestarter must have created the rules but where has it put them????. I would hope that it also backed up the origonals but where are they? Any help most appreciated as I am stuck messing around with this stupid program :mad:

---

### Post by towersoft on 2007-08-27
Well as I have not yet had an answer my hand was forced and I have removed the iptables executable. Dont know what this will do to my system but it has started up ok.. if anyone can help that would be great. If not I will just carry on regardless untill I change computers soon. :lolflag:

---

### Post by david_2001 on 2007-08-27
> Firestarter must have created the rules but where has it put them????. 
Never had any problems with firestarter myself.  Anyway, execute
```
sudo updatedb
```
Wait for it to finish then
```
locate firestarter
```
This should give you a list that will probably include the following:
> /etc/rc4.d/S20firestarter
/etc/rc3.d/S20firestarter
/etc/init.d/firestarter
/etc/rc2.d/S20firestarter
/etc/rc1.d/K20firestarter
/etc/rc6.d/K20firestarter
/etc/rc0.d/K20firestarter
/etc/rc5.d/S20firestarter
These are the symlinks/files that you need to delete (followed by a reboot).  If they're not there then you just need to reboot.

---

