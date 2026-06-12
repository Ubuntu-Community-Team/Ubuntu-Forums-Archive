---
title: "Ubuntu 12.10 boot failure - initramfs/busybox"
date: 2013-02-03
forum: General Help
---

### Post by MRFredB7 on 2013-02-03
I have Quantal Quetzal installed on my laptop (Dell Latitude E6400) and it was working fine for a couple of months until recently when it would fail to boot with mounting failed messages followed by BusyBox v1.19.3 and an initramfs command line (see attached photo).

I've tried looking for a solution to this problem elsewhere in the forums and have found references to the exact same problem in older versions of Ubuntu but nothing specific to 12.10.

If anyone can provide a fix, that would be much appreciated.

Thanks!

---

### Post by MRFredB7 on 2013-02-04
I have Quantal Quetzal installed on my laptop (Dell Latitude E6400) and it was working fine for a couple of months until recently when it would fail to boot with mounting failed messages followed by BusyBox v1.19.3 and an initramfs command line (see attached photo).

I've tried looking for a solution to this problem elsewhere in the forums and have found references to the exact same problem in older versions of Ubuntu but nothing specific to 12.10.

If anyone can provide a fix, that would be much appreciated.

Thanks!

---

### Post by ahallubuntu on 2013-02-04
~

---

### Post by cariboo on 2013-02-04
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by MRFredB7 on 2013-02-04
> **ahallubuntu said:**
> Looks like your / partition couldn't be mounted.  That could be due to a corruption or a failing hard drive.

Boot your Ubuntu live CD or live USB, assuming you have one, and see if you can even mount the main Ubuntu partition on your hard drive.  If you can...unmount it.  (More below.)

Now install GSmartControl on the live CD/live USB.  Start up GSmartControl after install and look at the S.M.A.R.T. Attributes of your hard drive.  Anything highlighted in Pink?  If so - what?

If nothing highlighted in pink for your HD, that's good.  The drive probably isn't failing.

Next, you can run e2fsck on the / partition of your hard drive.  Maybe there's some corruption you can clean up.  You want the partition NOT mounted before running this.  Drop into a terminal.  Use "sudo fdisk -l" to find out which partition it is if you aren't sure.  Then (let's assume it's /dev/sda1) type:

```
sudo e2fsck /dev/sda1
```

and see if it's not clean - and maybe it will fix some stuff.  If there is serious corruption, you may be asked to fix a lot of stuff.  There's an option in e2fsck to say "yes to everything" - but if you get that many problems, you probably won't be booting this thing again, anyway.
Thanks heaps for that! I had no pink-highlighted attributes so all good there but e2fsck seems to have done the trick. It's booting fine now :)

Cheers!

---

### Post by MRFredB7 on 2013-02-04
> **cariboo907 said:**
> Please don't create multiple threads on the same subject, I have merged your two threads.
Sorry about that. I forgot about that rule and wasn't sure if I was posting in the right forum. Will remember for next time though!

---

### Post by alienmindtrick on 2013-03-21
After spending 7 hours in the #Ubuntu channel on IRC to no avail and having to reinstall Ubuntu twice, I finally figured this out.

I'm willing to wager that you encrypted your drive when you installed Ubuntu. Yes or no? I did this both times, and both times I got the error /dev/mapper/cryptswap1, which the leets in the IRC channel repeatedly told me was a failed hard drive. They were wrong, all of them. It's a known error. Ubuntu DOES NOT LIKE TO BE ENCRYPTED!

Yes, I will run into the same issue again and I will have to reinstall Ubuntu again (since I didn't find this problem until after I had reinstalled 12.10), but I plan to do that prior to upgrade to 13.04 Raring.

If you get the error initramfs, you'll probably find that it's the same cause - an encrypted hard drive. Why this isn't notated with a warning on the installation screen is troubling.

---

### Post by Tahchin on 2013-09-15
"sudo e2fsck /dev/sda1" worked for me also but my GSmartControl showed one attribute in Pink as shown in image.

Please let me know the meaning of same. Is it serious? Do I need to change the HDD of laptop?. Thanks in advance
.[ATTACH=CONFIG]246247[/ATTACH]

---

### Post by kurrent93 on 2013-12-12
> **alienmindtrick said:**
> After spending 7 hours in the #Ubuntu channel on IRC to no avail and having to reinstall Ubuntu twice, I finally figured this out.

I'm willing to wager that you encrypted your drive when you installed Ubuntu. Yes or no? I did this both times, and both times I got the error /dev/mapper/cryptswap1, which the leets in the IRC channel repeatedly told me was a failed hard drive. They were wrong, all of them. It's a known error. Ubuntu DOES NOT LIKE TO BE ENCRYPTED!

Yes, I will run into the same issue again and I will have to reinstall Ubuntu again (since I didn't find this problem until after I had reinstalled 12.10), but I plan to do that prior to upgrade to 13.04 Raring.

If you get the error initramfs, you'll probably find that it's the same cause - an encrypted hard drive. Why this isn't notated with a warning on the installation screen is troubling.

Hi, I am having the same problem, and my drive is encrypted.

Do you find a way to rescue your drive and data?

---

### Post by kurrent93 on 2013-12-12
I managed to fix this problem using these:
[LIST]
[*][http://askubuntu.com/questions/8566/errors-when-performing-fsck-on-encrypted-partition-in-recovery-mode](http://askubuntu.com/questions/8566/errors-when-performing-fsck-on-encrypted-partition-in-recovery-mode)
[*][http://pissedoffadmins.com/os/mount-unknown-filesystem-type-lvm2_member.html](http://pissedoffadmins.com/os/mount-unknown-filesystem-type-lvm2_member.html)
[/LIST]

---

### Post by psipika on 2013-12-12
> **kurrent93 said:**
> I managed to fix this problem using these:
[LIST]
[*][http://askubuntu.com/questions/8566/errors-when-performing-fsck-on-encrypted-partition-in-recovery-mode](http://askubuntu.com/questions/8566/errors-when-performing-fsck-on-encrypted-partition-in-recovery-mode) 
[*][http://pissedoffadmins.com/os/mount-unknown-filesystem-type-lvm2_member.html](http://pissedoffadmins.com/os/mount-unknown-filesystem-type-lvm2_member.html) 
[/LIST]


Thanks for those.
Now all I need is a way to get grub to do that on boot, since it can't find the root LV without having first decrypted the drive...

---

