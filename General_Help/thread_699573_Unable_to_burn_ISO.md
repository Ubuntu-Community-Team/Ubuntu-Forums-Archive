---
title: "Unable to burn ISO"
date: 2008-02-17
forum: General Help
---

### Post by Indy452 on 2008-02-17
I have downloaded the Kubuntu 7.10 to try out and since I have never burned a cd with Ubuntu I might need some help here.

I'm using brasero for the job and it comes up fine but when I click "burn" an error message pops up stating that there is no cd in the cd writer. I have a fresh 700MB writable cd in the drive but I can't seem to figure out why the cd writer wont recognize that there is a cd in the drive.  when I load the drive with a fresh cd an icon appears on my desktop that has the properties etc of the cd in the drive.  I don't get it. Does this external cd writer need to be mounted or something?  If so where can I find the "mount" button.  I know that Ubuntu recognizes the drive, its all listed in the drive to write to category.  

I hope someone can help. If I can get this application to work Ubuntu will have far outweighed my expectations and will probably become my primary OS.:)

Thanks for the help, Neal

---

### Post by sb12 on 2008-02-17
> **Indy452 said:**
> I have downloaded the Kubuntu 7.10 to try out and since I have never burned a cd with Ubuntu I might need some help here.

I'm using brasero for the job and it comes up fine but when I click "burn" an error message pops up stating that there is no cd in the cd writer. I have a fresh 700MB writable cd in the drive but I can't seem to figure out why the cd writer wont recognize that there is a cd in the drive.  when I load the drive with a fresh cd an icon appears on my desktop that has the properties etc of the cd in the drive.  I don't get it. Does this external cd writer need to be mounted or something?  If so where can I find the "mount" button.  I know that Ubuntu recognizes the drive, its all listed in the drive to write to category.  

I hope someone can help. If I can get this application to work Ubuntu will have far outweighed my expectations and will probably become my primary OS.:)

Thanks for the help, Neal

you dont want to mount it, I am guessing it is a hal error probably.  try from a terminal

wodim isoname.iso

and see if that works

---

### Post by Indy452 on 2008-02-17
wodim isoname.iso
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/sr1
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TOSHIBA '
Identification : 'DVD-ROM SD-M1402'
Revision       : '1008'
Device seems to be: Generic mmc2 DVD-ROM.
wodim: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.


This is what I get in terminal code you gave me. What does it mean?  I'm not sure. 

I'm using an external cd writer that is older but worked fine with my other computer. I like this external for ISO because its naturally slow.

Any other ideas?

Neal

---

### Post by mouseboyx on 2008-02-17
you could download cdrecord
sudo apt-get cdrecord
and run it as cdrecord <isofile.iso> in a terminal.

---

### Post by Indy452 on 2008-02-17
> **mouseboyx said:**
> you could download cdrecord
sudo apt-get cdrecord
and run it as cdrecord <isofile.iso> in a terminal.

Hi mouseboyx,  what is cdrecord?  I already have two cd burning applications. neither of them are disfunctional. I need help identifying why my cd writer keeps saying there is no disc when there is.

I have no idea where to go that i haven't already.  If you think cdrecord will work I'll give it a shot but I'll wait for more input also.

Thanks

---

