---
title: "Nvidia drivers gone after update"
date: 2013-02-19
forum: General Help
---

### Post by texpat on 2013-02-19
On this machine I run 12.04.2 LTS, 64-bit Xubuntu.

Weird thing happened when the system updated today. I do this en-passent, as it were, and today seemed another routine update. I revised the list of items - kernel image and related files, so I updated as usual. After reboot, however, the Nvidia drivers were gone. I tried installing the 'post-release updates' version but this failed, so I installed the '**experimental** beta-310' version which up to now works fine.

I'm good allright, but worry a bit about this whole 'beta' and 'experimental' bit. Has anyone else had this? Any idea why I can't download/install the 'post-release upgrades' version?

---

### Post by bogan on 2013-02-20
HI1, **texpat**,

If you are using a clean install of 12.04.2, not an update, with the 3.5 Quantal kernal, some programs are not compatible with the Xorg and linux -lts-quantal files.

I had exactly the same problem, except I tried to install the 'post-release updates' version of nvidia from Synaptic and - luckily -  it gave me a warning that lots of the 'lts-quantal' and 'backports' files would be un-installed.

So I used the nvidia.com Downloads to install 304.51 which I knew was reliable and stable with all my equipment.

Steam is also one of the programs affected.

Chao!, **bogan.**

---

### Post by texpat on 2013-02-20
Not sure about the "clean install". This computer has only ever had 12.04 LTS installed, but has received its updates regularly. Kernel version is 3.2.0-38-generic (as per [FONT="Courier New"]**uname -r**[/FONT]).

I'll give the drivers on the Nvidia site a shot, though.

Thanks for the info :-)

---

### Post by bogan on 2013-02-21
Hi!,** texpat**,

If it had been a 'clean install'of 12.04.2, and not an update, 'uname -r' would have returned: "3.5.0-24 xxx", as it does not, what I Posted does not apply.

In your place I would try the nvidia-experimental-304 driver from Additional Drivers, first, unless you are already familiar with installing an Nvidia.com Download driver.

But steer clear of the 310 version.

If you still have problems, please Post:```
 lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```Chao!, **bogan**.

---

### Post by texpat on 2013-02-21
Hi bogan,

so far the 310 drivers are working well, but guess I'll follow your advice and install the 304 ones. Seems safer in the long run.

Thanks!

---

### Post by bogan on 2013-02-21
Hi!, **texpat,**

I am a great believer in the Ford motto of; " If it aint broke, don't fix it", so if 310 is working for you.....x.

I have 310 working on one OS without problems, and have no personal experience of any. I think it probably depends on which GPU is in use. Certainly it is inadviseable for any GPU prior to GeForce 7xxx.

I was passing on what I have read in other posts, a warning from nvidia, and advice from MAFoElffen, for whom I have the greatest regard in these matters.

Chao!, **bogan**.

---

### Post by texpat on 2013-02-21
I ran some benchmarks (among others GpuTest from [geeks3d]("http://www.geeks3d.com/20121113/gputest-0-2-0-cross-platform-opengl-benchmark-furmark-lands-on-linux-and-os-x/#download")) and graphics apps and all went fine, so I guess it'll be OK to stick with what works.

---

