---
title: "resize and clone xp using Gparted"
date: 2008-06-30
forum: General Help
---

### Post by boyofford on 2008-06-30
Hi, have just ordered a new computer from Dell which is coming with vista and a xp 'downgrade'.
This will mean that it will come with xp pre-installed but only a vista os disk.
There will be some backup software included but this will fix problems with xp, not allow for reformatting etc.

So what I'm planning on doing is 
1. removing all bloatware on new computer.
2. installing all the software i need and getting up and running.

then..
3.defragmenting the harddrive
4. running **Gparted** on ubuntu livecd and resizing xp partition.
5. cloning the reduced partition into some free space.

Hopefully this would mean that if xp went wrong i'd be able to use gparted on livecd to just put the saved xp partition clone back on top of the original partition top fix.

Would any/all of this work? anyone see any problems with this approach?
I've used gparted before to resize my ubuntu home partition, but never used it to clone or on windows partitions.

all comments welcomed!:popcorn:

---

### Post by sillyxone on 2008-06-30
I would swap step 3 and 4 (but requires additional/external drive).

When I setup a Windows machine for my mom, I just do as you do: install, cleanup, defrag. Then using CloneZilla ([http://www.clonezilla.org/](http://www.clonezilla.org/)), I clone the Windows partition and put it on a bootable restore DVD so that if anything wrong happens, she just need to pop the DVD in, bootup, press Y and the machine is back in good state in 15 minutes. She lives in a different country so this is crucial.

Note that in my setup, I always have two partitions for Windows. One partition just to to store system files and programs (about 8-16GB) and another partition to store user data (in her case of Windows only machine, it's the rest of the HDD). I used TweakUI to redirect user folders (Document, Desktop) to the data partition so that ClonneZilla only restores the system partition without affecting user data (same idea as putting /home on a separate partition).

CloneZilla only images data, ignoring free spaces so you will have the minimum sized compressed image (that's why a 16GB partition could fit into a DVD as my Windows installation take only about 4GB). It works very well with most types of partition, including NTFS and ext3.

So, in your case, you can resize the partition first then clone it to the free space (with a new partition), or play it safe by cloning the partition to an external drive before resizing it. I think you'll have to use CloneZilla to do the cloning. Gparted only works on the partition table, I think.

---

### Post by boyofford on 2008-06-30
> **sillyxone said:**
> I would swap step 3 and 4 (but requires additional/external drive).


Yeah, only gona be one hard drive so think will have to do in this order

> **sillyxone said:**
> 
When I setup a Windows machine for my mom, I just do as you do: install, cleanup, defrag. Then using CloneZilla ([http://www.clonezilla.org/](http://www.clonezilla.org/)), I clone the Windows partition and put it on a bootable restore DVD so that if anything wrong happens, she just need to pop the DVD in, bootup, press Y and the machine is back in good state in 15 minutes. She lives in a different country so this is crucial.


That sounds perfect for me, though a bit confused by exactly what i have to do to achieve this from website?

> **sillyxone said:**
> 
Note that in my setup, I always have two partitions for Windows. One partition just to to store system files and programs (about 8-16GB) and another partition to store user data (in her case of Windows only machine, it's the rest of the HDD). I used TweakUI to redirect user folders (Document, Desktop) to the data partition so that ClonneZilla only restores the system partition without affecting user data (same idea as putting /home on a separate partition).


I have all my computers set up with seperate partitions for my files as you do, find it much safer in case of system screw ups!
Its a computer for work that i'm setting up, so doing all my research now so limited down time, and red faces when stuff doesn't work! dam dell for not supplying a xp disk! for work I normally just wipe the computers when i get them and completely clean reinstall with partitions as needed.

---

### Post by sillyxone on 2008-06-30
In that case then, resize using Gparted, create a new partition to store the image, use CloneZilla to read the Windows partition into an image, and optionally make a bootable restore DVD from that image.

About CloneZilla, you may want to with CloneZilla Live ([http://www.clonezilla.org/clonezilla-live/](http://www.clonezilla.org/clonezilla-live/)), which is a bootable CD that you then can perform imaging after booting up from it. All the information are explained very carefully on that webpage, including creating bootable restore CD/DVD.

When creating a bootable restore CD/DVD, you'll need to use the Debian bootable template ISO. It can be downloaded here:

[http://gnupg.cdpa.nsysu.edu.tw/local-distfiles/clonezilla-live/template-files/stable/](http://gnupg.cdpa.nsysu.edu.tw/local-distfiles/clonezilla-live/template-files/stable/)


About Windows XP downgrading, does it come with a CD/License Key? Can you use it with any Windows installation CD? Just curious how they play with this.

---

### Post by boyofford on 2008-06-30
> **sillyxone said:**
> In that case then, resize using Gparted, create a new partition to store the image, use CloneZilla to read the Windows partition into an image, and optionally make a bootable restore DVD from that image.

About CloneZilla, you may want to with CloneZilla Live ([http://www.clonezilla.org/clonezilla-live/](http://www.clonezilla.org/clonezilla-live/)), which is a bootable CD that you then can perform imaging after booting up from it. All the information are explained very carefully on that webpage, including creating bootable restore CD/DVD.

When creating a bootable restore CD/DVD, you'll need to use the Debian bootable template ISO. It can be downloaded here:

[http://gnupg.cdpa.nsysu.edu.tw/local-distfiles/clonezilla-live/template-files/stable/](http://gnupg.cdpa.nsysu.edu.tw/local-distfiles/clonezilla-live/template-files/stable/)


About Windows XP downgrading, does it come with a CD/License Key? Can you use it with any Windows installation CD? Just curious how they play with this.

cheers mate, 

don't think will be coming with licence key for xp, just vista, and defo not a xp disk.

---

