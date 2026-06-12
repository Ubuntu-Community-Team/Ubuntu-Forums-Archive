---
title: "Is it ok to remove &quot;Volumes&quot; : &quot;Loop Devices&quot; after removing/purging snapd?"
date: 2023-06-22
forum: General Help
---

### Post by ozark_hillbilly on 2023-06-22
Hello,

After removing/purging snapd I have found these "Volumes" / "Loop Devices" listed under the Disks utility.
One is nearly a half gigabyte in size and I want to cleanup anything leftover from snapd that can free up disk space.

If it is ok to remove these then is it best to accomplish this with a terminal mode command or through Nautilus?

thanks....

[I am running 20.04 LTS]


solved: reboot cleared out loop devices.

---

### Post by #&amp;thj^% on 2023-06-22
How did you remove snap and snapd, from your pics it don't look like you followed anything good for your removal.
If you just started deleting things like /var/snap then stop there, but we will need your recipe to remove snap snapd.

---

### Post by Holger_Gehrke on 2023-06-23
I notice that they all have '(deleted)' as the last part of the backing storage. A file that is open when it is deleted stays accessible to the program - in this case probably the loopback driver of the kernel - using it , the used blocks are only freed after the program that uses the file is closed. You could either unmount them manually or reboot.

Holger

---

### Post by ozark_hillbilly on 2023-06-23
"we will need your recipe to remove snap sna

1st command: sudo apt autoremove --purge snapd

2nd command: sudo apt-mark hold snapd

3rd command: sudo rm -rf /var/cache/snapd/

I only had the snap-store installed, nothing else.

---

### Post by ozark_hillbilly on 2023-06-23
deleted

---

### Post by ozark_hillbilly on 2023-06-23
Thank you. A reboot cleared all those "deleted" loop devices. =d>

---

