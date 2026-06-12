---
title: "[SOLVED] Help: Ubuntu GRUB Error 15"
date: 2007-11-04
forum: General Help
---

### Post by TuxTwig on 2007-11-04
I've been running Vista on my desktop for a while now. A week ago, I installed Ubuntu to a seperate parition (My D Drive in Vista). My initial problem was that I couldn't boot Vista from GRUB (a black screen appeared after the Vista loader showed up). I tried to reinstall GRUB and Ubuntu today because someone posted that it might help. Now, not only can I not boot Vista, whenever I try to load GRUB to boot Ubuntu, all I get is the Error 15 message. If you know why this happens and any way I can fix it. (I can only access tools from my Live DVD), please post here. I'd really appreciate it. (I've been reading through posts and trying to learn Ubuntu for the past week just to fix this problem with no success, I am on the verge of tears.) 

I've tried the suggestions from this website, but I can't seem to access the menu.lst file from my live DVD. 
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

Any posts would be of **great help**.

-Twig 8)

If you need any additional information, just post here and tell me what to post. :)

---

### Post by Pumalite on 2007-11-04
Try Knoppix Live CD; it mounts drives/partitions automatically and from Terminal post:
cat /boot/grub/menu.lst
(if you can't find it anywhere, you have to reinstall)

---

### Post by disturbedite on 2007-11-04
this happened to me after a fresh install of gutsy.  i used the guided install to format a disk but grub didn't know the correct path of the newly created gutsy partition.

i had to change the root line in fstab from hd(1,0) to hd(0,0) to solve the grub error 15.

keep in mind, you have to edit that file as root/su and save it in order to avoid having to edit it every time you boot/reboot.

---

### Post by TuxTwig on 2007-11-04
Pumalite, mind giving me the link to where i can download the Knoppix .iso file?

Disturbedite, mind giving me instructions to how I can fix it..not quite understanding your post?

EDIT; seems like Disturbedite's post seems less time-consuming and logical.. Please post clearer instructions! (Sorry, I'm a noob 8))

---

### Post by TuxTwig on 2007-11-04
Oh, ok I figured out how to do it. Thanks, I'm trying it now.

---

### Post by TuxTwig on 2007-11-05
Fstab should be accessable and editable from the Live DVD right? I think there's something wrong with mine.. (Should I use vi or Gedit?)

Using Gedit, this is my fstab file,

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0

Weird or what? :(

What is the terminal command for fstab??

---

### Post by TuxTwig on 2007-11-05
If you kno what's wrong or have an idea, please post. :) 

Like I've said, **any** ideas or comments will help.

Thanks so much. 8)

---

### Post by TuxTwig on 2007-11-05
Also, If you have any ideas or suggestions to what I should do to fix my Vista boot problem, please post here as well. And I will try your suggestions after fixing this GRUB problem. Alternatively, if you have any ideas on how to fix Vista directly (I'm not that concerned about the Ubuntu, I can fix it after I access my Vista, which has a lot of important files I need) please post here. Going to bed now. See you all soon. 8)

-Twig

---

### Post by notna01 on 2007-11-05
the vista error occurs when you have the hard disks mounted on the ubuntu root account, to fix:
login to root
right click on the hdds on the desktop
click unmount
logout
shutdown
restart into vista

error 15 = kernel not found so put in ubuntu cd, boot, open terminal, type update-grub or grub-update
then reboot and grub should work

---

### Post by TuxTwig on 2007-11-05
ALright, thanks for suggestions (too bad won't be trying these out till tommorow). Goodnight. How do you use the Ubuntu root account?

---

### Post by confused57 on 2007-11-05
> **TuxTwig said:**
> ALright, thanks for suggestions (too bad won't be trying these out till tommorow). Goodnight. God bless you.
If you have a Vista install DVD(not a recovery disk), you can use the bootrec.exe utility to restore your mbr:
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

You might want to open a terminal & post the output of:
```
sudo fdisk -l
```
-l is a small "L"

In order to access files on your Ubuntu root partition, you need to mount it, using the live DVD/CD:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

If you have access to another computer, you could download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's a small download(5-7 Mb) and might be able to boot Vista or Ubuntu and it can also restore the mbr.

---

### Post by TuxTwig on 2007-11-05
> **confused57 said:**
> If you have a Vista install DVD(not a recovery disk), you can use the bootrec.exe utility to restore your mbr:
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

You might want to open a terminal & post the output of:
```
sudo fdisk -l
```
-l is a small "L"

In order to access files on your Ubuntu root partition, you need to mount it, using the live DVD/CD:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

If you have access to another computer, you could download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's a small download(5-7 Mb) and might be able to boot Vista or Ubuntu and it can also restore the mbr.

I only have the Vista OEM Dvd and can't access bootrec.exe.


I've tried SGD and I've had no success.

I'll post the results of fdisk when I get home.

---

### Post by Tethtibis on 2007-11-05
best I've found, run the live cd, go into partition editor, delete all partitions excep the vist one, apply, then expand the vista partition to max, run ultimate boot cd to boot into vista(super grub loader in filesystem directory), let it do it's error check, then run the live cd and reinstall.

---

### Post by TuxTwig on 2007-11-05
Hmm, since I'm a noob. I better post a screenshot of my Gparted Scan. :)

Nvm, I deleted my D Drive (Second Partition, the one with the Linux System files) and resized my C Drive to 232GB which is my entire Hard Drive.

OMG. THANK YOU SO MUCH. YOU ARE MY HERO. <3 I was finally able to access Vista. :)

So, now do I reinstall Ubuntu from the Live DVD?

Thanks for all your help. SOLVED.

---

