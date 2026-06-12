---
title: "Similar to Acronis?"
date: 2007-07-23
forum: General Help
---

### Post by SegMat on 2007-07-23
Hello all,

I recently switched over my 4 computers to Linux.  Ubuntu on the main one, and Xubuntu on my 3 older ones.  I ran XP Professional before Ubuntu and I used Acronis for imaging software.  I'm wondering if someone could help me figure out what a good backup/imaging software is and how to use it.  I don't know how well Acronis would work because Linux makes many more partitions than Windows and so I don't know which one(s) I'd have to back up and where I could put the images.  If someone could give me some advice that would be great.  My main reason for this is so that I can test certain software and if I don't like it, I can totally get rid of it easially without uninstalling, I could simply restore an image.  If there are other similar methods that I could use other than imaging I would be grateful for those as well.  Instructions on how to use any program mentioned in replys would be great as I am new to this whole thing.

Matt Segstro

---

### Post by noynac on 2007-07-23
You can use TrueImage to backup your Linux install. It's best to save the images to an external hard drive. If you do not dual boot with Windows on one partition, you would have to boot to the TrueImage recovery CD to create and restore images, but that's pretty easy to do. I back up the entire drive, although I have on occasion created and restored images of just one or a few partitions. 

There are other programs that can be used to image your hard drive, but reliability is number one for me in a backup program and TrueImage has never failed me.

---

### Post by SegMat on 2007-07-23
Which partitions do I have to back up to give me a complete backup of my system like backing up a C: drive in Windows?  Which is the C: drive for Linux?

---

### Post by noynac on 2007-07-23
> **SegMat said:**
> Which partitions do I have to back up to give me a complete backup of my system like backing up a C: drive in Windows?  Which is the C: drive for Linux?

The answer to your question depends on how the drive was partitioned at the time you installed Linux. On my drive, I would only have to back up the EXT3 partion and swap partition. Your drive may be different. 

I have two suggestions. First, you need to learn a bit about the Linux file organization. It is different from Windows, and you need to understand how things are organized in Linux. 

Secondly, boot to the TrueImage recovery CD and go to the point where you are going to backup the ENTIRE DRIVE. This will allow you to view how the drive is organized and what you need to back up.

For now, until you learn a bit more, I would back up the entire drive if at all possible.

---

### Post by rbmorse on 2007-07-23
Noynac gives good advice. I use Acronis, too.  

Since I have a live Windows XP installation on the machine I can backup my Linux partition(s) when while booted in XP, or as mentioned, I can use the Acronis "rescue CD."  Either method works fine.

---

### Post by SegMat on 2007-07-23
Thanks to both of you for your advice, I will try it out as soon as I can.  I'm really impressed with Ubuntu, it can substitute very easially for XP.  There is nothing so far that I did in XP that I can't do in Ubuntu.  As well, this forum is a great way to do things.  In XP, there isn't anything like this.  This is fantastic.

Matt Segstro

---

