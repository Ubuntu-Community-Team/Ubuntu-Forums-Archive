---
title: "Help! Grub causing boot problems"
date: 2006-12-05
forum: General Help
---

### Post by jetsetlemming on 2006-12-05
A while ago I installed ubuntu to dual boot with windows, figuring that it could be something to fall back on in case windows screwed up. I tried to use it a few times, but could never get far, and couldn't manage to get it online (my ISP requires a login through it's software, which is windows only).
Last week I got a new video card, an ati Radeon, and this pretty much killed linux. It couldn't boot at all, besides to a format that resembled DOS. 
Since I'm running a bit low on HD space on my main windows partition (<9 GB left), I decided to uninstall ubuntu. However, since I couldn't access ubuntu at all, I ended up opening up Partition Magic, setting it to format and erase the linux and swapfile partitions, and resize the windows partition to the entire  harddrive again. 
It rebooted the computer, started the process, got rid of the two linux partitions, and failed when trying to resize the windows partition, and rebooted the computer again. This time, when it got to Grub, it got an error, and froze. I panicked, broke out my windows recovery disc, and tried to fix it. I'm not sure how, but somehow between the windows recovery disc, the BIOS menu, creating a new NTSC partition over where the linux one was, and a constant stream of requests to God for help, I managed to log into windows. I have no idea how I got here. 
Basically, I need to get rid of Grub, so the computer just boots to windows by default. According to my friend who also uses ubuntu (happily, he's a bit more savvy than I), Grub is on a seperate partition that it boots from. Partition magic, however, does not display this partition. How can I get rid of Grub, and cease my booting troubles? :( Here's an image of the current layout of my harddrive, according to Partition Magic:
[IMG]http://xa7.xanga.com/26ba85e60053093510383/b65221463.jpg[/IMG]
I have no idea what the "extended" is, or why when the windows recovery disc made the new partition it left that 7.8 MB empty and unassigned.

---

### Post by bulldog on 2006-12-05
To remove GRUB,just use a windows install disk.
Boot from it and let it run till you get three options.
Install,Repair and exit.
One of them is repair a windows installation.
Choose this one and you get to a console window,which is called recovery console.
You have to provide your administrator password,if there's any,and login to the existing windows.

Now type fixmbr,you get a warning but ignore this,and apply.
Now exit the windows cd and boot from hard disk.
It should run right into windows again.

---

### Post by IMELucky on 2006-12-05
Ok, this shouldn't be to hard to do.

I don't know much about partition magic, so if it interferes with this you might have to remove it.

1) Start by disabiling any security programs that protect the Master Boot Record of your hard drive (Windows Security Center, Antivirus Software, etc)

2) Open up the command prompt

and try...

3) fdisk /mbr

This should make Windows rewrite the MBR and you should be able to boot the computer normally

---

### Post by jetsetlemming on 2006-12-05
> **bulldog said:**
> To remove GRUB,just use a windows install disk.
Boot from it and let it run till you get three options.
Install,Repair and exit.
One of them is repair a windows installation.
Choose this one and you get to a console window,which is called recovery console.
You have to provide your administrator password,if there's any,and login to the existing windows.

Now type fixmbr,you get a warning but ignore this,and apply.
Now exit the windows cd and boot from hard disk.
It should run right into windows again.
Thank you, man! That fixed my problem completely. >_> Windows rewrote the master boot record, restarted, and now it's going fine. I don't think I'm gonna mess around with linux OS's for a while...

---

### Post by IMELucky on 2006-12-05
Well, I'm sorry you didn't have good luck with Linux. I'm glad this fixed your problem, but I hope that you give Linux a try again further down the road. I had a lot of trouble with Linux when I first began using it, but after giving things some time, I never use Windows anymore.

Good Luck

---

