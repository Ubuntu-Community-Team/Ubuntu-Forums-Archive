---
title: "Problem with grub, after resizing linux and swap partition"
date: 2006-09-08
forum: General Help
---

### Post by muffinhead on 2006-09-08
Hi all, I started having a problem with grub, after I resized my Linux,   and swap partition with partition magic in windows XP  

  My Problem is, I was extending or making my Linux, and swap partition bigger with partition magic, near the end after my pc rebooted and was resizing and moving the partitions, I got an error at the end saying something couldn't be done because it was in use, and it said, "Press any key to reboot".  

  Ok, so I rebooted and am presented with an error during boot, saying, "error 17, cannot load OS, or grub boot loader.  At least I was able to boot back into windows XP, buy popping in my restore DVD, and fixing the master boot record with, "fdisk /mbr" , but now that has left my linux partition unbootable, and unusable until I can somehow figure out how to reinstall grub, without sacraficing my data on my Linux Partition.

 Can someone tell me how I can reinstall the Grub boot loader, without reinstalling Ubuntu Linux, and Losing all my data? 

I spent hours upon hours downloading libraries, such as gtk, libsdl, libpng, and a bunch of other things on my 56k dial-up, So I could compile ZSNES under Linux, and use other emulators as well on Linux. I also have downloaded other linux freeware, and Automatix, which all take forever to download and update.

 I don't have a floppy disk drive in my computer, or even a bootable floppy drive, Is there any other way I can reinstall grub, possibly by making a bootable cd with grub bootloader, or the grub installer on it? At least my DVD-RW drive is bootable in the bios, so if I can make a bootable cd with grub on it, that would hopefully solve my problem.  

Thank You if anyone can help .:) 

Btw, I'm using Ubuntu 6.06 (Dapper Drake)  specs are:   

2.66 ghz celeron D 330,   

1024 megabytes of ram,   

plenty of hard disk space,  

Nvidia Geforce FX 5500 OC, 

Sound Blaster Live 24-bit.

---

### Post by link141 on 2006-09-08
I have the same error (I posted a thread), except grub is still on the drive, and windows is gone.  I do not know how to fix this error either, and would be grateful if anyone would come forth to help.  Thanks :)!

---

### Post by muffinhead on 2006-09-08
Hopefully someone can help, as this is a very important problem that I need to solve, so I don't lose all my data on my linux partition.

I can't compile the grub source from the official grub website, and fix it that way, since I can't boot into linux atm.

Is there a command on the live/install cd of dapper drake, that allows grub to be reinstalled to the master boot record?

---

### Post by muffinhead on 2006-09-09
Can someone please help me, I've been up all night trying to fix this problem, so I can boot back into ubuntu Linux.

I have tried creating a grub boot cd-rom, but all is it gives me when booting the grub boot cd, is a command-line, that I have no Idea how to use, or what to do in order to boot Ubuntu.

Is there a simpler way to fix this, or any way at all, I'd really hate to lose all my data, downloads, and libraries, i spent hours upon hours downloading on my 56k dial-up.

I'd really appreciate it if someone can help me solve my problem, as soon as they can, because there's important docs, programs, on my linux partition.

Thank you if anyone can help;)

---

### Post by Irony on 2006-09-09
Using the Hoary CD I do;

Boot from the install ubuntu CD and at the prompt typed;
[PHP]boot: rescue[/PHP]
Go to a  mount points, hda5 would be;
[PHP]dev/disc/disc0/part5[/PHP]
At the sh-3.00# prompt type;
[PHP]grub-install /dev/hda[/PHP]
After being returned to the prompt, do;
[PHP]#umount /dev/hda5
#reboot[/PHP]
Or Ctrl-Alt-Delete will also probably reboot. At this point, how you open the CD drive depends on the machine. Usually if you hit the open button on the drive as the system has just begun to boot (when you see the BIOS name, CPU, and RAM), it will open. If you can't seem to get it open naturally, enter the BIOS setup and change the boot sequence to bypass the CD, boot normally, login, and eject the CD. Try not to use the pin or hard-reset.

I expect from the Dapper Live CD you would click the install button but skip the installing but at the install grub point install it. Or you might just install grub via synaptic.

---

### Post by muffinhead on 2006-09-09
If my Ubuntu installation is on my Secondary hdd drive, which is my D:\ Drive in windows XP, what would I type, using the commands given by irony? 

[SIZE=3][COLOR=Black]I don't think, "[/COLOR][/SIZE][COLOR=#000000][SIZE=3][COLOR=Black]dev[/COLOR][/SIZE][SIZE=3][COLOR=Black]/[/COLOR][/SIZE][SIZE=3][COLOR=Black]disc[/COLOR][/SIZE][SIZE=3][COLOR=Black]/[/COLOR][/SIZE][SIZE=3][COLOR=Black]disc0[/COLOR][/SIZE][SIZE=3][COLOR=Black]/[/COLOR][/SIZE][COLOR=#0000bb][SIZE=3][COLOR=Black]part5" , is going to work if Ubuntu is on my second hard drive.

would it be something like, "/dev/disk/disk2/part5, if Ubuntu is installed on my second hdd D:\ Drive in windows XP?

Please let me know, Thank You:)
[/COLOR][/SIZE][/COLOR][/COLOR]

---

### Post by muffinhead on 2006-09-09
Nevermind, I didn't realize till today, that I trashed my ext2 filesystem as well, in the process of resizing my partition.

I'll have to do a full reinstall ,what a bummer:(

I found that out when I tried to reinstall grub, and mount my Ubuntu Partition, it returned an error saying the partition had errors on it, and it wasn't a valid ext2 filesystem, and it couldn't be mounted.

Oh well I guess. It would help tremendously if the Libraries I needed installed, could be installed using the ubuntu cd-rom, rather than spending hours upon hours downloading them.


Thank to those that replied, I appreciate your help;)

---

### Post by nickpaton on 2006-09-09
It may be too late, but have a look at post #5 from

[http://www.ubuntuforums.org/showthread.php?t=252186]("http://www.ubuntuforums.org/showthread.php?t=252186")

Details (thanks to Drakkor):

> Boot to the live Ubuntu CD
Open terminal type sudo grub
At grub>.prompt enter these commands
find /boot/grub/stage1
This will return a location like (hd0,1)
still in terminal type
root (hd?,?) use the values from the find command
Next enter the command to install grub to the mbr
setup (hd0)
Enter quit
reboot to the hard drive


---

### Post by muffinhead on 2006-09-09
Yeah, it's too late now. I deleted my Linux partition, and am starting fresh.

I found out, that I ended up trashing not only grub, but my ext2 partition as well when resizing my Ubuntu Linux and swap partition. So it was pretty much a lost cause.

Are there any packages or libraries on the Ubuntu Live/install cd-rom, that can be installed? This would at least help me to avoid Spending hours downloading stuff again, and shorten up the time somewhat, if some of the packages can be installed via the ubuntu cd in synaptic, but I have no clue how to do this. Maybe someone can let me know:) Thank You.

---

