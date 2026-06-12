---
title: "Twisted Question here. Two Linux OS's, backup drives, confusion."
date: 2007-01-26
forum: General Help
---

### Post by Roasted on 2007-01-26
This may make your head spin, so I'm going to try to keep this as simple as possible.

I have two hard drives. They are identicle. WD 250 gig 7200 RPM 16mb buffer SATA drives. I have drive A running Ubuntu with a 30 gig Win2KPro partition, giving Ubuntu the remainder of the drive. I have drive B which has no OS on it. It's an idle drive that I use for backup via an rSync script, which mounts the drive and sync's everything from my home folder on drive A to drive B. 

I have a Linux class starting Monday in school, and the distro we will be learning is Suse 10.2. I was thinking about installing that on my computer as well, so that way I can tinker with my school distro and learn it on my own time, and still have my "home" distro of choice, being Ubuntu.

My question is this. As I mentioned earlier, I have an rSync script for Ubuntu, where my home folder is sync'd to drive B. Now, if I install Suse 10.2 on drive B, what would happen if I were to use my rSync script on drive A (Ubuntu)? Is it possible I could use drive B as a bootable drive with an active OS (Suse 10.2) on it and still have drive A synchronize files (music, pictures, documents, music videos, etc) to drive B? 

Also, another question. Say I wanted to install a small partition of Suse 10.2 on drive A. That would mean I have Suse 10.2, Ubuntu 6.06, and Win2kPro all on ONE 250 gig hard drive. Would Suse 10.2 be able to access any files on Ubuntu 6.06? Or would I be stuck?

---

### Post by rsambuca on 2007-01-26
I would recommend downloading gParted to repartition your drive A, to make room for Suse.  That way, you can have all of your operating systems on the one drive, and use your B drive for storage, backups, etc.  You should be able to access your Suse files from ubuntu, although sometimes you may have troubles due to ownerships, but there are of course workarounds.

---

### Post by Roasted on 2007-01-26
But if I wanted, COULD I put suse on my second drive? I have the script set up to copy the home folder over... so realistically, it shouldn't mess up the system files... right?

If I WOULD go that route, could I set the script to be a two way script? So if I'm in suse I can run the script to copy from drive B to drive A? That way if I use suse to download something and want to back it up, I can back it up on drive A. That'd be kinda sweet...

---

### Post by rsambuca on 2007-01-26
I haven't used rSync, so I have no idea!  It sounds like it should be doable in theory, though.

---

### Post by kosmic on 2007-01-26
Yes you can put Suse in the other drive, an continue to use rsync.

When instaling SUSE make a partition where you want rsync to backup your files like "/backup " and the edit your rsync script so it write to the partition /backup in the B drive ;)

---

### Post by Roasted on 2007-01-27
Ah, I see.

But do you understand what I'm saying? Essentially this is what I was thinking on doing.

Drive A - 250 gig - Ubuntu.
Drive B - 250 gig - Suse 10.2.

And set up a script on EACH distro, where the rsync script syncs whichever drive's home folder I'm on to the OTHER drive's home folder that I am currently not on.

AKA if I'm on Ubuntu and run the script, it'll sync whatever I have on Ubuntu and sync it with Suse. If I'm on Suse, it'll sync whatever I have on Suse with Ubuntu. 

Essentially, if this works, I'd have two fully functional and well rounded Linux operating systems. That way, I start off each distro with the SAME files as far as music, pictures, etc. Then as time progresses, if I'm on Ubuntu and download a music video, run the script, and it'll sync it to Suse. If I'm on Suse and I upload 20 pictures from my digital camera, run the script and it'll sync to Ubuntu.

Do I make sense? And is THIS possible?

---

