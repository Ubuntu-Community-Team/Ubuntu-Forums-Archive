---
title: "Hard Drive Problem"
date: 2008-05-31
forum: General Help
---

### Post by tut on 2008-05-31
So, I downloaded Ubuntu and installed it on my computer giving it 30GB of my second hard drive, however, my computer got messed up and I had to re-install Windows and when I went to check out my hard drive I noticed the 30GB I gave to Ubuntu was gone, is there anyway to get this back?

---

### Post by Rasitiln on 2008-05-31
What do you mean gone? you reinstalled windows and used the entire disk? or some how deleted your ubuntu partition with in the windows partition editor..or is it simply your ubuntu partition isn't selectable upon boot? IE you dont see grub, which lets you choose which OS you want to boot into.

---

### Post by tut on 2008-05-31
I had a full disk free (D:) and I reinstalled Windows removing Ubuntu and the 30GB I gave Ubuntu has gone... :(

---

### Post by jomacintosh on 2008-05-31
I had that problem before.  The restore program that came with my windows machine automatically re-partitions the drive weather you like it or not.  Could this be the case for you? I dumped windows altogether and have never looked back!

jomac

---

### Post by Rasitiln on 2008-05-31
It sounds like you are going to have to resize your windows partition, inorder to get the space back for ubuntu but I cant say for sure unless you post your hard disk lay out.

In order to do that just post a screen shot of your disk layout

Follow these directions if your not sure how to go about doing that. Also do be careful in disk management less you accidentally format something or otherwise break windowss.

> 1 .Log on as administrator or as a member of the Administrators group.
2. Click Start, click Run, type compmgmt.msc, and then click OK.
3. In the console tree, click Disk Management. The Disk Management window appears. Your disks and volumes appear in a graphical view and list view.

---

### Post by tut on 2008-05-31
This is what I get Rasitiln:

[http://img515.imageshack.us/img515/97/pic1jx1.png](http://img515.imageshack.us/img515/97/pic1jx1.png)

---

### Post by ajgreeny on 2008-05-31
Boot into the live ubuntu CD and run sudo fdisk -l in terminal and let's see the output from that.  We will then know if your ubuntu partition and files have really gone, or are just not showing to you at boot, as grub has now been overwritten by the new windows MBR.

---

### Post by tut on 2008-05-31
Sorry I'm kinda new to this how do I run sudo fdisk -l?

I have put the disk in and I'm using the live session user, when I click Computer I can see the drive that I can't see when using windows.

Is that any help?

---

### Post by tut on 2008-06-01
Bump. Anyone able to help?

---

### Post by cariboo on 2008-06-01
Windows is kind of stupid concerning different types of file formats.You need a program like Explore2fs to read ext3 formatted hard drives.

Jim

---

### Post by tut on 2008-06-01
I downloaded that but like I said above, I'm new to this so I don't know what it is I'm looking for.

---

### Post by black drongo on 2008-06-01
tut
follow this link
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28install%29%7C%28windows%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28install%29%7C%28windows%29)
it should solve your problem. if u are unable to follow the directions pls do let me know:)

---

### Post by tut on 2008-06-01
I'm not looking to reinstall Ubuntu at this time, not on this laptop anyway, I'm just trying to get the 30GB of hardrive I lost.

---

### Post by black drongo on 2008-06-01
the fact is u dont have to "reinstall" ubuntu.its there all the time. only thing is your windows does not recognise where it is(or what it is).u only have to point to it by changing the boot loader "grub". u will then get the option of booting either to windows or ubuntu. or if u want to delete ubuntu & hence remove any data in that 30 gb and hence recover that space only, then u can do it from windows by deleting that partition. for this go to control panel >administrative tools>Computer management > Disk manage ment. hope i was of help.

---

### Post by tut on 2008-06-01
Alright, so I deleted that partition using Windows but it still shows 15GB on the second hard drive.

---

### Post by tut on 2008-06-02
Bump. :(

---

### Post by black drongo on 2008-06-02
sorry. i didn't follow that. i understand that u were able to  delete that,(30 GB)right?
then what is this 15 GB in second(?) hard drive 
could u format it to fat/ntfs?

---

### Post by tut on 2008-06-02
When I try formating it and I get this error:

[img]http://img519.imageshack.us/img519/6497/ddfb9.png[/img]

---

### Post by black drongo on 2008-06-02
:confused: i guess that u may have partition table problems, i am also trying a solution for same. 
try booting from ubuntu live  cd . can u see the partition now?
try gparted (system > administration >gparted).
if it shows either the free space or the partition, then u can modify it from there. if it shows a single unallocated disk(with no partitions whatsoever), then u have a partition table problem. which seems to be an involved business. any way, best of luck.

---

### Post by tut on 2008-06-02
Greetings black drongo. I fixed it using gparted, major thanks for helping me through this. :)

---

### Post by black drongo on 2008-06-02
:)

---

