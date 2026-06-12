---
title: "Installing VMWareplayer"
date: 2013-08-11
forum: General Help
---

### Post by DeMus on 2013-08-11
Hi, I have installed MWareplayer but when I start the program I get a message saying:
Before you can run VMWare, several modules must be compiled and loaded into the running kernel.
Kernel headers 3.8.-26-generic.

How do I do this? What do I need? I am using 3.8.0-26 but the program asks for .h files. Where do I get those, how do I install them and where are they installed? I need to give a path where the VMWare installation program can find them.

Thanks.

---

### Post by chadk5utc on 2013-08-11
I believe what your looking for is:
>  sudo apt-get install build-essential linux-headers-$(uname -r)

---

### Post by DeMus on 2013-08-11
[ATTACH=CONFIG]245267[/ATTACH]Thank you for your help, and although it sounds very plausible what you wrote, it did not help. I still get the same warning when I fire up VMWare.
I even rebooted after the installation but also that did not help. Hope you have some more ideas.

---

### Post by Cheesemill on 2013-08-11
Which version of Ubuntu and which version of VMware Player?

If the version of Ubuntu you are using is later than the release of the VMware Player version you are using then it's not officiially supported and you will need to patch the VMware installer before running it.

You can usually find the required patch and instructions for using it by simply googling for 'VMware Player Ubuntu xx.xx patch' where xx.xx is your Ubuntu version.

---

### Post by DeMus on 2013-08-11
Cheesemill, you are right. I did not have the latest version of the VMware Player. I really thought I did but I was wrong.
Now it works. Thank you so much.

---

