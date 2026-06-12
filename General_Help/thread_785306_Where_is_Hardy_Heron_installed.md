---
title: "Where is Hardy Heron installed?"
date: 2008-05-07
forum: General Help
---

### Post by Jonka on 2008-05-07
Hi,

I am about to take you up on your advice not to be afraid to ask questions.
With the release of the beta Hardy Heron and its ease of installation I was at last tempted to try a different OS. I even amazed myself at successfully burning an ISO file, another first for me.The install went well, a problem with screen definition size was overcome thanks to this forum.
Reviews of Hardy heron state that it is installed on C: drive. I have searched all through this drive to try and find it, so my simple question is where on C: drive is the file and what is it called?

My thanks for any assistance   ---   Jonka

---

### Post by glennric on 2008-05-07
Did you use WUBI?  If you did a normal install there is no C:.  Linux doesn't use the windows C: drive naming scheme.

---

### Post by Joeb454 on 2008-05-07
Also if you just booted from the CD and chose "Start or Install Ubuntu" it will be running from the CD (no installation at all) :)

---

### Post by eriqjaffe on 2008-05-07
> **glennric said:**
> Did you use WUBI?  If you did a normal install there is no C:.  Linux doesn't use the windows C: drive naming scheme.If you **did** use WUBI, it should be in c:\ubuntu

---

### Post by bodhi.zazen on 2008-05-07
Normally you repartition your hard drive to make space for Ubuntu. In windows terminology this amounts to e:

Linux partitioning uses alternate terminology :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

wubi is an alternate method of installing Ubuntu into a file on your C drive without repartitioning or installing grub.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Jonka on 2008-05-10
Thank you to all those who replied to my question but unfortunately it did not answer the question. This is the Absolute Beginners Forum is it not?
I have done a search on all my drives, C:,E:,F:,and H: the latter being an external USB drive that is used only for backups. I searched using the words, wubi, ubuntu and hardy heron in separate searches, all with no result.
The following convinced me to give it a try


[COLOR="Red"]Try out and remove Ubuntu like a Windows program
No hard drives to re-organise, no dual-boot setup—just pop an Ubuntu desktop CD in while Windows is running, and you'll get an option to install Ubuntu—inside Windows. Basically, a program called Wubi creates a **single file tucked away in Windows** and packs a virtual Ubuntu installation inside it. When Windows boots up next time, you'll get an option to boot that pretend Ubuntu installation, and you're off to see how Ubuntu would run on your system. Sick of experimenting and want to try the next step? Uninstall Wubi the same way you'd uninstall any other program.[/COLOR]

Any other advice as to where to find the file would be appreciated

Regards   ---   Jonka

---

### Post by Joeb454 on 2008-05-10
Ok so I assume that means you installed it via Wubi (the menu that allows you to install Ubuntu **from** Windows).

If so I think it should be in C:\Ubuntu

---

### Post by bodhi.zazen on 2008-05-10
According to the wubi FAQ :

> Ubuntu is installed within a file in the Windows file system (c:\ubuntu\disks\root.disk), this file is seen by Linux as a real hard disk.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

