---
title: "New to Ubuntu and it will not Boot just restart in endless loop."
date: 2018-04-03
forum: General Help
---

### Post by commandersnuggle on 2018-04-03
Hi everyone thank you for looking at my question. 

So I have a Thinkpad E480 and it is duel drives and I dedicated one drive for Windows and the other for Ubuntu. I set up the Ubuntu drive first then the windows and everything worked fine for about three days. Ubuntu would not start and just restart my computer and would do this loop for every till I forced it to turn off. I reinstalled Ubuntu a bunch of times on the the drive and it still give me that same problem and I even tried other Linux distros to see if that would fixed my problem it did not. I used the Boot-Repair and it did not work but it gave me a link that I could share and get others to help me. I am still super new to Linux and I really want to switch over to Ubuntu permanently but if i cannot get it to work I might have to stick to Windows. Thank you for all your help.  

[http://paste.ubuntu.com/p/8tKH2SyFm9/](http://paste.ubuntu.com/p/8tKH2SyFm9/)[COLOR=#000000] [/COLOR]

---

### Post by oldfred on 2018-04-03
You show UEFI secure boot on? Have you tried turning it off in UEFI?
It also looks like you have Windows fast start up on. Grub only boots working Windows or Windows that is not hibernated nor needs chkdsk. Then you have to directly boot Windows and turn it off again.

Windows on updates (which may be in background) may turn fast start up on. Some also posted it may turn UEFI Secure Boot on also. 

Try directly booting Windows from UEFI and try with UEFI Secure Boot off.

If you do not have time to press any keys, then UEFI fast Boot (different than Windows fast start) may be on. It assumes no changes to configuration, either hardware or operating system and immediately starts booting without rechecking system. But that can be so quick that you do not have time to press any key.
You may have to then drain all power and do a "cold" boot not warm reboot. If laptop, you may have to remove battery and hold power switch for 10 sec or so.
On my desktop I had total lockup and that did not, I tried removing coin battery on motherboard, and jumpering reset pins on motherboard and still did not work. But disconnecting default boot drive did work.

---

