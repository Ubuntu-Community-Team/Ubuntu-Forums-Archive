---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2018-12-17
forum: General Help
---

### Post by hamiltzp on 2018-12-17
Hello,

Noob here, so I apologize if this has been answered before, but I couldn't find anything that quite seemed to fit my situation.

I'm the SysAdmin in a VMware environment.  Most of the VMs are Windows, but I have a handful of Linux of various flavors.  One machine is Ubuntu 16.04 (no GUI) that ran out of disk space.  I'm not real strong on Linux, but I fought through and expanded the disk and partition.  Unfortunately the errors I was seeing when I try to do updates didn't go away, so I'm thinking they are related to the previous running out of disk space.  Here's what I'm seeing if I try to run "sudo apt-get upgrade" or "sudo apt-get install -f":

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-140-generic_4.4.0-140.166_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-128-generic_4.4.0-128.154_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-131-generic_4.4.0-131.157_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-138-generic_4.4.0-138.164_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-139-generic_4.4.0-140.165_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help and teaching is greatly appreciated.

Thanks,

Zack

---

### Post by Impavidus on 2018-12-17
That's just the last part of the error message. The beginning is far more interesting.

Let's see the full error message:```
sudo apt install -f
```
Next verify the partition is now indeed large enough:```
df -h
```
The currently running kernel:```
uname -r
```
The contents of /boot:```
ls -l /boot
```
And the list of currently (partially) installed kernels:```
dpkg --list linux-\*
```After all, it appears something went wrong during installation of a kernel.

That should tell us what's going on. Then we can make a plan to fix this.

---

### Post by hamiltzp on 2018-12-18
Just to update on this: I seem to have gotten things to work by playing around with "sudo apt autoremove" and "sudo apt-get dist-upgrade".  I may have used the -f switch when I ran that, but I can't recall.

Thanks,

Zack

---

### Post by Impavidus on 2018-12-19
autoremove may have solved your problem. If you're satisfied, could you mark this thread as solved? Else, to be completely sure, run the commands in my previous post (except the first) and post the output. Then we can see if any more cleanup is needed.

---

