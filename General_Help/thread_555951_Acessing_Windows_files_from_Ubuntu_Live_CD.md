---
title: "Acessing Windows files from Ubuntu Live CD"
date: 2007-09-20
forum: General Help
---

### Post by kais58 on 2007-09-20
Ok so for some unknown reason windows xp died and keeps restarting at the xp load screen and so I would like to know how, if possible, to access the files in the windows partition using a ubuntu live cd as I have what I think is the correct folder with it all in however it says i dont have the rights to access it in order to write the files to cd and I need some help.
thanks

---

### Post by arkara on 2007-09-20
you can acess the windows partition by mounting it from the live cd.
now the thing is linux can only read and not write on the ntfs as far as i know
there is a way to write on a ntfs partition but not from a live cd. its from a linux installation.
even though writing on a ntfs partition form linux is not recommended as it could mess it up..

you should reinstall your windows thats the best solution

---

### Post by rsambuca on 2007-09-20
> **arkara said:**
> even though writing on a ntfs partition form linux is not recommended as it could mess it up..

The ntfs-3g driver is now a stable release, so this is not true.

---

### Post by kais58 on 2007-09-21
I think I should elaborate, I need to copy the files from my windows based system hard drive however windows doesnt work and I would like to use ubuntu to access the files and copy them to a cd/usb stick however ubuntu tells me I dont have permission to/it cant access the drive and this is what I need to get past

---

### Post by rsambuca on 2007-09-21
Ah, OK, I think I got ya now!  Yes, that easily be done from the liveCD.  The steps that you have to do are:

1.  Create a folder to mount the Windows drive.  Open a terminal and enter```
sudo mkdir /Windows
```
2.  Mount the Windows drive. **```
sudo mount /dev/hda1 /Windows
```
3.  Just copy the files to your USB stick!

** You will have to replace the /dev/hda1 with whatever your Windows drive is (It is probably /dev/hda1 or /dev/hda2, or /dev/sda1 or /dev/sda2, depending on your system.

---

### Post by jchan2 on 2007-11-15
I'm in a similar situation, except I'm dealing with unbootable Powerbook G4 Mac OSX. Could the same procedure be done with Mac OSX where I can access and backup my files?

---

