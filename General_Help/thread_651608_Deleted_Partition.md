---
title: "Deleted Partition"
date: 2007-12-27
forum: General Help
---

### Post by Pingpong27 on 2007-12-27
okay so i was trying to remove ubuntu from my computer because everytime i tried to start it it would just show a blank screen and not load. so i decided to delete the partition it was on and reinstall it. the problem i have now is that when i try to start my computer all i get is the grub loader saying error 22. i can not get past this page is there anyway to fix this. i tried to do the system recovery for vista but i do not have the disc and i need to access vista to do a system recovery. im stuck, someone please help.

---

### Post by gilf on 2007-12-27
> Super Grub Disk can also write other bootloader codes to MBR for you, from the operating system of your choice. For example, you can even restore the Windows bootloader code to MBR if you want to uninstall your Gnu/Linux operating system. Super Grub Disk can easily perform quite a large range of other very useful functions that make troubleshooting and diagnosis of bootloader problems a lot faster and easier. For example, SGD has the ability to scan a computer for various files involved in the booting process. This scanning can save the user a lot of time and tedious repetition.

Read the docs at the link below and you can also download from links there.


[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)



Basically you need to restore something called an IPL (initial program loader) at the beginning of your disk in the MBR or Master Boot Record. Several different kinds of programs can do this.

You can also use Ranish Partition Manager if you are sticking with Windows. However it is fairly easy to mess up a disk if you play with anything else (like changing partition sizes) with this program. You only want to select the "standard program loader", save the MBR and get out. Don't try anything fancy.  

My favorite choice: you can also try reinstalling Ubuntu. You can then multiboot again into Vista.. 

ps. I'd be willing to bet that your Ubuntu CD was flawed.

Try downloading and burning another copy -- burn at no more than 8X speed.

If you need help finding out how to get Ubuntu working well, I bet several thousand people could help you here. Some are quite tenacious.

---

### Post by dcstar on 2007-12-27
> **Pingpong27 said:**
> okay so i was trying to remove ubuntu from my computer because everytime i tried to start it it would just show a blank screen and not load. so i decided to delete the partition it was on and reinstall it. the problem i have now is that when i try to start my computer all i get is the grub loader saying error 22. i can not get past this page is there anyway to fix this. i tried to do the system recovery for vista but i do not have the disc and i need to access vista to do a system recovery. im stuck, someone please help.

Boot off the CD and install Ubuntu again, then boot Windows after the install completes and restore the MBR.

---

### Post by gilf on 2007-12-27
Also, one likely cause of the blank screen on startup was that the splash screen was in a resolution  that wasn't supported by your monitor.

That can be fixed if you still want to try Ubuntu.

---

### Post by Pingpong27 on 2007-12-28
i got ubuntu to work like 2 or 3 times and from what i saw i really liked it. only things that i didnt like was that my bluetooth mouse didnt work with the bluetooth software on ubuntu. but thanks for the suggestions, i will try again.

---

