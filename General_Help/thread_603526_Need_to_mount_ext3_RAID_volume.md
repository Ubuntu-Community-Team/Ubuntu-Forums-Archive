---
title: "Need to mount ext3 RAID volume"
date: 2007-11-05
forum: General Help
---

### Post by bkuras on 2007-11-05
I have a Maxtor Shared Storage II external hard drive array that failed recently. I was able to take it apart and connect one of the drives that were configured for RAID 1.

I can see the volume in GParted but I am unable to mount it. Do I need to do anything special since this was part of RAID 1 array?

Here is a screenshot of GParted. The volume in question is highlighted. Please help!
[IMG]http://www.limbomusic.com/screenshot.png[/IMG]

---

### Post by fjgaude on 2007-11-05
Do you wish to save the data on the drive? And use it as a single drive? 

It looks like the drive could be mounted by GParted. Are you using GParted from a LiveCD? Do you need instructions as to how to mount?

Questions, questions, eh?

---

### Post by az on 2007-11-05
I don't know if you need to use a raid tool to use the drive.  

I would image the drive first, so that you don't lose any data by tring to access the filesystem on it.

Do these packages help?

---

### Post by bkuras on 2007-11-06
> **fjgaude said:**
> Do you wish to save the data on the drive? And use it as a single drive? 

It looks like the drive could be mounted by GParted. Are you using GParted from a LiveCD? Do you need instructions as to how to mount?

Questions, questions, eh?

I am using GParted from a live CD.  I would love some instructions on how to mount.

I'd like to get the data off the drive and onto whatever I purchase to replace the junky Maxtor Shared Storage II.

---

### Post by fjgaude on 2007-11-06
Okay, first we make a mountpoint, then we mount:

```
sudo mkdir /media/sda6
sudo mount /dev/sda6 /media/sda6
```

We use the media folder to create the subfolder, sda6; you can use whatever names you wish. I've assumed the LiveCD you are using is a Ubuntu one. Let me know if that is not true.

Now you can copy data from the various foldrs you see mount, using File Browser going to the /sda2 folder. The new drive has to be online, mounted also, of course.

Let us know how you do, if you need more information.

---

### Post by bkuras on 2007-11-07
This is the response I get when trying those commands:

**mount: unknown file system type 'linux_raid_member'**

Any ideas?

Thanks so much for your help so far fjgaude.

---

### Post by fjgaude on 2007-11-07
You could try:

sudo mount -t ext3 /dev/sda6 /media/sda6

If that doesn't work, go into Gparted and set the Manage Flags to normal, boot, or nothing. Then try mounting again.

Keep us informed...

---

### Post by psusi on 2007-11-08
Ummm... why don't you just plug it back into the raid enclosure?  Why did you take it out in the first place?  If it is a raid-1, it should continue to operate perfectly normally in the event of a single drive failure.

---

### Post by bkuras on 2007-11-12
The enclosure is dead.  The hard drives are fine.  The Maxtor Shared Storage II claims to be RAID 1 but the controller itself sucks.  I had to take the drives out in order to access the data.

I was able to access the drives using Knoppix 5.1

Thanks for all your help.

---

