---
title: "Backing up installed Ubuntu on Live USB to another USB"
date: 2017-03-21
forum: General Help
---

### Post by Lanane on 2017-03-21
I have a Live USB Install of Ubuntu. I installed it on to a jump drive so I could take it wherever I go. I want to backup,, and be able to regularly backup this drive as I need to. When new files are added, extremely important bookmarks, the list goes on ... I didn''t like any of the programs I tried so I spent time on google learning DD .. 

Ultimately I would like a simple .iso image of what is own my USB (Sort of like my own linux distro) so I can share copies with friends etc - there are things i am installing etc i would like them to have copies to. Right now there are 6-7 people who want a copy of my Ubuntu as installed. 

--------------------------------------------------------------------------------------------------

I tried two commands, 


Command 1) USED WAS dd if=/dev/sdb of=/dev/sdc bs=64K conv=noerror,sync

B - is for the 32 gig USB .. C is for the new 16 Gig Thumb Driver
...........................................................................................................................
From what I read this would take the backup of my 32 Gig USB drive (B) and place it on the 16 GB USB Drive (C) I put in.  

The 16 GB USB did not run out of space however I got a grub error when I tried to boot from it. 



Also tried as follows  :  

Backing up to Image

dd if=/dev/sdb conv=sync,noerror bs=64K | gzip -c  > /home/lanane/Desktop/backup-image.img.gz

B : Is he active drive for the 32 Gig USB stik with the OS on it. 

The file on my desktop ended up being over 20 Gigs when I woke up (I waited by the comp for 3 hours before crashing) and I had an error saying I was out of space on my drive. 

Right now, on my 32 gig drive, 5 Gigs have been used for the Ubuntu version I have with all settings etc I want stored. 


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

---

### Post by Lanane on 2017-03-21
I am trying again, here are the exact commands - Freshly formatted 16 GB USB stick - The 32 GB USB is active Ubuntu running, I am typing this off of in face

lanane@lanane:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sdb      8:16   1  29.2G  0 disk 
&#9500;&#9472;sdb2   8:18   1     1K  0 part 
&#9500;&#9472;sdb5   8:21   1   3.5G  0 part [SWAP]
&#9492;&#9472;sdb1   8:17   1  25.7G  0 part /
sr0     11:0    1  1024M  0 rom  
sdc      8:32   1  14.6G  0 disk 
&#9492;&#9472;sdc1   8:33   1  14.6G  0 part 
sda      8:0    0 698.7G  0 disk 
&#9500;&#9472;sda4   8:4    0 145.1G  0 part 
&#9500;&#9472;sda2   8:2    0   100M  0 part 
&#9500;&#9472;sda5   8:5    0   817M  0 part 
&#9500;&#9472;sda3   8:3    0    16M  0 part 
&#9500;&#9472;sda1   8:1    0   450M  0 part 
&#9492;&#9472;sda6   8:6    0   200G  0 part 
lanane@lanane:~$ dd if=/dev/sdb of=/dev/sdc bs=64K conv=noerror,sync
dd: failed to open '/dev/sdb': Permission denied
lanane@lanane:~$ sudo dd if=/dev/sdb of=/dev/sdc bs=64K conv=noerror,sync
[sudo] password for lanane:

---

### Post by oldfred on 2017-03-21
The dd command is also known as Data Destroyer, so be careful.

You may  need to read more on dd as it is only for same size to same size drive copying. I also copies all blank space so is one of the slowest ways to copy data.

I just prefer a new clean install & copy my data which usually is not in /home but in /mnt/data even on flash drives. You also can then copy /home. Only if you manually changed hardware configuration settings, might you need to copy some or all of /etc.

 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)
"I have become dd, the destroyer of data." Unix Proverb 
[https://en.wikipedia.org/wiki/Dd_%28Unix%29](https://en.wikipedia.org/wiki/Dd_%28Unix%29)

---

### Post by Lanane on 2017-03-21
Well here' my issue : And ULTIMATE Goal ..

I want to take whatever is on my USB stick - Right now a 32 Gig USB stick with Ubuntu and some special programs installed on it .. 

I want to be able to burn it to an .ISO image, so friends can simply use something like Pen Drive, drop the ISO, and end up with an exact copy of the Ubuntu I am running. I want them to be able to do this from Windows - and not have to install Ubuntu themselves. 

As time changes and I add things I also want them to be able to take my newly created .iso file and reburn it from Windows. Instead of them taking every command I run and having to do it themselves. This way they constantly have an updated and current version of Ubuntu EXACTLY as I am running it. I'm aware they will lose any saved data, which is a non issue. Simply them having an exact copy of the version I am running, easily installable from Windows. Obviously they will install to their own USB stick. From their own computer, after downloading the .iso image I create that's an exact copy of my Ubuntu.

I tried a couple Ubuntu programs, and had no luck with those. From windows you cant use programs like Magic ISO as Windows programs don't recognize the file system and immediately want me to format the USB drive with the files I want to create an .iso image from

Thanks for any help

---

### Post by yancek on 2017-03-21
I'm not really sure I understand what you are trying to do but, if you have an actual install of Ubuntu (which version?) on your flash drive, you should be able to download and run either systemback or pinguybuilder to your Ubuntu and run it following the instructions on their respective sites.  This will create an iso file which you can then copy to a USB or burn to a DVD.  If I remember correctly, pinguy will include the ubiquity installer but systemback does not you so you would need to install ubiquity before running systemback if that is your choice.  Not sure if you've tried either but it might be worth checking out.  The file sizefor the created iso has a 4GB limit so if your install is much more than 10GB, it probably won't work.

---

### Post by Lanane on 2017-03-22
Thanks, one of those programs might work. I installed the ubiquity prerequisites. There were two. 

I will try Pinguybuilder & Systemback from their websites, they aren't in the software repo "as is" with Ubuntu. So I'll follow on site directions, add repos or however it has me do it. Hopefully one of these work. 

As for what I'm trying to do. It's pretty basic :

I want to share my EXACT copy of Ubuntu with others. Exactly as configured. As an .iso installable file. Once I update it I will be releasing a new .iso to be burnt again, which will have the new EXACT version of Ubuntu I am running with the changes I have made.

Let's say you have 100 games installed on your Ubuntu system, and you wanted to give that exact copy to friends - that's what I want to be doing. 

Let's say I add 20 more games, totaling 120 - once those are added I want a new release with a new .iso file - they can simply "ReBurn to the same USB Drive" 

I want this release an initial install for users setup as an .iso file for users to install using ... Say Pen Drive Linux. Or most likely YUMI. As I change my copy I am running I want to re-copy it and re-release it for users to re-burn.

My Ubuntu will never be more then ... say ... 10 Gigs I'm imagining not more than 8 ... I don't know how the compression rates work on .iso but I'm assuming 70% at least ? Right now I am looking and it is 

/dev/sdb1       26396940 5257972  19775000  22% /           -   I.E. 5 Gigs or so .. 

I don't ever expect it to get larger then 7.5 - I'm assuming the .iso should compress not explode it, like it did the first time I tried. 

Hopefully those programs you gave me, one will work. It's late but I'll be trying tomorrow. 

Thanks !!

---

### Post by Bucky Ball on 2017-03-22
Clear about what you want to do. Unclear about the install you have on USB. You said you have a 'live' install. That is the Ubuntu installer running a live session, not Ubuntu installed to a USB stick. Anything you install to that will be lost on reboot.

So please confirm: You have installed Ubuntu to a USB stick (you would generally need two USBs for this; one with the installer and one blank one to install Ubuntu to) or you have created a USB installer on a USB stick and you are currently running 'Try Ubuntu'? If you reboot your machine, do the changes you made to the USB install stay there, or is it back to 'vanilla'?

---

### Post by yancek on 2017-03-22
You do need to clarify whether you have an actual install or are using a Live Ubuntu.  Either Systemback or PinGuyBuilder will create an iso file which is what you will want to use.  You should then be able to use software such as 'rufus' or 'unetbootin' and point to this iso to put it on a flash drive which should be bootable and can be used to install.  Or you could simply copy the iso to a flash drive and let your friends use it an copy the iso to their windows machine and use 'rufus' or 'unetbootin' or similar software to create a bootable flash drive.  Or they could burn it to a DVD.

I tested this on a few systems and below are the installed sizes with the iso sizes.  I'm not sure why there are differences in the ratios as I expect they all use the same software, probably genisoimage.  If you do have an actual installed Ubuntu and it is less than 8GB, it shouldn't be a problem.

        Lubuntu installed size: 5.3GB, Created iso:  1.1GB
        Mint 17 installed size: 4.8GB, Created iso:  1.8GB
        Ubuntu installed size:  9.6GB, Created iso:  3.5GB

---

### Post by kyknos12 on 2017-03-22
read my post 6 video tutorial [https://ubuntuforums.org/showthread.php?t=2353736](https://ubuntuforums.org/showthread.php?t=2353736)
few words about this, essentially you need to do squashfs system, the squashfs tools It is a powerful tool any backup linux system if you know you work to something that is not mentioned in any of the known forums, replace the old filesystem.squashfs from official same iso ubuntu version from new filesystem.squashfs after that the tool genisoimage make out new iso image, burn image to dvd/usb thats all, As for the limitation 4GB the genisoimage give the option genisoimage -allow-limited-size

---

### Post by Lanane on 2017-03-23
Systemback seems to be working as far as backing up everything. Just having some issues I'll figure out I'm sure ... 

Main ones being 

1) The created files .iso and .live are only read on and off in Windows for some reason. Sometimes Pen Drive picks them up, sometimes magic iso, I'm going to continue to try to copy the backups different ways until I get one that works every time, 

2) Oddly even on a 16 Gig thumb drive it is saying 4 or so Gigs used and under 2 available. Pry, again, something with the backup procedure .. 

Thanks for the help guys. Got the basics, now it's just making it flawless at this point.

---

### Post by yancek on 2017-03-23
> The created files .iso and .live are only read on and off in Windows for  some reason. Sometimes Pen Drive picks them up, sometimes magic iso

The created iso file is read-only by design and mounting/accessing it in windows or Linux will not allow you to write to it.  I'm not sure why you would want to?  Modifying the created iso would require you to copy it to another directory/folder and use the squashfs tools mentioned above which is a much more complicated process. 

You should be able to use burning software to burn the created iso file as an image to a DVD or use pendrivelinux, rufus or similar software to put it on a flash drive and be bootable.

---

