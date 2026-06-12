---
title: "Different kernels with 12.04.3 LTS"
date: 2014-01-08
forum: General Help
---

### Post by jlh68 on 2014-01-08
I have two computers that are using Linux 3.2.0-58-generic (x86_64), and a third computer that is using Linux 3.5.0-45-generic (x86_64).  why are they different and why don't they all upfrade to the most recent kernel?

---

### Post by efflandt on 2014-01-08
The mainstream 12.04 kernel is 3.2.0-58, so if you have a 3.5.0 kernel on one system you must have done something different on that system to install that version.

---

### Post by Dave_L on 2014-01-08
It depends on when you installed 12.04. There are several kernel series available for 12.04: 3.2.x, 3.5.x, 3.8.x and 3.11.x.

The original 12.04 used kernel 3.2.x. At some point (12.04.1 or 12.04.2) it was upgraded to 3.5.x.

I'm using kernel 3.11.0-15 on 12.04.3. I specifically upgraded to that kernel.

---

### Post by deadflowr on 2014-01-08
12.04 was the original release and it contained the 3.2 series kernel.
Then they have what are known as point releases.
Each point release has an upgraded kernel series and updated graphics stack.
12.04 = original kernel and x stack
12.04.1 = I forget, but think it was the same with bug fixes.
12.04.2 = quantal kernel and x stack
12.04.3 = raring kernel and x stack
12.04.4 = will have the saucy kernel and x stack.
[More]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule")

The download page at ubuntu.com always reflects the latest point release for LTS.
Finding the old point releases and the original release is a  pain, but here
[http://old-releases.ubuntu.com/releases/12.04.2/](http://old-releases.ubuntu.com/releases/12.04.2/)
if you scroll down the page you'll get a list of downloadable files,
the old release are iso files, typically i386,amd64 and will have the desktop name.
example would be ubuntu-12.04-desktop-amd64.iso.
You can note when the file was uploaded and the size, which will be several hundred MBs.

Added, prior to the point release, the newer kernel and x stack are made available, to those who would wish to trend those waters, in the repos.
As the saucy kernel is for precise right now.

---

### Post by efflandt on 2014-01-09
Strange, I installed 12.04.3 after replacing a failing hard drive, but it has a 3.2 kernel```
efflandt@xps8100-1204:~$ cat /etc/os-release
NAME="Ubuntu"
VERSION="12.04.3 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.3 LTS)"
VERSION_ID="12.04"

efflandt@xps8100-1204:~$ uname -a
Linux xps8100-1204 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by mastablasta on 2014-01-09
strange indeed: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by carl4926 on 2014-01-09
Might it depend how the OP is doing updates?

---

### Post by deadflowr on 2014-01-09
> **efflandt said:**
> Strange, I installed 12.04.3 after replacing a failing hard drive, but it has a 3.2 [/code]

Not that strange, unless the disk is a minty fresh download.
I'm on 12.04.3 as well, and the kernel is 3.2.0-58 something something, but the install disk was 12.04.
Which ever point release or release point version you installed from, the kernel will stay that version, unless you opt in for the newer kernel/x stack versions.
As stated in the LTSEnablement wiki mastablasta posted.

---

### Post by efflandt on 2014-01-09
Maybe I grabbed the wrong iso (12.04 instead of 12.04.3) for Startup Disk Creator, since /etc/os-release for a backup system on SSD upgraded from 11.10 also shows it as: VERSION="12.04.3 LTS, Precise Pangolin"

So apparently **os-release** shows the current updated state (more or less) rather than when that version was installed. The computer is from 2010 anyway, so nothing it needs from a really new kernel.

---

### Post by jlh68 on 2014-01-09
Thanks everyone.  I see what happened, I installed 12.04 on my Laptop and my desktop with 3.2.x kernel in 2012, and I installed a newer download of 12.04 to the laptop this September, which has the 3.5 kernel..   That would account for the kernel version differences.  I guess some time in April or May I will probably be upgrading all three to Ubuntu 14.04LTS.  

What is involved in upgrading the kernnel whilekeeping the same Ubuntu version?

---

### Post by Dave_L on 2014-01-09
To upgrade to the latest kernel (3.11.x), install the metapackage linux-generic-lts-saucy. For the 3.8.* kernel, install linux-generic-lts-raring. Etc.

Kernels already installed won't be affected, so you can always revert to using them if the new one causes problems.

---

