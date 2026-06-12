---
title: "Repairing WiFi connection"
date: 2007-11-16
forum: General Help
---

### Post by netpage on 2007-11-16
I am new Linix but with many years of WIndows admin behind me so I know what I would normally do but not sure how this translates to Linux.

One problem I am having is my WiFi connection.  It works fine when the laptop is started but after a few times being put on suspend it stops.  In Windows XP I would now right button click the connection icon and select repair.  Is there an equivalent in Linux?

Thanks

James

---

### Post by briwood on 2007-11-16
sudo  /etc/init.d/networking restart

That will often fix problems like you describe. 

There have been a lot of problems resuming networking after suspend - especially on laptops like thinkpads.  And especially using network-manager.

I fixed my problems (thinkpad t40p) by:

* fresh install of Gusty (I don't trust upgrading after my upgrade to Feisty experience)
* disable ipv6 (search for how to do that. it's easy)
* use [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

hth

---

### Post by netpage on 2007-11-19
Thanks briwood,

I will stick with the 'command line' for now and see if that clears it.  I have a brand new install of Gutsy and checked out removing ipv6 but will try that later is needed.  Linux is all a bit new to me at the moment so one step at a time.

Regards

James

---

