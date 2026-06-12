---
title: "ntfsclone --rescue help"
date: 2008-06-28
forum: General Help
---

### Post by CM5186 on 2008-06-28
My windows HD crashed and I am using livecd and trying to make a copy of my internal HD ntfs volume to my external USB drive. I am new to this whole thing and just want to recover the files. I am unable to mount the internal drive because of errors to the disk. I don't know how to force mount or anything. When i go to the information about the disk i get this warning: "The disk has a bad sector. This means physical damage on the disk...we suggest making a full backup urgently by running ntfsclone rescue..."  

How do i run ntfsclone rescue. I have no clue how to write code in the terminal. 

A want to copy the entire partion to my external 250gb HD. It is dev/sbd1. can someone tell me what code i need to type to do this. 

THANK YOU!!!

---

### Post by ironring1 on 2010-07-19
I'm sure that this reply is getting to you far too late to help, but just so that the answer is here for other users, here is the command:

sudo ntfsclone --save-image --rescue --output image_file.img /dev/sdg1 

Replace /dev/sdg1 with whatever partition you wish to clone.  If you are unsure, run gparted (partition editor) to see which one is which.  The image taken of the disk will be written to image_file.img.  If/when bad sectors are encountered, you will get a warning on the screen, but ntfsclone will just continue reading until it gets to good data again.

---

### Post by alecz20 on 2010-12-12
I have a similar problem, but when I try to clone the system, I get errors that the filesystem check failed consistency check.

It also says to run chkdsk /f on Windows and reboot twice.

I also tried the --force option, but still didn't work.

I am a little bit reluctant to doing a filesystem check on this hard-drive. I don't want to make any changes, I just want to get a snapshot of the current state so if fixing attempts fail, I can start from the same initial conditions.


Any idea on how to get the clone on an inconsistent system, or if it's even possible?

Thanks!

---

