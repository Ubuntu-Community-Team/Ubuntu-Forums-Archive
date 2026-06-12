---
title: "Persistent pen drive partition not correct."
date: 2008-03-08
forum: General Help
---

### Post by Ruzihm on 2008-03-08
Hello, helpful world of Ubuntu-knowledgeable people.  I have installed a persistent boot partition of 32-bit 7.10 Gutsy Ubuntu on an 8gb thumb drive, as per the instructions at [this link,]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") and I seem to have run into a problem.  Despite the flash drive (I am using different names, so it appears for searchers) having a total capacity of 8.0 gb, which is reflected in gparted and fdisk, I seem to only be able to use approximately 2.2 gigabytes of it, according to nautilus.

Now, to my understanding, the thumb drive is partitioned between the live CD's contents, and the persistent partition that is responsible for saving my changes between logins.  Going into nautilus and viewing the properties reveals that the The liveCD-esque partition is a "vfat" format and the persistent partition is "unionfs."  I was wondering if the unionfs format has some kind of size limit and if there may be a workaround, or if there is some other cause I could somehow correct.  

If there is no real solution for this, if there is a way to reduce the persistent partition to 2.2 gb (since apparently, that is all I can use) without losing the data I already have stored on there, that would be greatly appreciated.  Unfortunately this could be a problem, since gparted doesn't recognize its format (instead it names it "unknown") and I am afraid that since it doesn't recognize it, I am doomed to lose my data.

I hope I have given enough pertinent information, but if there is anything else you need to know to help, please tell me and I will quickly answer your questions.

Thank you in advance :)

---

### Post by ssj3strife on 2008-03-08
This is a very interesting scenario you have. I read up on unionfs on wikipedia and it looks like it is designed to be overlayed on top of an existing file system - in this case, the partition for your live cd. What I'm *guessing* is supposed to happen is that you don't save files directly to your second partition. Rather, you save them anywhere you want, and the system magically remembers where they're supposed to be relative to /, via the unionfs partition.

Maybe this is obvious to you, or maybe I have the wrong idea? Like I said, I'm guessing, this is new to me. Why don't you try filling up the space on your drive with one big file, and then finding out how big the file is? That would say for sure how much space the system "thinks" it has to work with. Try a command like this:

dd if=/dev/zero of=~/dummyfile

Make sure it's in your home directory and not directly on either flash partition. If it gets to be bigger than 2.2 GB, I'd say you're in the clear.

---

### Post by Ruzihm on 2008-03-08
I think I know what you're getting at, but believe me, I have little idea of what is going on, as well.  I know that the 2.2 gb *is* a true limit at the moment.  Once subtracting the around 800 MB that is already on the device, I only have 1.4 gb to utilize.  I tried copying a number of somewhat large files from my normal hard drive, to the thumb drive, but when their collective size went over 1.4 gb, I couldn't fit any more onto the thumb drive.

Thanks for the idea, though :)

Edit: 
Oh, and to clarify, I'm booting directly off the flash drive, so the home directory is actually on the flash drive... unless you really _want_ me to put it on the hard drive.  I don't think that would help, because any changes I've made to the hard drive (when I've booted to the flash drive)  stay on the hard drive

---

### Post by ssj3strife on 2008-03-08
Alright, I have a thought! Assuming you followed that guide step by step, then I don't know how one of your partitions wound up as unionfs, since according to that guide, you ran the mkfs.ext2 command.

Actually, I have 2 thoughts. Either one of the files on your flash drive is a loopback device and is somehow limited to 2.2 GB, or the union fs is being stored in RAM and the machine only has 2.2 GB of free mem to work with. I think the former option is probably the more likely one.

Regardless, could you post the output of mount, when booted into the system from the flash drive?

You might also try playing with the baobab tool. It might not be useful, but then again, you might be able to massage it into giving you some helpful information, and it's pretty cool in any case. :)

---

### Post by Ruzihm on 2008-03-08
Gosh, this is a bit anticlimactic.

On my way back to the thumb drive partition to answer ssj3strife's request, I found that it had wiped all of the changes.

Frustrated, I repeated the process and, behold, it works now.  I have all of the space available to my use, and it shows up as ext2 as ssj3strife predicted.  I was wondering why is wasn't ext2, but I think I know the answer.  I think I may have pulled the thumb drive out too early, or perhaps skipped a step.  Oh well, at least we know this problem can be skipped by having some common sense. >_>

Thanks for your help, all.  I'm glad to know I'm not the only one confused by that predicament!

---

### Post by ssj3strife on 2008-03-10
Hah, well, I'm glad you got it working! Now that you got me curious, I might have to try this out for myself... :)

---

