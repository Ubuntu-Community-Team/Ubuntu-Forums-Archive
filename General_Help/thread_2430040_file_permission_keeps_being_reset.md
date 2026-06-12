---
title: "file permission keeps being reset?"
date: 2019-10-26
forum: General Help
---

### Post by croyle on 2019-10-26
hi everyone,
I am having a small but annoying issue I am running a modified 18.04LTS distro and use the 'light' package to control the backlight on my laptop.  The 'light' command writes to the /sys/class/backlight/amdgpu_bl0/brightness files to control the backlight and everytime I logout or reboot the /sys/class/backlight/amdgpu_bl0/brightness has its permission, ownership and group reset to -rw-r--r-- 1 root root 4096 Oct 26 17:58 brightness  Is there a way to stop this or flag the file so I can see what is accessing the file and changing it?  Any help would be greatly appreciated.
Thank you,
Jason

---

### Post by uRock on 2019-10-26
Changing the permissions of a file in the root file system could cause problems. I do not recommend doing that.

---

### Post by TheFu on 2019-10-26
> **croyle said:**
> hi everyone,
I am having a small but annoying issue I am running a modified 18.04LTS distro and use the 'light' package to control the backlight on my laptop.  The 'light' command writes to the /sys/class/backlight/amdgpu_bl0/brightness files to control the backlight and everytime I logout or reboot the /sys/class/backlight/amdgpu_bl0/brightness has its permission, ownership and group reset to -rw-r--r-- 1 root root 4096 Oct 26 17:58 brightness  Is there a way to stop this or flag the file so I can see what is accessing the file and changing it?  Any help would be greatly appreciated.
Thank you,
Jason

/sys/ isn't a real file system. It is a pseudo-file system provided as a way for root to directly modify settings on a running system.  If you look at the storage when booting from alternate media, you'll not see any /sys/ or /proc/ on the storage.

If you want to use some program to directly modify the values in files under /sys/, then those processes will need to run with root elevated permissions.  The best practice for creating tools which can do this uses a C program which is carefully created with security as the primary consideration.  A poorly designed and poorly coded tools can be abused to provide a back door into the system.  We can go deeper into this, if you like.  It has been a few decades since I wrote a setuid-root program to do something like this, but is was definitely non-trivial to ensure all the holes were closed.  A quality Unix Systems Programming book should have a chapter about this.

---

### Post by croyle on 2019-10-26
Ok I think I am getting somewhere i understand the that the /sys/ files are pseudo file kinda like a symbolic link if my understanding is correct.  I assume that’s why those files reset each time I reboot because there being remade on each boot.  That link goes to /pcie00.00.01.0/?????/?????/amdgpu_bl0/brightness I forget exactly don’t have it in front of me but I know the exact location.  But all those files are root:root also is there any issue changing those or adding other privileges to those? I’ll try it when I get home I can then pass the path to ‘light’ when it’s executed.  This may just work but is it correct way to do it?

---

### Post by TheFu on 2019-10-26
Hate to say this, but a pseudo-file system is fake.  It is provided only while the system runs and show current internal state of the running system.  Nothing is saved between reboots and not even between process stop and starts.

A symbolic link is a real file system object.  Nothing fake about it.  Same for hard links.  Those are real.

Perhaps this will help: [https://en.wikipedia.org/wiki/Everything_is_a_file](https://en.wikipedia.org/wiki/Everything_is_a_file)
It is one of the defining differences between Unix-like systems and Windows.

---

### Post by Skaperen on 2019-10-26
the approximate truth is that each "file" in /proc/ or /sys/ is a way to access some variable inside the kernel.  more precisely it is handled by some function in the kernel.  it may then be passed down to a device driver or kernel module.

there are frequent valid reasons to change these.  changes that need to exist from when the system starts up need to be changed when the system starts up such as with a system initialization script or in a script that starts a program that needs the change (usually for a long running daemon).  don't change them unless you have a good reason to do so.

file systems that have a storage based backing store generally store things there.  some file system types do some unusual things like compression and/or encryption (uncompression and decryption when reading).  think of /proc/ and /sys/ as having a "backing store" of logic inside the kernel (which is generally initialized by the kernel before it is mounted).  the really fun one is tmpfs.  tmpfs has no backing store.  it exists by trickery inside the kernel.  it's buffered but just not saved in any backing store.  the buffers are in RAM or can be swapped out, as needed.  it does not exist when the system is not running.

---

### Post by croyle on 2019-10-26
thanks guys learning that the /sys/class/????? is however we like to say pseudo or temporary was the key.  I made a custom udev rule and that seems to be working i just ACTION=="add", SUBSYSTEM=="backlight", RUN+="/bin/chmod g+w /sys/class/backlight/amdgpu_bl0/brightness i am assuming this is safe sense i am only giving write permission to the one file

---

