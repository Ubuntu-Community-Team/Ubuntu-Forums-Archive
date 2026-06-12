---
title: "Chroot Jail"
date: 2017-01-08
forum: General Help
---

### Post by newbie2linux2 on 2017-01-08
Hi -

I'm following this guide [https://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](https://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/) to access encrypted files on the old drive. However, I cannot copy to the /data folder created as root when I'm in the chroot jail as it says I don't have the permissions. Also, how do I mount the my laptop drive correctly?
I want to be able to copy the unencrypted files under chroot from the old drive onto the new drive with a fresh ubuntu on the notebook?

what am I missing that the guide doesn't state explicitly?

Thanks very much!

---

### Post by coffeecat on 2017-01-08
Support, not chat.

*Thread moved to **General Help**.*

---

### Post by newbie2linux2 on 2017-01-08
Just tried to copy to a shared Windows folder using the rsync and scp commands but have always gotten connection timed out on port 22. What am missing???

> **newbie2linux2 said:**
> Hi -

I'm following this guide [https://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](https://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/) to access encrypted files on the old drive. However, I cannot copy to the /data folder created as root when I'm in the chroot jail as it says I don't have the permissions. Also, how do I mount the my laptop drive correctly?
I want to be able to copy the unencrypted files under chroot from the old drive onto the new drive with a fresh ubuntu on the notebook?

what am I missing that the guide doesn't state explicitly?

Thanks very much!

---

### Post by newbie2linux2 on 2017-01-08
Hi -

My Ubuntu HDD got corrupted during a botched upgrade and I'm trying to recover the files there.

Having booted from a LiveCD, mounted the HDD and chroot'd, I managed to decrypt the home folder. Now I'm in the chroot environment, how do I transfer these files from the hard drive?! Can I mount an external HDD and copy the files??

Thanks!

---

### Post by kpatz on 2017-01-08
I'd mount the external drive to a directory outside the chroot to a directory accessible within the chroot.  If you're chrooting the root of the HDD from a live CD, you could mount the external to the mnt folder.

So, something like:

```
mount /dev/sda1 /mnt   #internal HDD
mount /dev/sdb1 /mnt/mnt #external HDD
chroot /mnt
```
(now external HDD available within the chroot under /mnt)

---

### Post by newbie2linux2 on 2017-01-08
Thanks kpatz!
I had exactly the same idea however once I'm chroot'd, I need to
su - myusername
to be able to do the ecryptfs the files in the /home folder. Once I do that, I lose the privileges to move the unencrypted files to the /mnt folder (per your example)...
How do I resolve that?!

Thanks!

---

### Post by kpatz on 2017-01-08
Is the external drive formatted NTFS (Windows), or something Linux like ext4?

If it's NTFS, find out the UID and primary GID of myusername by running "id myusername" within the chroot, or examining /etc/passwd (/mnt/etc/passwd while mounted) on the HDD.  If you run id, you'll see something like this:```
uid=1000(myusername) gid=1000(myusername) groups=1000(myusername),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),113(lpadmin),128(sambashare),132(vboxusers),1002(share)
```

Specify the UID, GID, and umask when mounting the external drive.  umask=000 will give all files/directories 777 permissions so full access.
```
mount -o uid=1000,gid=1000,umask=000 /dev/sdb1 /mnt/mnt
```Then your user ID will have "ownership" of the external drive and should have write access.

If it's ext4 or some other linux filesystem, from within the chroot but before you run su, run:
```
chown -R myusername:myusername /mnt
```or```
chmod 777 /mnt
```

---

### Post by newbie2linux2 on 2017-01-09
Many thanks kpatz! The external drive is a Linux fs. Will try this later in the day and report back!

---

### Post by kevdog on 2017-01-09
Are you trying this over a network?

---

### Post by coffeecat on 2017-01-09
@newbie2linux2, I've merged your two threads as they were essentially about the same thing and you are getting replies to both. Which is confusing to all.

---

### Post by newbie2linux2 on 2017-01-09
kpatz, that worked! I've managed to copy the files. Thanks for your help!
One (paranoid) question: is it possible that I may not have copied all the files? I had over 100gb of data, tried comparing the folders but didn't get any output after about 40min or so...

---

