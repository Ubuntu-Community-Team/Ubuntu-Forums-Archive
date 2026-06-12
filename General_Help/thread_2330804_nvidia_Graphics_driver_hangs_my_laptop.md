---
title: "nvidia Graphics driver hangs my laptop"
date: 2016-07-15
forum: General Help
---

### Post by coolnine98 on 2016-07-15
Hi:

This is my first post and new to Ubuntu. Recently, I have installed Ubuntu Gnome 16.04 to my old HP laptop. Everything seems working fine until I installed nvidia graphic card driver to my computer. It boots up fine but I can't do anything like, for example when I click firefox, nothing happened. I cant open any application or nothing. I can see my mouse cursor moving around the screen.How do I solve this? 

Thanks

---

### Post by GU4$+7rxH#@ on 2016-07-15
Hello

Perhaps it is predetermined by the driver Nouveau.

In some post I read this often cause problems for these cards .

Let's try to uninstall it.

To avoid confusion sending the link of the page with the possible solution.

Follow the second answer.

[http://askubuntu.com/questions/112302/how-do-i-disable-the-nouveau-kernel-driver](http://askubuntu.com/questions/112302/how-do-i-disable-the-nouveau-kernel-driver)

Or:

[http://www.allaboutlinux.eu/remove-nouveau-and-install-nvidia-driver-in-ubuntu-15-04/](http://www.allaboutlinux.eu/remove-nouveau-and-install-nvidia-driver-in-ubuntu-15-04/)

I hope to serve.

Thanks

---

### Post by mörgæs on 2016-07-16
Hi, welcome to the fora.

We need to see the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. If the present install is dead it can be done from a live boot.

---

