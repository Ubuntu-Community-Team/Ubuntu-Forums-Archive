---
title: "Cannot boot into Ubuntu Partition"
date: 2007-12-02
forum: General Help
---

### Post by isaaclimdc on 2007-12-02
Hi all,

My ubuntu partition has been working okay until recently, when it started freezing up for no reason: I can still move my cursor but can't click on anything. I would always have to force shut down. However, the problem I have now is when I forced-shutdown it today, it refused to boot with the attached check disk error (pic attached). Can anyone help please? It's my school computer and I can't afford to muck this up.

All help appreciated,
Isaac.

---

### Post by rzrgenesys187 on 2007-12-02
pic?

---

### Post by TidusBlade on 2007-12-02
Since it is a school computer, I would recommend you reinstall Ubuntu, further troubleshooting could ruin the system even more :( 
If you got anything valueble on the ubuntu partition, I would then suggest you use some program like Acronis, to backup the whole partition to another partition, or find a way to read ext3 partition from another OS, assuming you dual boot Windows? Acronis can also backup a partition to an external drive ;)

---

### Post by isaaclimdc on 2007-12-02
Sorry I just attached the pic. I read on one of the threads that I can boot from the live CD into terminal and do a "sudo fsck /dev/sda2"

Will that help? I havn't tried because I need to borrow the USB CD drive in order to do that. The HP tablet im using does not have a built-in CD drive.

---

### Post by PmDematagoda on 2007-12-02
Would you please give the specific error that concerns the root filesystem? Unfortunately I cannot gather what is wrong with it and what is going on when I look at the picture.

---

### Post by isaaclimdc on 2007-12-02
After a force shut down, I tried booting back into ubuntu, and it will always do a check for any errors on the disk as a result of the force shut down. The following is the output:

```
/dev/sda2:
Unattached inode 1507898

/dev/sda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
fsck died with exit status 4

* An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
* The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@ubuntu-pc:~#
```

Does this info help? How can I perform a manual fsck?

---

### Post by isaaclimdc on 2007-12-02
Ok I solved the problem by running a "fsck" in that command line interface. Thanks to anyone who tried to help! I appreciate it.

---

