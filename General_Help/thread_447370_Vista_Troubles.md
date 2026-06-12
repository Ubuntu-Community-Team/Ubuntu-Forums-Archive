---
title: "Vista Troubles"
date: 2007-05-17
forum: General Help
---

### Post by PapaSmirf on 2007-05-17
Unfortunately, I installed Ubuntu Feisty Fawn and used its partitioning tool to repartition my drive to share with Vista.  Now I cannot boot Vista.  Can someone help me fix this problem without having to reinstall Vista entirely.

---

### Post by m.musashi on 2007-05-17
The install should have installed something called GRUB. It's a boot loader and would have automatically recognized vista and set up a menu with the options for both Feisty and Vista.

I take it that you did not get a GRUB menu on boot? Can you open a terminal and post the output of
```
sudo fdisk -l
```
The last part of that is a small letter L

Also, open the file /boot/grub/menu.lst and copy and past the contents. You can skip the lines that begin with a # to keep it shorter.

Can you also explain a bit more about what happens when you boot?

---

### Post by pete222 on 2007-05-18
this is what I picked up off the forums;

I have 2 HD one is sata XP and the other ide fiesty- 

I now have a grub menu that displays what I want to boot into- 
I edited this; 


/boot/grub/menu/lst

title Windows XP
root (hd1,0)
makeactive
map (hd0)  (hd1)
map (hd1) (hd0)
chainloader +1

so when I was installing ubuntu I disconnected my XP drive and installed ubuntu and then added this and now I have 2 PC's in 1 with no risk if I screw up windows or ubuntu 

I don't like the idea of a dual boot system on the same drive, and this keeps everything neat and gives me a piece of mind. 

HD's are cheap.

---

### Post by bobplano on 2007-05-18
sorry to hear that happened to you. its been suggested to use vista's partitioning tool to resize the partition. it sounds like you may have deleted something at the end of the drive. you might have to repair the vista install but try other people's suggestions first

---

### Post by PapaSmirf on 2007-05-18
I apologize for not being more detailed.  It was late and I was a little frustrated.  It installed GRUB correctly.  I also editied the menu.list file to make sure it was all correct, it was.  Basically, when I get to grub I can boot into Ubuntu, but when I select Vista it just reboots the entire PC and I end up back at the BIOS screen and then it goes back to GRUB.

This is my menu.list entry for Vista:

title Vista
root (hd0,0)
makeactive
savedefault
chainloader +1

---

