---
title: "Multisession with cdrecord not working"
date: 2005-07-29
forum: General Help
---

### Post by SteveF on 2005-07-29
I'm trying to burn multisession CDs.  It doesn't appear that gnomebaker supports it, so I'm trying to do it using mkisofs and cdrecord.

I started by using mkisofs to create an image:
mkisofs -v -r -J -V MyLabel -o myimage.iso mydata

I then burned it using:
sudo cdrecord dev=ATAPI:0,0,0 -v speed=4 -data -eject -multi -tao myimage.iso

This worked fine and I could view the data under Linux and Windows.

For the next session I ran:
sudo mkisofs -v -r -J -C 'cdrecord dev=ATAPI:0,0,0 -msinfo' -M ATAPI:0,0,0 -o mynewimage mynewdata

I used sudo because cdrecord needed it.  I forgot the .iso extension (but I don't think that matters).

I tested the new image using:
sudo mount -t iso9660 -o ro,loop mynewiso /mnt/iso

Everythiing looked good.  I new all files and listed and I was able to access the new file I just added.

I ran:
sudo cdrecord dev=ATAPI:0,0,0 -v speed=4 -data -eject -tao -multi mynewimage

It looks like it ran fine, but when I mount the disk I only see the first session's files.  It looks like cdrecord did not write the new TOC.  I ran cdrecord 2 more times playing around with unmounting to see if I had a lock problem, but the same thing happened.  cdrecord looks like it worked (it writes about 5MB which is the size of the new file I added), but I can't get access to it.

I tried loading the CD on a Windows machine, only could see the original files.

I ran:
sudo cdrecord dev=ATAPI:0,0,0 -toc

It shows 4 tracks (one for each of the sessions I wrote).  I tried mounting the CD with -o session=4.  But it still only shows the original files.  I tired mounting using -o  sector=xxx but mount would not work.

The only thing I see is I get this message when running cdrecord:
cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.

Is this a known issue with the version of Linus I'm running?
Does anyone have any ideas on what I'm doing wrong?

Thanks,

Steve

---

### Post by SteveF on 2005-07-30
Well I found out how to get it to work (from comp.os.linux.misc).  I needed to use ``s for the embedded cdrecord command not ''s.  Also it was recommended to use device names (/dev/hdc) instead of 0,0,0 values.  This worked and I got multisessions fine.

Steve

---

