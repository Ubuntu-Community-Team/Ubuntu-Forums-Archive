---
title: "clone system to smaller SSD"
date: 2021-01-26
forum: General Help
---

### Post by michael351 on 2021-01-26
I have a 2TB hard drive with Ubuntu and my 'home' directory loaded taking up a total of about 600 GB. I want to "clone" both over to a 1 TB SSD.
The boot partition is an ext4 system and root and home are LVM.

I was wondering how (if) I can just "dd" from the old drive to the SSD and then boot from my new drive?

I'm sure this has been done before, just can't find a straight forward set of steps to follow.

---

### Post by oldfred on 2021-01-26
UEFI or BIOS?

I believe in new install. And then restore from you standard backup. That confirms you backup is complete when you still have old install to get anything still missing. And then more confidence when hard drive totally fails you have a way to recover.

You cannot have duplicate UUIDs nor duplicate GUIDs if UEFI/gpt.
And if LVM, cannot have duplicate volumes.

Or you have to totally disconnect HDD if booting from SSD.
Several recent threads where users tried dd and just had issues. Not sure if they got it working or not, others that helped that user may see this.
The dd is usually the last suggestion as it is relative slow & copies bit for bit including all your unallocated/blank space.
Others have suggested clonezilla, but do not know about LVM as I do not use it.

---

### Post by GhX6GZMB on 2021-01-26
dd is a bit-for-bit copy, and needs a target larger than the source to work.

I second oldfred's suggestion to do a new install.

Use a file-based backup to store and retrieve your old system, much more comprehensive and reliable.
Examples: Timeshift or BackInTime, but there are more out there.

---

### Post by michael351 on 2021-01-26
New install it is ... 
I have all of the files backed-up, but you know how it is. Once I get up and running, lots of subtle config files and changes I long forgot about will 'bite' me.
Especially Samba. I'm hoping all I would have to do is copy over the smb.conf file. We'll see.

One benefit - SSD should be a lot faster to boot my server after all of these years.

Here goes ...

---

### Post by GhX6GZMB on 2021-01-26
This might help:
[https://ubuntuforums.org/showthread.php?t=2447108](https://ubuntuforums.org/showthread.php?t=2447108)

---

