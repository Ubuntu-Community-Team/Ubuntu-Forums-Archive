---
title: "Unususal error message"
date: 2015-02-10
forum: General Help
---

### Post by Otto-C on 2015-02-10
Dell Inspiron B130.  Ubuntu 12.04.5 up to date.

At boot get the below message:

Disk drive for /tmp not ready or present.

Continue to wait or Press S to Skip mounting or M for manual recovery.

Have used the waiting option for some time. Using machine now.

tia

---

### Post by kpatz on 2015-02-10
What's in your /etc/fstab?

---

### Post by Otto-C on 2015-02-11
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=1a5c5fcd-eefa-4854-9b70-7bb2affb1e25 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b6d9b642-6b7f-4d12-abc0-346a4462bd65 none            swap    sw              0       0

hth
otto-c

---

### Post by plucky on 2015-02-12
Also output of ```
sudo blkid
```

Do the UUID's match for / and /swap partitions?

Good Luck

---

### Post by Otto-C on 2015-02-12
Just on way out door. Will setup laptop at noon when I get back.

thanks

---

### Post by Otto-C on 2015-02-12
Crazy day.
~$ sudo blkid
[sudo] password for: 
/dev/sda1: UUID="1a5c5fcd-eefa-4854-9b70-7bb2affb1e25" TYPE="ext4" 
/dev/sda5: UUID="b6d9b642-6b7f-4d12-abc0-346a4462bd65" TYPE="swap"

---

### Post by plucky on 2015-02-13
All looks ok with your partitions.

When you get the error message,do you press S to continue?

Have you tried choosing M for Manual Recovery?

Do you have a tmp directory under the / root directory?

Post output for ```
ls -l /
```

---

### Post by Otto-C on 2015-02-13
Do not use S option.
Not tried M option.
tmp is present using ls -l /

Reluctant to use S or M option not clear as to what they do.
Machine does boot thru after a few moments.

---

### Post by plucky on 2015-02-13
Can you post the output for the ```
ls -l /
``` command as I would like to see what the permissions are for the /tmp directory.

---

### Post by Otto-C on 2015-02-13
drwxrwxrwt   9 root root  4096 Feb 13 20:17 tmp

---

### Post by plucky on 2015-02-14
All looks ok.I am at a loss of what next to suggest.

Perhaps a GRUB problem.

You could try booting with "quiet and splash" disabled to see what is trying to mount the /tmp directory.

---

### Post by Otto-C on 2015-02-14
Thanks so much for your suggestions.  Will look into your booting idea in a few days.
Have no idea how to do as GRUB is not dispalyed at boot.

---

### Post by mc4man on 2015-02-14
see 
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1091792](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1091792)

---

### Post by Otto-C on 2015-02-14
Thanks all.

Will close this out with a solved.

---

