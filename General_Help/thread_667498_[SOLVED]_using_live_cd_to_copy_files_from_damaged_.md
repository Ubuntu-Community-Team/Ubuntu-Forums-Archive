---
title: "[SOLVED] using live cd to copy files from damaged windows xp partition to external ha"
date: 2008-01-14
forum: General Help
---

### Post by VCSkier on 2008-01-14
A friend of mine had a damaged Windows XP installation on his laptop, which he needs to recover data from.  He is interested in linux, but is still dependent on windows, and he would like me to show him how to use a live cd to access his windows drive and copy his data to his external hard drive, which I assume will be NTFS as well.  I'd like to do it as simply as possible, so as to not make linux seem complicated to a potential user.  If there's a way, for his sake, I'd rather not use terminal.

I know that Linux Mint has a tool called mintDisk.  I'm not familiar with it, but I was, wondering if that would be a simpler way for me to show this to him.  Would it work from the Live CD?

If not, would would be the best way to do this from Ubuntu's live cd.  I assume I would need to unmount the partition first, and then remount it properly from terminal, which would be OK.  What would be the proper mount command to do this.

My last question is regarding the external hard drive that we will be coping the files *to*.  Will that be a problem, or will the Live cd automatically mount it with read/write access and proper permissions when it is plugged in?

This friend is planning on coming over this afternoon for me to do this for him, so prompt responses would be greatly appreciated.  :)  Thanks.

---

### Post by TeeAhr1 on 2008-01-14
First, you need to find out what partition Windows is on.  The easiest way to do this from the live CD is to go to Partition Editor (it's in System > Administration) and find the NTFS partition.  It'll be something like /dev/hda1 or some such.

Next, bring up a terminal and do:
sudo mkdir /mnt/windows
sudo mount /dev/hda1 /mnt/windows
(replace /dev/hda1 with the windows partition name)

This will automaticaly make an icon on the desktop called /mnt/windows, which you should be able to enter and browse.  Plug in the external drive (it'll come up by itself), and you're in business.

-pd-

---

### Post by VCSkier on 2008-01-15
For what it's worth, I didn't even need to use the terminal.  From within nautilus, when I tried to open the hard drive, Ubuntu automatically mounted the partition, and everything was good to go.  Ubuntu has come a long way.  Things are getting so easy!

---

### Post by Saartjexxx on 2008-01-15
Thank you, seriously!

Now, how do I do this with an external hard drive that is also ntfs?

Greetings

---

### Post by VCSkier on 2008-01-17
Is it not all working automatically, like it did for me?  I think you just need to find the device in nautilus, and Ubuntu will mount it properly for you.

---

