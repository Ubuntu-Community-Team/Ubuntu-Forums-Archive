---
title: "Gutsy: How to activate Proprietary Nvidia Module with custom compiled kernel."
date: 2007-10-18
forum: General Help
---

### Post by garymansell on 2007-10-18
Hi,

I have installed Gutsy and had it working with Nvidia proprietary module configured by the restricted drivers tool.

I have a Dell D630 and unfortunately the sound did not work so I compiled a custom kernel (2.6.23.1) and installed it using dpkg.

I have rebooted into the new kernel sucessfully and the sound is now working but unfortunately the Nvidia driver is not working anymore.

I went to the restricted modules tool to install it for the new kernel but when I fire up the tool its says that I need to install linux-restricted-modules-2.6.23.1.

Now I guess that this package does not exist so please can someone advise me how to get my Nvidia proprietary drivers compiled and working again with my new  custom kernel.

Thanks in advance

Gary

---

### Post by nappleapple on 2007-10-18
[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

I did that this morning, hoping to fix one of my problems.  It worked and installed NVIDIA proprietary drivers on my new custom kernel, but didn't fix my problem.  Try it out.

---

### Post by chillman88 on 2007-10-20
Hey Gary, I was curious if you remember what problem the driver gave you when you tried to load X? i had a problem where it said that the the installer failed for the kernel module when i ran modprobe? That confused me, because the nVidia compiler/installer program didn't puke an error at me! :confused:

---

### Post by worc on 2007-10-20
> **chillman88 said:**
> Hey Gary, I was curious if you remember what problem the driver gave you when you tried to load X? i had a problem where it said that the the installer failed for the kernel module when i ran modprobe? That confused me, because the nVidia compiler/installer program didn't puke an error at me! :confused:

Exactly the same issue here.
I followed [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) to remove nvidia driver come with restrict-modules and delete /lib/linux-restricted-modules/.nvidia_new_installed, then modprobe ran with no error. BUT, I still can not get X running on nvidia driver, when I "sudo /etc/init.d/gdm start", the screen  flicks for 3 times then lead to a "low graphic mode" dialog. I can enter X with the "low graphic" mode, but how can I get the nvidia driver work?

---

