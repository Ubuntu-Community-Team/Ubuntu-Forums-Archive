---
title: "LiveCD Customization - Adding and removing stuff"
date: 2013-03-26
forum: General Help
---

### Post by farmdve on 2013-03-26
Hi,

I have been following this guide [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) to customize my own LiveCD by using Ubuntu 12.04 TLS as my choice of OS, so far so great, but there is software I want to include in it, which I want to compile from source, but the article does not say anything about how to do that.
Secondly, my target machine is a laptop, which is quite slow and so I want to remove Gnome and add something that is as lightweight as possible like XCFE or something even better. I also want to update the compat-wireless driver, ath9k to the very latest and greatest.

Thirdly, I want to remove as much things as possible which I won't need, so this LiveCD can fit on a normal CD(700MB). But again, it's not said in the article what can be removed which I may not need.

Every software I install must be available to be used from the LiveCD, without installing the OS.

I am not a very experienced user of Ubuntu, so I am still new, and this is my first time customizing a LiveCD so thank you in advance :).

---

### Post by audunpoi on 2013-03-26
You could try remastersys. It makes installable media from your current installation.
[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

---

### Post by farmdve on 2013-03-26
Is it possible to compile the program and create a package from it, so I can just run dpkg on the chroot and install it that way. But I am not sure if there will be missing dependencies...

And my installation won't work since it's meant for different things.

---

### Post by audunpoi on 2013-03-26
Not sure. Maybe you could prepare it in a virtual machine.

---

### Post by farmdve on 2013-03-26
That is how I am doing it. I am a Windows user, my Ubuntu installation is in a VM, and I am preparing the LiveCD from that same VM.

---

### Post by audunpoi on 2013-03-26
Clone the VM and modify it? I guess you've thought of that already.

---

### Post by oldfred on 2013-03-26
You can start with the minimal CD. It has no gui, just kernel and enough drivers to download everything or nothing from the Internet. 
Some then have scripts to add their favorite apps. You can use or modify.

       [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
HowTo Achieve "Ubuntu-Desktop-Minimal" 
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)
Install script for minimal
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

