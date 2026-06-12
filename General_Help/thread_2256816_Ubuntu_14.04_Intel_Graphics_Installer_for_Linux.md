---
title: "Ubuntu 14.04 Intel Graphics Installer for Linux"
date: 2014-12-15
forum: General Help
---

### Post by Billisnice on 2014-12-15
This is what I get when I try to use the installer.

W:Failed to fetch [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Thanks

---

### Post by papibe on 2014-12-15
Hi  Billisnice.

I think that's the error when you are trying to install it?

Could you post the commands the gave you that error?

Regards.

---

### Post by Billisnice on 2014-12-15
When i run the program that is msg I get. 

[ATTACH=CONFIG]258588[/ATTACH]

---

### Post by papibe on 2014-12-15
Thanks.

The error you're seeing is an error that happens when you update your sources. You can test that by open a terminal and running:
```
sudo apt-get update
```
I believe you have added the openshot develover ppa, right? It looks like there's no longer (or never was) a Trusty version. That's is the error you are getting. 

I'd recommend opening 'Software & Updates', then going to the 'Other Software' tab, and un checking the openshot ppa.

You can test if the error goes again, by running again on the terminal:
```
sudo apt-get update
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by monkeybrain20122 on 2014-12-15
The openshot-developer ppa is not available for 14.04. You should remove it from your sources list first. Open synaptic, go to Settings > Repositories > Other Software and uncheck the line for openshot-developer and then reload synaptic, close it and run the intel installer again.  Synaptic is installed by default in lubuntu.

---

### Post by Billisnice on 2014-12-15
i deleted the openshot develover ppa and the graphics updated and deleted old files. I really do not see a noticeable different. What does the Intel updater do?

---

