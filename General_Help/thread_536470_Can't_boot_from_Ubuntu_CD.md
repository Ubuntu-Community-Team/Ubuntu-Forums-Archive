---
title: "Can't boot from Ubuntu CD"
date: 2007-08-27
forum: General Help
---

### Post by zajacattack on 2007-08-27
Hello, I just received my Ubuntu 7.04 CD. I tried to boot from it. I selected "Start or Install Ubuntu" at the boot menu. Then, the Ubuntu logo with a progress bar showed up for thirty seconds or so. Then, I started getting error messages. Every few minutes or so a new one would pop up. It would say:

Buffer I/O error in device hdc, logical block 0
hdc: device is not ready for command

Then, after a few minutes

Buffer I/O error in device hdc, logical block 1
hdc: device is not ready for command

Every few minutes a new error message comes up with the logical block being incremented by one. So, as you can see, my boot fails. I am running a PC with a Pentium 4 1.8 Ghz processor, 256 MB of RAM, and am booting from a CD-RW drive. Can someone help me?

---

### Post by jonathanmotes on 2007-08-27
You can try downloading the alternate disc from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and burning it - just check the box below the download button to get the alternate disc. It usually works when the live disc doesn't. I have seen this error before but have gotten the alternate disc to work. I think there are ways to work around this problem and get the live disc to work, you might be able to find out how by googling your problem.

---

### Post by zajacattack on 2007-08-27
OK, just a few questions:

1. If I use the alternate desktop download, can I still just try out Ubuntu and not install it?

2. What do the error messages mean? I googled it, and I think it's trying to mount my hard disk, but I'm not sure.

3. If it is trying to mount the hard disk, is there a boot option I can use to disable this? Something like, "boot: live [option]"

---

### Post by jonathanmotes on 2007-09-11
> **zajacattack said:**
> OK, just a few questions:

1. If I use the alternate desktop download, can I still just try out Ubuntu and not install it?

2. What do the error messages mean? I googled it, and I think it's trying to mount my hard disk, but I'm not sure.

3. If it is trying to mount the hard disk, is there a boot option I can use to disable this? Something like, "boot: live [option]"

Sorry, I didn't notice you had responded. No, if you use the alternate disc, you have to install it first -- that is the real difference in the live and alternate discs. It allows you to install ubuntu when your computer won't allow live booting (for some reason or another).

I don't know the answers to your other questions. I think I have seen tutorials on this forum on how to get past your errors though. Sorry!

---

