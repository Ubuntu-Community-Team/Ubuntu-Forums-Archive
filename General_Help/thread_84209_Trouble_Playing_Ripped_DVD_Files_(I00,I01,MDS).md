---
title: "Trouble Playing Ripped DVD Files (I00,I01,MDS)"
date: 2005-10-30
forum: General Help
---

### Post by mousepad on 2005-10-30
From winXP, I have ripped DVD files using DVD Decrypter.  They have file extensions: i00,i01,MDS.  I used Daemon Tools to load the i00 file onto an imaginary drive and play using any multimedia player.  I'm not sure how to do this in x.  What's interesting is that a thumbnail appears for the i01 file and I am to play it just by double clicking on it and using totem-xine, but usually that is only the special features section of the DVD.  Thanks for your help guys.

---

### Post by mustang on 2005-10-30
[QUOTE=mousepad]From winXP, I have ripped DVD files using DVD Decrypter.  They have file extensions: i00,i01,MDS.  I used Daemon Tools to load the i00 file onto an imaginary drive and play using any multimedia player.  I'm not sure how to do this in x.  What's interesting is that a thumbnail appears for the i01 file and I am to play it just by double clicking on it and using totem-xine, but usually that is only the special features section of the DVD.  Thanks for your help guys.[/QUOTE]

Are you sure you're playing the right .vob files? Different vob files correspond to different sections of the movie and if I recall correctly, the special feature section has its own vob file. So did you try the other i00?

---

### Post by mousepad on 2005-10-30
I'm not sure what a vob file is, but I only have 3 files per DVD (i00,i01,mds).  If I try playing i00 in totem-xine, I get a message that says I don't have the right plugins to play the file.

---

### Post by mustang on 2005-10-30
How big are the files?

For DVD playback:

sudo apt-get install libdvdcss2

---

### Post by RAOF on 2005-10-30
Ok, those files are a copy of of the filesystem of the DVD, suitably decrypted, but in a strange format.  If it were in .iso format, you could use the "loopback" device to mount the .iso (essentially the same way you do with daemon tools) and play with that (I've done it in the past, but totally forgotten the specifics.  Try "man mount", and look for "loopback", I think).  I don't know of anything which will allow you to mount those under linux, but google might :)

---

### Post by Nomad64 on 2005-10-31
To mount an ISO file, execute the following commands (be sure to replace *file.iso* with the accual .iso file name):
```
sudo mkdir /media/iso
sudo modprobe loop
sudo mount *file.iso* /media/iso/ -t iso9660 -o loop
```

Then, after you are done, you can unmount it using umount:
```
sudo umount /media/iso
```

After it is mounted, totem will try to play it...but my experiences with Totem have been horrid at best. So I use xine, problem is that you have to mount it differently so xine knows how to read the DVD.
```
sudo modprobe loop
sudo mount *file.iso* /dev/dvd/ -t iso9660 -o loop
```
This loads the .iso file in the /dev/dvd/ directory, which Xine looks at to read DVDs.

If you have the files ripped, and not the ISO, you may want to either use WINE with DVD Shrink installed, or goto WinXP and download/install DVD Shrink (probably easier and faster). This program can load the files, and allows you to then save them in .ISO format, if you wish. If you have Nero installed, you can just burn it to a DVD.

---

