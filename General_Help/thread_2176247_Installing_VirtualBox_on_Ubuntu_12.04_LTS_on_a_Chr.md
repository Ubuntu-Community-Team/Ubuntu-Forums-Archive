---
title: "Installing VirtualBox on Ubuntu 12.04 LTS on a Chromebook 303c"
date: 2013-09-23
forum: General Help
---

### Post by Fedoraguy on 2013-09-23
I tried to install Virtualbox on Ubuntu Software Center.  I searched for "virtualbox" on the Software Center, it came up, I clicked on it, and it said this "There isn't a software package called “virtualbox-qt” in your current software sources."  Is there a way to add a software source or could someone help me add a software source so I can install it in Software Center, I really don't wanna use terminal, besides every time I try to install something, it just doesn't.  Please help

---

### Post by JKyleOKC on 2013-09-23
Save yourself lots of confusion by getting vbox from [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) instead of through the Software Center. The SC version is woefully out of date; Oracle's official site is always up to date, and even includes instructions for adding a PPA to your system so that it gets automatic updating whenever a new version becomes available.

Usually it's best to stay with the distro's repositories, but vbox is a notable exception.

---

### Post by mlentink on 2013-09-23
I'm afraid you're not lucky. First of all, the Chromebook (is it a Samsung?) almost certainly runs on a ARM-processor, and there aren't any Virtualbox-packages for that processor in the repos. I'm not sure which VM does run on ARM, but you might try Qemu. 
Secondly, a notebook with those specs won't be particularly equipped to run a VM, especially if the guest needs a lot of horsepower and memory, like e.g. Windows. A lean linux distro (e.g. Lubuntu) might run ok, but you'll have to try that.

Edit: just found this, which might help as well: [http://superuser.com/questions/509774/can-i-run-windows-7-in-a-vm-on-arm-processor-under-ubuntu-xubuntu-lubuntu](http://superuser.com/questions/509774/can-i-run-windows-7-in-a-vm-on-arm-processor-under-ubuntu-xubuntu-lubuntu)

---

### Post by slickymaster on 2013-09-23
> **JKyleOKC said:**
> Save yourself lots of confusion by getting vbox from [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) instead of through the Software Center. The SC version is woefully out of date; Oracle's official site is always up to date, and even includes instructions for adding a PPA to your system so that it gets automatic updating whenever a new version becomes available.

Usually it's best to stay with the distro's repositories, but vbox is a notable exception.

+1

Here's the download location in case you're interested: [http://download.virtualbox.org/virtualbox/4.2.18/](http://download.virtualbox.org/virtualbox/4.2.18/)

---

### Post by mlentink on 2013-09-23
> **slickymaster said:**
> +1

Here's the download location in case you're interested: [http://download.virtualbox.org/virtualbox/4.2.18/](http://download.virtualbox.org/virtualbox/4.2.18/)


Could you please point out the ARM versions to me? AFAIK Virtualbox does NOT run on ARM-processors. The OP has a Chromebook 303c which is, I think, a Samsung equipped with an Exynos (=ARM) processor.

---

### Post by slickymaster on 2013-09-23
> **mlentink said:**
> Could you please point out the ARM versions to me? AFAIK Virtualbox does NOT run on ARM-processors.
No I can't. As you correctly put it, we can't run VirtualBox on ARM CPUs. The closest possible is QEMU, but performance will be hopelessly slow.
> **mlentink said:**
> The OP has a Chromebook 303c which is, I think, a Samsung equipped with an Exynos (=ARM) processor.
When I posted my previous download link I didn't have the slightest idea that his Chromebook is equipped with an ARM processor, which now thanks to your information I do.

---

