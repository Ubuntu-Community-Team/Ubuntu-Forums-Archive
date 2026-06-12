---
title: "Repartition NTFS and give to Linux"
date: 2007-05-04
forum: General Help
---

### Post by kleam on 2007-05-04
Ok right now this is my setup for harddrives. I understand that It mgiht not have been set up very well.

Harddrive1: 40gb
[INDENT]Drives:
[INDENT]C:\[/INDENT]
Content:
[INDENT]Windows XP OS and system files[/INDENT]
[/INDENT]

Harddrive2:200gb
[INDENT]Drives:
[INDENT]E, F, G, Linux[/INDENT]
Content:
[INDENT]e:\music and videos       Size:50gb  Free space: 10gb[/INDENT]
[INDENT]f:\games and downloads      Size:110gb Free sapce: 20gb[/INDENT]
[INDENT]g:\game ISO files      Size:40 Free sapce: 20gb[/INDENT]
[INDENT]Linux ubuntu Feisty 7.04-desktop-i386      Size:22gb Free sapce: 1.5gb[/INDENT]
[/INDENT]


Ok what I want to do Is take from the g partition, which is NTFS and add it to the Linux partition. I don't understand how I do this.


Also: I think there is a problem with my ubuntu installation.
I don't have much on the linux partition (ubuntu, wine, ati graphics drivers, and WOW) and before I even finished installing WOW It said that my partition was full.

This is what I think happend: I first installed Ubuntu-7.0.4-Desktop-AMD64 on this partition. I had problems understanding how to work whine under the 64-bit conditions because the compatibility. I downloaded i386 version of ubuntu and installed that and when I said "delete the linux partition and make a new one with the same file format" Im not sure if it jsut kept the files.

My GRUB (the Dual-boot loading program) doesn't show the amd64-bit Os on load anymore so i am not sure the problem. 

Can someone people tell em what is eating at my drive space?

Thank you

-Kleam

---

### Post by NICU on 2007-05-04
Hi, Ubuntu should definitely not take up that much space.  I don't know what could cause it to be so big.  I can help on the first question though.

You can use Gparted (Ubuntu's partition manager in the OS and LiveCD) to resize your NTFS partition.  Make sure you backup anything you want to save before doing this...  Gparted uses a nice GUI that shows free/full space on each drive.  Using a slider on your G: drive you can resize it.  Then (if I recall correctly) you can move your Ubuntu partition to right up to the end of your newly sized G: drive, then expand the Ubuntu directory.  

Depending on how your /etc/fstab file is setup you may get an error after changing the size of any drives because of a bad CRC.  You will have to modify your /etc/fstab file, but we can deal with that if it happens.  Let me know your progress.

---

### Post by stchman on 2007-05-04
> **kleam said:**
> Ok right now this is my setup for harddrives. I understand that It mgiht not have been set up very well.

Harddrive1: 40gb
[INDENT]Drives:
[INDENT]C:\[/INDENT]
Content:
[INDENT]Windows XP OS and system files[/INDENT]
[/INDENT]

Harddrive2:200gb
[INDENT]Drives:
[INDENT]E, F, G, Linux[/INDENT]
Content:
[INDENT]e:\music and videos       Size:50gb  Free space: 10gb[/INDENT]
[INDENT]f:\games and downloads      Size:110gb Free sapce: 20gb[/INDENT]
[INDENT]g:\game ISO files      Size:40 Free sapce: 20gb[/INDENT]
[INDENT]Linux ubuntu Feisty 7.04-desktop-i386      Size:22gb Free sapce: 1.5gb[/INDENT]
[/INDENT]


Ok what I want to do Is take from the g partition, which is NTFS and add it to the Linux partition. I don't understand how I do this.


Also: I think there is a problem with my ubuntu installation.
I don't have much on the linux partition (ubuntu, wine, ati graphics drivers, and WOW) and before I even finished installing WOW It said that my partition was full.

This is what I think happend: I first installed Ubuntu-7.0.4-Desktop-AMD64 on this partition. I had problems understanding how to work whine under the 64-bit conditions because the compatibility. I downloaded i386 version of ubuntu and installed that and when I said "delete the linux partition and make a new one with the same file format" Im not sure if it jsut kept the files.

My GRUB (the Dual-boot loading program) doesn't show the amd64-bit Os on load anymore so i am not sure the problem. 

Can someone people tell em what is eating at my drive space?

Thank you

-Kleam

Yes a properly configured Ubnuntu OS with all the trimmings installed should run under 4GB.  I have not had much experience with AMD64 version.  I have an Athlon 64 and I use the i386 version as there are more things that just work.

Try the 32 bit version.  IMO 64 bit is atill a ways away from greatness.

---

### Post by kleam on 2007-05-04
Extra Information:
-Right now I am using the i386 version
-I got the error when I tried to install WoW using wine-0.9.6

when I was installing wow it said "wow needs 4.6gb you only have 1.5gb left" I clicked ok and i didn't notice anything happen.
-I could still open wow, so i wasn't crying yet.

When I did open wow i had to download a 468mb file, once it was done downloading it said the file would take up 1.8gb and that i only had 1.5 gb of free space left.

I'm going to try to resize the partitions tonight or after school in a few minutes

-kleam

---

### Post by kleam on 2007-05-06
is there a GUI interface for the gpart? I can't understand how to ise the command to resize in the terminal.

when i try to gpart -s it says that the sector must be >=0 but i put in 45000 as the variable.


help again please!

-kleam

---

### Post by NICU on 2007-05-07
Yes there is definitely a GUI.  In the live CD or in Ubuntu the GParted GUI is in your Administrator tools menu.

---

### Post by kleam on 2007-05-07
ok, so to access my administrator tools i would go to system on the top and there would be a drop down. When I do this, Gpart does not exist.

Ive ran the command "sudo apt-get install gpart" and "sudo apt-install gpart"

I don't understand where I open the GUi interface



-kleam

---

### Post by churchi on 2007-05-08
once you add it through synaptic or apt-get then if you go to system, then administrator. you should now see GNOME Partition Editor *should be the first item). i have just installed it and it works and i get an icon under that menu.

---

### Post by kelvin spratt on 2007-05-08
i've just check my root folder 3.95 gb home folder 1.65 are you saving to home folder then copying to your other folders as this could explain your problem make sure you are copying to the folder to save and not leaving temp files download gparted live from their site to repartition then you will not have problems with permissions
as it is not system dependent don't forget to defrag any windows partitions first if you change their sizes

---

### Post by Memocjro on 2007-05-08
You need to use Gparted from a LiveCD. I'de recommend the GParted LiveCD : [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

It does a wonderful job.

---

