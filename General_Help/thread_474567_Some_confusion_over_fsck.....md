---
title: "Some confusion over fsck...."
date: 2007-06-15
forum: General Help
---

### Post by Midahed on 2007-06-15
Hi,

Hopefully someone can put me right on a couple of queries I have about fsck...

I'd had a couple of lock-ups (Ubuntu 7.04 Feisty 64-bit) and decided to run fsck manually.  I know that it can only be safely run on a mounted filesystem if the -n switch is used.  However when I did this it reported a couple of errors - the free block and inode counts were wrong.

However, if I ran fsck from a live CD on the unmounted filesystem, it was reported as clean.

Presumably this means that fsck, even run with the -n switch, on a mounted filesystem gives bogus errors?  Is that right?

My second question is about forcing fsck to run on reboot.  I've seen several posts on the Ubuntu forums that say that **sudo shutdown -rF now** forces fsck to run during the boot process before the filesystem is mounted.  I tried this and the system shutdown and rebooted OK, but there was no evidence that it ran fsck at any time.  The boot time was just the same as it normally is, and there were no messages from fsck.

I had a look at the man pages for shutdown and there is no reference to a -F switch (which is, presumably, what tells the system to run fsck on restart).  I'm confused....

Lastly, I don't like using the live CD to run fsck because it's so slow to load, yet it seems to be the most commonly recommended way to run fsck.  I eventually found that I could switch to single-user mode, manually unmount the filesystem and then run fsck...

[b]sudo su root
password
shutdown now[/b]
...wait for system to go to single user mode...
[b]unmount /dev/hda2
fsck -nfv /dev/hda2[/b]   (I used the -n switch because I believed there were no errors to correct)

It seemed to run OK and didn't report any errors.  Specifically, the unmatching free blocks and inodes problem that I'd seen when running it on the filesystem while it was mounted had gone.

Once it had finished I just ran **shutdown -r now** to reboot the system .

Are there any reasons why it's better to boot from the live CD rather than using single-user mode?

Thanks,

Mike

---

