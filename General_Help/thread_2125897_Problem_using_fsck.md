---
title: "Problem using fsck"
date: 2013-03-15
forum: General Help
---

### Post by rdh61 on 2013-03-15
Hi,

I am running Ubuntu 12.04.

I want to check and if necessary repair my file system. I gather I can use fsck to do this. Many of the instructions I have seen to do this begin with running the following command as root, to "take the system down to run level one" (whatever that means):

```
# init 1
```

When I do this, I get a purple screen with the Ubuntu logo and the white/red dots. To begin with the latter turn over, then they freeze and nothing else happens. At that point I have to restart my computer.

Can someone advise?

Many thanks.

---

### Post by dargaud on 2013-03-15
You must unmout the filesystem in order to check it and you cannot unmount a live filesystem, even in init 1. [Solution here]("http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/").

---

### Post by rdh61 on 2013-03-15
Thanks. How do I view the outcome of the check?

---

### Post by dargaud on 2013-03-15
I... don't know. It may end up in some logfile somewhere but I don't know. If you want to see that, another solution is to use a liveCD (Ubuntu or Knoppix or any Linux), boot with it, then DON'T mount your drive, do "fdisk -l /dev/sda" to verify that it's the proper disk, then "fsck /dev/sda1". You probably need sudo in front of those two commands. Then reboot.

---

### Post by sudodus on 2013-03-15
> **dargaud said:**
> I... don't know. It may end up in some logfile somewhere but I don't know. If you want to see that, another solution is to use a liveCD (Ubuntu or Knoppix or any Linux), boot with it, then DON'T mount your drive, do "fdisk -l /dev/sda" to verify that it's the proper disk, then "fsck /dev/sda1". You probably need sudo in front of those two commands. Then reboot.
+1

This is for linux ext2, ext3 and ext4 file systems. Make sure the drive is not mounted, run
```
sudo e2fsck -f /dev/sdxy
```
where x is the drive letter and y is the partition number. -f means force a check, even if the first scan reveals no errors. You will get output to the terminal window, and in some cases a prompt to accept or deny a repair action.

If it is a FAT or NTFS file system, it is best to check it from Windows using ```
chkdsk /f X:
``` where X: is the volume letter.

---

### Post by rdh61 on 2013-03-19
Thanks.

---

