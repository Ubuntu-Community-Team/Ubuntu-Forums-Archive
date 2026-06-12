---
title: "NVIDIA Driver Installer Can't Find Kernel Sources"
date: 2008-07-03
forum: General Help
---

### Post by blazercist on 2008-07-03
Hey so after last nights updates and a reboot my video was screwed.  So I figured it was some kernel update or something, which I know now was wrong.  But video wasn't working properly either way.

So I tried to reinstall the NVIDIA proprietary driver.

I have a 9600GT and only drivers 171.06 and up support my card.

So I ssh into the box.
sudo /etc/init.d/gdm stop
sudo sh NV*

all goes well until it attempts to build the driver, and it gives the error that it couldn't find kernel.h.  It tells me I need to install the kernel sources.  Only thing is that they are installed.

sudo apt-get install linux-headers-2.6.24-19-generic says its already installed.

ls /lib/modules/linux-2.6.24-19-generic/include/linux/
reports that kernel.h is infact there.

ls /usr/src/linux-2.6.24-19-generic/include/linux/
reports that kernel.h is infact there.

I tried running

sudo sh NV* --kernel-source-path /usr/src/linux-2.6.24-19-generic

because the default directory is /lib/modules and it still says it can't find kernel.h even though I know its there.

So what gives?

---

### Post by phidia on 2008-07-03
The ubuntu community guide for manually installing the nvidia driver is [here]("https://help.ubuntu.com/community/NvidiaManual")
Also note that there is a [preferred/recommended method]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"). Perhaps your card doesn't work with the ubuntu way of enabling the driver?

---

### Post by blazercist on 2008-07-03
yea the ubuntu way doesn't work with my card the driver in the repos doesnt have support for it, I'll try the wiki when I get home hopefully there is something i've missed that I can find there because this is very confusing.

I just dont understand how it can tell me the file is not there when it actually is, the installer tells me the path its looking in, i cd there and the file is there plain as day... its weird.

---

### Post by oldos2er on 2008-07-03
Open up System, Administration, Software Sources, and make sure Source Code is checked. Then run "sudo aptitude update."

---

