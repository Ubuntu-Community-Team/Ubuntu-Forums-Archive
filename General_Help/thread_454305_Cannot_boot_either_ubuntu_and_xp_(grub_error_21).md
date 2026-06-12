---
title: "Cannot boot either ubuntu and xp (grub error 21)"
date: 2007-05-25
forum: General Help
---

### Post by rudlavibizon on 2007-05-25
Please help, i have a lot of work over weekend and cannot boot to my OS's. 
I installed ubuntu feisty today and cannot boot from grub.
When I choose from grub menu Ubuntu or Xp I get an error 21 selected disk does not exist.

I have four hdd's (3 sata and 1 IDE). Previous installations (kubuntu and ubuntu studio) worked fine. 

I tried messing with grub to try to fix this and it seems grub does not see 2 of my drives (the ones with Ubuntu and winXP). Here's how I figured that out:

When I type geometry (hd_ and press tab i get these possibilities:
"hd0 and hd1"
When I do a cat /boot/grub/menu.lst I see that Ubuntu root is on (hd3,0) and winXP on (hd2,0). That seemed odd.
Also i have a third entry in menu.lst in between which says "root" and nothing else

I've spent half the day trying to solve this, what do I do now?

---

### Post by FunnyLookinHat on 2007-05-25
A common bug with the installer is that it will incorrectly setup your GRUB to point to wrong hard drives if you have IDE and SATA hard drives on the same system (my desktop had this error).

You will have to try guessing which hard drives are correct by editing your GRUB boot lines when grub loads up...

When you see the GRUB menu, highlight your ubuntu line and hit "E"
Then on the first line (it will probably have an (hd3,1) or something similiar on it, hit E again.
This will let you edit the line.
Change the first number that is next to hd to 0, then hit enter.
Now hit B to try to boot that line.

If that doesn't work, try agian with 1 instead of 0, then 2, then 3...  one of those is bound to work.

Once you find the correct number you should boot into your system and edit the file /boot/grub/menu.lst to reflect the changes you made...
then run the command sudo grub-install

Hope this helps!

---

### Post by confused57 on 2007-05-25
> **rudlavibizon said:**
> Please help, i have a lot of work over weekend and cannot boot to my OS's. 
I installed ubuntu feisty today and cannot boot from grub.
When I choose from grub menu Ubuntu or Xp I get an error 21 selected disk does not exist.

I have four hdd's (3 sata and 1 IDE). Previous installations (kubuntu and ubuntu studio) worked fine. 

I tried messing with grub to try to fix this and it seems grub does not see 2 of my drives (the ones with Ubuntu and winXP). Here's how I figured that out:

When I type geometry (hd_ and press tab i get these possibilities:
"hd0 and hd1"
When I do a cat /boot/grub/menu.lst I see that Ubuntu root is on (hd3,0) and winXP on (hd2,0). That seemed odd.
Also i have a third entry in menu.lst in between which says "root" and nothing else

I've spent half the day trying to solve this, what do I do now?

You could also use the live cd to reinstall your original Ubuntu grub to the mbr of the drive you're booting from:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
I would use the original Ubuntu live cd to reinstall grub.

Hopefully you'll be able to boot your Windows XP and your original Ubuntu.  If you can, you might want to check the output of:
```
gedit /boot/grub/device.map
```
once you determine how your original Ubuntu device.map recognizes the order of your hard drives, you could add an entry to your menu.lst to boot your Feisty, using configfile:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

Check back if you're able to get your Window's XP & original Ubuntu to boot, there's still a little configuring of your Feisty menu.lst that you'll need to do in order to get it to boot, i.e. changing the root designation..

---

### Post by rudlavibizon on 2007-05-25
I tried reinstalling grub via  ubuntu studio rescue mode and it reported an error. Then i got restless and begun to install ubuntu studio (which was my previous install) again. I aborted this when i saw your post and reinstalled plain ubuntu. And now it booted! Weird! Grub menu.lst points now to (hd1,0) ->ubuntu and (hd0,0) -> XP. :confused:

---

