---
title: "How to update a file in current kernel for 18.04 (5.0.0-37), compile &amp; install it?"
date: 2019-12-03
forum: General Help
---

### Post by agmaragos on 2019-12-03
Hello all...

I am looking for information on how to update a line of code in the kernel my current system is running (5.0.0-37-generic), compile and install it.
There seems to be an issue with the Trim function not working properly under Linux with the newest Ryzen platforms when utilizing the new gen 4 nvme ssd drives. A work-around/fix for this issue was identified at Kernel.org - Bugzilla ([https://bugzilla.kernel.org/show_bug.cgi?id=202665](https://bugzilla.kernel.org/show_bug.cgi?id=202665)) where one must update a line of code at 'drivers/nvme/host/core.c' 

I've come across an article that discuss the process for building your own kernel:
[LIST]
[*][https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)
[/LIST]

Reading this article, I'm able to install the required packages and use Git to clone the Bionic repo. (git clone git://kernel.ubuntu.com/ubuntu/ubuntu-bionic.git)
From there, I can find the file that needs to be updated (from the bugzilla.kernel.org link above) and I subsequently make the update.  

I then run the following commands, as outline in the article:
```
fakeroot debian/rules clean
fakeroot debian/rules binary-headers binary-generic binary-perarch
fakeroot debian/rules binaryWhen that process is complete, when I go up one directory I see the three files that the article makes reference to:
linux-headers-4.15.0-70_4.15.0-70.79_all.deb
linux-headers-4.15.0-70-generic_4.15.0-70.79_amd64.deb
linux-image-unsigned-4.15.0-70-generic_4.15.0-70.79_amd64.deb
```


So it almost looks like this process works.  Unfortunately, it looks like the .deb files that were created are based on an earlier (original?) kernel version that shipped with 18.04 (4.15.0-70_4.15.0-70.79). (And not the kernel I currently have installed, 5.0.0-37-generic)  I am guessing that the bionic repo I'm cloning  isn't of the latest 5.0x kernel that 18.04 is currently updated with.

So I have two questions...

[LIST=1]
[*]How can I update the impacted file of the kernel version my system is currently on (5.0.0-37-generic), compile it...and then subsequently install it?
[*]I'm under the assumption that the process I described above, where I update the 'drivers/nvme/host/core.c' file per the buzilla.kernel link above and run the commands 
```
fakeroot debian/rules clean
fakeroot debian/rules binary-headers binary-generic binary-perarch
fakeroot debian/rules binary
```
...will produce a Linux kernel package set that contains an updated 'drivers/nvme/host/core.c' file, and that Linux kernel can than be installed on my machine via the sudo dpkg -i ...command?  Am I right in thinking this?
[/LIST]

I'm not a Linux expert but I'm not completely unfamiliar with Linux...though I've never had to bother with compiling a Kernel to resolve an issue like this.
Any assistance would be greatly appreciated.  Thank you for reading through this lengthy post.

---

