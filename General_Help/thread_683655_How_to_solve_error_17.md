---
title: "How to solve error 17"
date: 2008-01-31
forum: General Help
---

### Post by ttmw on 2008-01-31
ok, ive just taken linux off mylaptop by deleting the partition through ubuntu live cd, then i rebooted and put my windows disk in again it went through the whole system restore thing and told me it was all completed and to reboot. I rebooted and i keep getting...

 'grub loading please wait... error 17'

and then it does nothing. How do i get rid of grub completely or what do i need to do to get windows back? Thanks in advance.

---

### Post by Darkhack on 2008-01-31
Boot with your Windows Disk and use the [Recovery Console]("http://support.microsoft.com/kb/307654/") command "fixmbr".

---

### Post by ttmw on 2008-01-31
ok now ive got onto the command promt it just shuts down the computer after about 10 seconds, any ideas why this is?

---

### Post by slayer04 on 2008-01-31
I don't know why it shuts down on you cause it shouldn't but heres some information

when you installed grub it over write your windows boot  record and thats why he told you to use fixmbr which means fix master boot record maybe to help the proccess assign the fixmbr to the hard drive windows is on so try 

fixmbr \Device\(your Hard Drive) 

ex. fixmbr \Device\HardDisk0

this will only work if you boot from your windows disk and use the recovery console because windows gets the new MBR off of the disk

---

### Post by redenex on 2008-01-31
Here is another discussions had on Grub Error 17, and there are some solutions in there as well.

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

