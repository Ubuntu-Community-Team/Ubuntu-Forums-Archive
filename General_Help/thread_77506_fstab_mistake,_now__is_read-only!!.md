---
title: "fstab mistake, now / is read-only!!"
date: 2005-10-16
forum: General Help
---

### Post by aubuti on 2005-10-16
Who was it that said a little bit of knowledge is a dangerous thing.....

It's been a while since I've used Unix based systems, mostly AIX and RedHat, and wanted to give BB a try. All was going well, except that my vfat/windows partitions were read-only. So I edited fstab, but stupidly didn't stop at the vfat devices. I also stupidly changed the root partition to read:

/dev/hda5  /  ext3  rw,user,noauto,errors=remount-rw 0 1

Something in there, probably at least the remount-rw, is an invalid option, so at boot time it balks and mounts the root partition as read-only. Meaning that it won't let me even get back to my old fstab, even when I boot in recovery mode and am logged in as root, because the filesystem is mounted read-only.

Is there a way to make the root partition r/w again?

Many thanks in advance.

---

### Post by timelord726 on 2005-10-16
Hi there,

Total shot in the dark here, but perhaps you could try booting off a Linux live CD (i.e. Ubuntu or Knoppix), mounting your root partition, and editing /etc/fstab from there?  Just a thought, but it might be an option worth exploring.

Good luck!

---

### Post by aubuti on 2005-10-16
Sorry to follow-on my own post, but, never mind about the earlier posting. I've now learned the 'remount' option on `mount', which got me back to r/w mode.

Will now *carefully* edit fstab to take care of the vfat entries!

---

### Post by mlomker on 2005-10-16
> Is there a way to make the root partition r/w again?


Boot to a CD version of linux.  You could use the Ubuntu installer disc and manually mount the partition, but Knoppix would make it easy.

---

### Post by timelord726 on 2005-10-16
Glad you got everything working again!  :)

---

### Post by matthew on 2005-10-16
Glad you got it working again! This reminds me of the time, about a week after my first linux install, when I had a permissions porblem with something. I learned the chmod command from a book, read the man page and thought, "Hey, I'll just change the permissions on the whole drive once and for all," and promptly typed
```
sudo chmod 777 -R /
```
followed by some confusion, frustration, and a complete reinstall.

I am so glad your mistake ended up better than my first one with permissions.

---

### Post by aubuti on 2005-10-16
Thanks for the suggestions, and sorry about the false alarm. My first venture into the forum, and it appears to be like everything I've seen so far with Ubuntu: a class act.  Cheers.

---

