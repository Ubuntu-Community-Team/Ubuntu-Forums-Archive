---
title: "Ubuntu Live CD customization"
date: 2017-05-23
forum: General Help
---

### Post by navachaitanya on 2017-05-23
Hi All,

I was trying to do Ubuntu live CD customization with virtualbox installed,Can any one please help me or providing some reference links to make live cd customization

I want to customize Live CD with Ubuntu 16.04 version and I have tried UCK but I was not able to add the packages like Virtualbox,

Please Help me and Thanks in Advance

---

### Post by howefield on 2017-05-23
Not a chat/discussion thread so moved to the "*General Help*" forum in the meantime.

---

### Post by ian-weisser on 2017-05-23
Live environments are not designed to run complex applications like Virtualbox. Your settings may run afoul of RAM limits on some systems. You probably won't be able to upgrade Virtualbox.
Your virtual hard drive will be read-only, possibly causing the guest OS to crash. Even with persistence, the virtual hard drive will have a limited life.

Build your Live system in a VM, so you can figure out which of those problems (and others) applies to your situation.

If, on the other hand, you simply want to install Ubuntu (with virtualbox) normally, then search for the topic of 'preseed file'.

---

### Post by yancek on 2017-05-23
I don't know what "UCK" is and am not really sure what you are trying to do.  Do you want a modified DVD that contains VirtualBox?  If you install your Ubuntu to a hard drive and then install VirtualBox and then download and install either 'Systemback' or 'PinguyBuilder', you can create an iso file which you can then burn to a DVD or put on a flash drive and it will have VirtualBox.  Not really sure why you want that because as a Live DVD, anything you change or install in Virtualbox will be gone on reboot.

---

