---
title: "Revert to older kernel"
date: 2006-12-19
forum: General Help
---

### Post by Hamal on 2006-12-19
I've been having a problem with my scanner which connects through a scsi card (scanner identifies itself as a FlatbedScanner_9). Unfortunately, it does not work with Edgy because the newer kernels broke support for it. The workaround is to revert to a 2.6.15 based kernel - which makes sense seeing as the scanner worked fine under Dapper.

Rather than revert back to Dapper, I'd really prefer to install a 2.6.15 based kernel on this current Edgy system and select it from the grub menu if I need to scan. My only issue there being how exactly do I go about that? I imagine I could find an old backports repository and apt-get the older kernel, but would that work? Or would I need to compile from source? Do I risk killing this install if something goes wrong?

If someone has some pointers or links I'd be awfully grateful.

---

### Post by pay on 2006-12-19
I would recommend trying to find out if the newer kernels have support for your scanner and then using one of those.

---

### Post by Hamal on 2006-12-19
> **pay said:**
> I would recommend trying to find out if the newer kernels have support for your scanner and then using one of those.

No, they don't. The latest kernels broke support. The workaround is an older kernel. The latest working being 2.6.15.

---

### Post by pay on 2006-12-19
In that case look for kernel patches for your scanner and compile your own.

---

### Post by Hamal on 2006-12-19
> **pay said:**
> In that case look for kernel patches for your scanner and compile your own.

If you can find one available (I cannot) and give me a detailed step-by-step instructions on how to compile a kernel up to Ubuntu's standards then I would consider it.

Until then, maybe you would like to give me some advice on implementing a solution that is actually feasible and will not introduce the possibility of hosing my system - like showing me how to install an older version of the linux kernel which should logically solve my problem.

---

### Post by pay on 2006-12-19
I don't know what scanner you have. Heres a quick crash course on how to compile a kernel ```
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.15.7.tar.gz
sudo tar jxvf -C /usr/src/linux-2.6.15.7 linux-2.6.15.7.tar.bz2
sudo ln -s /usr/src/linux-2.6.15.7 /usr/src/linux
```Now's the time to patch it if needed and then ```
cd /usr/src
sudo make menuconfig
sudo make clean && sudo make && sudo make modules_install
sudo mount /boot && sudo make install
sudo module-rebuild rebuild
```Make sure you have your /boot partition mounted
Heres a howto [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by Hamal on 2006-12-19
That's a pretty good guide for installing a vanilla kernel, however I was hoping to be able to revert back to a previous 2.6.15 based Ubuntu kernel using apt-get and benefiting from those enhancements (menuconfig is awfully daunting for a new user and Ubuntu are pretty good at installing the most frequently used and helpful patches). I was hoping it could be as easy as adding a repository, apt-getting a handful of kernel related packages and editing my grub.conf with an extra entry.

However, if no-one can provide me with a way to do this then your solution looks to be quite satisfactory.

---

### Post by pay on 2006-12-19
You maybe able to do all those things that you want but I'm scared that you might get undesirable results from getting a kernel from an older version of Ubuntu. Also when you finish compilling the kernel, make sure you link /usr/src/linux back to the latest kernel, otherwise you won't get video driver support and things like that with the new kernel.

---

