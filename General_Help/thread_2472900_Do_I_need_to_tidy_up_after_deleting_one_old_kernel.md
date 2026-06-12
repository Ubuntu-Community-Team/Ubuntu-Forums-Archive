---
title: "Do I need to tidy up after deleting one old kernel pls?"
date: 2022-03-16
forum: General Help
---

### Post by andrew-q2 on 2022-03-16
hi, on Ubuntu 20.04, I tried to delete the oldest kernel rather than use autoremove, so that I would have more than one kernel available in case of problems.
Before I did this I had these -

```
dpkg --list | egrep -i --color 'linux-image|linux-headers'
ii  linux-headers-5.13.0-28-generic            5.13.0-28.31~20.04.1                amd64        Linux kernel headers for version 5.13.0 on 64 bit x86 SMP
ii  linux-headers-5.13.0-30-generic            5.13.0-30.33~20.04.1                amd64        Linux kernel headers for version 5.13.0 on 64 bit x86 SMP
ii  linux-headers-5.13.0-35-generic            5.13.0-35.40~20.04.1                amd64        Linux kernel headers for version 5.13.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-20.04            5.13.0.35.40~20.04.20               amd64        Generic Linux kernel headers
ii  linux-image-5.13.0-28-generic              5.13.0-28.31~20.04.1                amd64        Signed kernel image generic
ii  linux-image-5.13.0-30-generic              5.13.0-30.33~20.04.1                amd64        Signed kernel image generic
ii  linux-image-5.13.0-35-generic              5.13.0-35.40~20.04.1                amd64        Signed kernel image generic
rc  linux-image-5.8.0-43-generic               5.8.0-43.49~20.04.1                 amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04              5.13.0.35.40~20.04.20               amd64        Generic Linux kernel image
```

I did -
```
sudo apt-get --purge remove linux-image-5.13.0-28-generic
```

It seemed to work ok until the last line said -
```
rmdir: failed to remove '/lib/modules/5.13.0-28-generic': Directory not empty
```

and it is indeed not empty.
Now the dpkg command gives this -

```
ii  linux-headers-5.13.0-28-generic            5.13.0-28.31~20.04.1                amd64        Linux kernel headers for version 5.13.0 on 64 bit x86 SMP
ii  linux-headers-5.13.0-30-generic            5.13.0-30.33~20.04.1                amd64        Linux kernel headers for version 5.13.0 on 64 bit x86 SMP
ii  linux-headers-5.13.0-35-generic            5.13.0-35.40~20.04.1                amd64        Linux kernel headers for version 5.13.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-20.04            5.13.0.35.40~20.04.20               amd64        Generic Linux kernel headers
ii  linux-image-5.13.0-30-generic              5.13.0-30.33~20.04.1                amd64        Signed kernel image generic
ii  linux-image-5.13.0-35-generic              5.13.0-35.40~20.04.1                amd64        Signed kernel image generic
rc  linux-image-5.8.0-43-generic               5.8.0-43.49~20.04.1                 amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04              5.13.0.35.40~20.04.20               amd64        Generic Linux kernel image
```

so it seems kernel 28 is half-deleted.

Should I manually try to delete the remaining folder?  Will just leaving it as is cause any issues in future?  What do you suggest please?  I am not an experienced user and have only a fairly superficial understanding of these things, so pls don't be too technical!  Thanks

---

### Post by TheFu on 2022-03-16
Kernels have 3 different packages, image, modules, headers.

Delete all three (use apt or synaptic) or let autoremove handle it.  Autoremove doesn't always work, so it might need help.
NEVER manually remove a directory that has package files inside it if the package files are still showing as installed inside APT.

In general, package manipulation via dpkg shouldn't be done. Using dpkg to get information is fine, just don't install or remove packages with it.

IMHO.

---

### Post by ActionParsnip on 2022-03-16
You may want to run:
```

sudo dpkg P linux-image-5.8.0-43-generic

```

To tidy up

---

### Post by Impavidus on 2022-03-16
My guess is you still have the linux-modules-5.13.0-28-generic and linux-modules-extra-5.13.0-28-generic packages installed. Remove those too. Normally autoremove works fine though.

---

### Post by andrew-q2 on 2022-03-16
TheFu, thanks.  What do you mean pls by "delete all three" using apt?  I was hoping the "purge" command I did would do that!

---

### Post by andrew-q2 on 2022-03-16
ActionParsnip, thanks (though see what TheFu says about not using dpkg ?!)

---

### Post by andrew-q2 on 2022-03-16
Impavidus, thanks.  Just to be clearer, it wasn't that I thought autoremove might go wrong, rather, I just thought it prudent to keep at least one previous kernel in case the current one proves to have a serious bug / problem.  When you say "remove these too" do you mean by autoremove?  If not, how pls?

---

### Post by #&amp;thj^% on 2022-03-16
> **andrew-q2 said:**
> ActionParsnip, thanks (though see what TheFu says about not using dpkg ?!)

Here; dpkg

While the previous tools were focused on managing packages maintained in repositories, the dpkg command can also be used to operate on individual .deb packages. **_The dpkg tool actually is responsible for most of the behind-the-scenes work of the commands above; apt provides additional housekeeping while dpkg interacts with the packages themselves._**

**Unlike** the apt commands, dpkg does not have the ability to resolve dependencies automatically. It&#8217;s main feature is the ability to work with .deb packages directly, and its ability to dissect a package and find out more about its structure. Although it can gather some information about the packages installed on the system, **you should not use it as a primary package manager. **

---

### Post by TheFu on 2022-03-16
> **andrew-q2 said:**
> TheFu, thanks.  What do you mean pls by "delete all three" using apt?  I was hoping the "purge" command I did would do that!

You purged 1 package for the kernel image. You didn't purge the related kernel headers and kernel module packages.  Post #1 above has them in the list with the exact names to purge. Use apt, just like you did to purge the kernel image package.  The version numbers in the package names map 1-for-1.

---

### Post by Impavidus on 2022-03-17
> **andrew-q2 said:**
> Impavidus, thanks.  Just to be clearer, it wasn't that I thought autoremove might go wrong, rather, I just thought it prudent to keep at least one previous kernel in case the current one proves to have a serious bug / problem.If you autoremove old kernels, one old kernel will be kept automatically, just in case the current one has a serious bug.> When you say "remove these too" do you mean by autoremove?  If not, how pls?You can remove them the same way as how you removed linux-image-5.13.0-28-generic. **apt autoremove** should work (you may want to add the --purge option), but you can use **apt purge linux-modules-**... instead if you prefer.

The only time when it's normal to run dpkg manually (if not for information) is when package management is already broken and apt can't fix it.

---

### Post by ajgreeny on 2022-03-17
Whenever a new kernel version appears I always remove all packages of what will then be the oldest kernel's version number.

I have an alias set to see what kernel versions I have which runs command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-82
``` which will show me output like this ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-82
:menuentry 'Xubuntu-20.04 GNU/Linux' --class xubuntu_20_04 --class gnu-linux --
184:	menuentry 'Xubuntu-20.04 GNU/Linux, with Linux 5.4.0-100-generic' --class xub
203:	menuentry 'Xubuntu-20.04 GNU/Linux, with Linux 5.4.0-100-generic (recovery mo
221:	menuentry 'Xubuntu-20.04 GNU/Linux, with Linux 5.4.0-99-generic' --class xubu
240:	menuentry 'Xubuntu-20.04 GNU/Linux, with Linux 5.4.0-99-generic (recovery mod

``` and I then run command ```
sudo apt purge *<version of unwanted oldest kernel>
```, eg ***sudo apt purge *5.4.0-99**** which purges anything related to that kernel in a single command, ie headers, modules, etc etc.

---

### Post by VMC on 2022-03-17
I do this after new kernel installed **&** a reboot:
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-3]| xargs sudo apt-get -y purge --dry-run
```
Do the "dry-run" first, then if satisfied with results, remove "--dry-run". I've been doing it this way for years without fail.

---

### Post by andrew-q2 on 2022-04-28
Belated thanks, sorry so late, tidying complete!

---

### Post by VMC on 2022-04-28
If satisfied, please mark the topic as solved.

---

