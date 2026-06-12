---
title: "About running Ubuntu and Beryl on a Macbook"
date: 2007-02-12
forum: General Help
---

### Post by roostishaw on 2007-02-12
Hello,

It's been quite a while since I've posted around here, but here it goes.

Does anyone have a Macbook successfully running Ubuntu and AIGLX + Beryl (and Gnome I suppose)? 

I've been reading for a while about this, and still haven't decided. Here are a few of the issues holding me back:

The live CD's resolution is way too low.
The wireless isn't working with WPA, which I was told it would with gnome-network-manager.
The trackpad wont right click (two finger tap), nor will it scroll (two finger scroll).
Beryl wont run without crashing just seconds after I launch it.
Brightness control doesn't work.

That's pretty much all I can think of at the moment. This is post was not intended to bash Ubuntu, although it may seem like I'm just complaining :p 

If anyone here has any experience running Ubuntu with Beryl on a Macbook, please share.

Thanks!

---

### Post by Laerte Andrade on 2007-02-12
> **roostishaw said:**
> 
Does anyone have a Macbook successfully running Ubuntu and AIGLX + Beryl (and Gnome I suppose)? I've been reading for a while about this, and still haven't decided. 

Well, I have a Macbook Core 2 Duo 2Ghz, and I had sucessfully installed Edgy, and it's 95% functional. AIGLX and Beryl work perfectly. I only have two problems right now (microphone and suspend), and both of them will be taken care of when I have time. Now, talking about your issues:

> The live CD's resolution is way too low.

First thing of all, follow the instructions in [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) and you will have a very usable system. The resolution problem is treated there, and it is easily corrected (just a *sudo apt-get 915resolution* actually).

> The wireless isn't working with WPA, which I was told it would with gnome-network-manager.

If you have a Macbook Core Duo, you can make the wireless work with madwifi. If you have a Core 2 Duo, you need to install a new version of ndiswrapper (the one in the edgy repositories won't do), and follow[ these instructions]("http://ubuntuforums.org/showthread.php?p=1822454#post1822454"), but using [this windows driver]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-66449") instead.

> The trackpad wont right click (two finger tap), nor will it scroll (two finger scroll).

This is where things get a little tricky, but not much. You can't use the advanced features of the trackpad without compiling your own kernel using some macintel patches. In any case, you should know that the trackpad is very usable without these features.

> Beryl wont run without crashing just seconds after I launch it.

I think this has been already corrected. Just use the Beryl repositories as stated in the Macbook-Ubuntu wiki.

> Brightness control doesn't work.

Also taken care of in the wiki page. However, the instructions for the shortcuts only works with Metacity, not with Beryl.

Try searching this forum for "macbook" and reading a lot of threads. You may find it very useful!
Good luck! :)

---

### Post by mustang on 2007-02-12
Macbook (1st gen) user here. Beryl works fine using the guide posted above. Although I do get weird windowless borders every now and then...

---

### Post by roostishaw on 2007-02-12
> **Laerte Andrade said:**
> If you have a Macbook Core Duo, you can make the wireless work with madwifi. 

[http://www.mactel-linux.org/wiki/Macbook_dual_boot_wifi-with-WPA_howto#Configuring_the_wireless_network](http://www.mactel-linux.org/wiki/Macbook_dual_boot_wifi-with-WPA_howto#Configuring_the_wireless_network)

^^ Is that what you used to get the wifi working? That's all I could find, and even that seems a little hack-ish.

---

### Post by mustang on 2007-02-12
> **roostishaw said:**
> [http://www.mactel-linux.org/wiki/Macbook_dual_boot_wifi-with-WPA_howto#Configuring_the_wireless_network](http://www.mactel-linux.org/wiki/Macbook_dual_boot_wifi-with-WPA_howto#Configuring_the_wireless_network)

^^ Is that what you used to get the wifi working? That's all I could find, and even that seems a little hack-ish.

He's referring to madwifi. Go to madwifi.org and get the latest CVS drivers. "make" and then "sudo make install" should do it.

---

### Post by roostishaw on 2007-02-16
Last question: How can I control the fan speed, or just set it manually?

---

