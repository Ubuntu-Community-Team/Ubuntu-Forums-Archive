---
title: "The Disk Drive for / is not ready yet or not present"
date: 2017-07-17
forum: General Help
---

### Post by luisrafaelbarbosa on 2017-07-17
Good Day friends....

I have this ubuntu: DISTRIB_RELEASE=10.04. DISTRIB_CODENAME=lucid.DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS". And after an update, this messages appear: The Disk Drive for / is not ready yet or not present. S to skip mount or M for manual recover and The Disk Drive for /tmp is not ready yet or not present. S to skip mount or M for manual recovery

[IMG]https://imageshack.com/i/pmanDBMcj[/IMG]
 
I've already read here in forums but the methods don&#8217;t work. To use this host, I need to tap S, to skip, and mount / manually every time.

my fstab:
```
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=  fcaeade4-b03e-442f-bf12-c9184c186b49    /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=  5b7316be-bf18-4160-9f0b-cdfad34a2f1d  none swap sw  0 0
```


Someone can helps me?

---

### Post by Autodave on 2017-07-17
How and when did you get an update for that? 10.4 reached its end of life 2 years ago, I believe.  I'm thinking that you need to install the newest long term release: 16.04. Depending on the specs of your machine, you may want to go for a lighter desktop such as Xubuntu.

---

### Post by luisrafaelbarbosa on 2017-07-17
> **Autodave said:**
> How and when did you get an update for that? 10.4 reached its end of life 2 years ago, I believe.  I'm thinking that you need to install the newest long term release: 16.04. Depending on the specs of your machine, you may want to go for a lighter desktop such as Xubuntu.

This is a old apache server on a business, that runs Joomla, so I can't develop another site now... I'd like to solve this problem first

---

