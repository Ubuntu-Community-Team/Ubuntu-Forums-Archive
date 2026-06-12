---
title: "do I have a driver problem?"
date: 2016-07-03
forum: General Help
---

### Post by mrwaistcoat on 2016-07-03
I get some screen tearing problems on browsers, and streaming video isn't terrible but not as smooth as it should be, with some flickering

I went onto additional drivers - it finds one unknown device it said the device wasn't working.  There is an option of intel driver, which I select.   Now it still says "unknown device . this device is using an alternative driver" and that one propriety driver is in use. Does that sound OK?

Whether I use the intel driver or not seems to make no difference to the issues - so is there a driver problem or am I barking up the wrong tree?

My graphics are Intel® HD Graphics 520 (Skylake GT2) and I'm using a HP Pavilion

Any advice appreciated, cheers

---

### Post by pqwoerituytrueiwoq on 2016-07-03
What release are you using? 14.04, 16.04, etc.

---

### Post by mrwaistcoat on 2016-07-03
I'm using 16.04

I've tried ubuntu, kubuntu and gnome.  Same in all

Thanks

---

### Post by pqwoerituytrueiwoq on 2016-07-03
I'd try the mainline kernel and see if that makes a difference
a while back i made a script to make installing it simple
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)
the command to get the latest kernel is this
[FONT=courier new]KernelUpdateChecker -r \*[/FONT]
but if you would rather just install the kernel here are the deb files
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.7-rc5-yakkety/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.7-rc5-yakkety/)

---

### Post by mrwaistcoat on 2016-07-04
Cheers

Just had a system update, and all seems well now.  Fingers crossed!

If it goes pear shaped, I'll try your suggestion

---

