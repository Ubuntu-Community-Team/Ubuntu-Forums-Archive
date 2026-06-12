---
title: "Stop Xubuntu 19.01 eoan from doing FSCK checks"
date: 2019-11-24
forum: General Help
---

### Post by skybird182 on 2019-11-24
Hello
I am a new Xubuntu user with some limited previous Linux experience. A few days ago when restarting my system, the boot up process starting doing file checks. This did not happen initially after the install. When I press CTRL + C the checks continue for about 3 minutes.
After the checks are complete, then the system finishes a normal boot-up. I understand that some FSCK checks are necessary from time to time.  However, each time the system reboots the checks are annoying as I am trouble shooting a UPS issue. The SSD drive containing the install is a
new drive and not indicating any prior problems. I did read on another site to use shutdown -rf. When I viewed the Xubuntu man page -f is not an option so when the system restarted the file checks reoccurred. 

Thanks

---

### Post by CatKiller on 2019-11-24
If the check is needing to be started often, and is taking 3 minutes for an SSD, that sounds like there's actually some kind of issue with the filesystem. fsck on my SSDs, where nothing needs to be fixed, takes between 10 and 30 seconds. More fsck, rather than less, would be my recommendation; running a manual fsck and looking at the SMART results.

---

### Post by skybird182 on 2019-11-24
Thanks for replying. As I am new to this would appreciate some more help if you can. Should I boot from a USB drive and then run FSCK against the file system on the Linux drive?

It seems to be only running fsck but not fixing anything. This is puzzling.

Thanks

---

### Post by Bashing-om on 2019-11-24
skybird182; Hello - Welcome to the forum :)

Yeah - often times that preliminary boot file system check can not resolve the issue, and one is prompted to conduct the manual fsck.

We next need to know the partition to point fsck to,
Post back - between code tags - the outputs of terminal commands:
```

sudo parted -l
sudo fdisk -lu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we can further advise on the use of fsck.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by CatKiller on 2019-11-24
Yep, that's the idea; you can't check it while it's mounted so it either needs to be done before the drive is mounted or from a live environment.

It'll be fsck /dev/sd... something or fsck /dev/nvme... something, depending on whether it's an NVMe drive or not, and on how many drives and partitions you have in there. You can use Tab-completion to help you. I can't remember whether you need to be root or not, so try it without sudo and, if that says you're not allowed, try it with. /dev/sda2 is a fairly standard partition name, as an example.

Hopefully someone will be along to clarify reading the SMART information from the drive. I can't remember whether you need to install smartmontools to read it, nor whether that's on the install image already. Modern drives keep track of whether they've had to correct errors, how long they've been running, and so on; that's what SMART displays.

You should have your Internet connection and browser and stuff in the live environment, so you should be able to look things up or copy-and-paste the output here for people to take a look at.

---

