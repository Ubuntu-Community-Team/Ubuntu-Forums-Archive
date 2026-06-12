---
title: "Ubuntu GNome missing 319nvidia drivers in Jockey question"
date: 2013-06-05
forum: General Help
---

### Post by Heeter on 2013-06-05
Hi all,

I had Ubuntu Unity 13.04 installed with Steam, running 319nvidia drivers with 3.9.4 kernel. Last week my setup crashed, bad HD.

I installed UbuntuGnome 13.04 on a new HD, I installed Steam and also 3.9.4 Kernel, but jockey-kde is missing the 319 driver in the list (Only 313, 310, 304 nvidia series drivers listed.) I installed the x-orgedgers ppa, but the 319 is still not showing up in Jockey-kde, like it did in Ubuntu Unity.

I would like to install the 319 driver to resolve a some Steam gaming issues.

Is there a real good howto that I can print and follow on manually installing nvidia drivers. The howto's I find are quite lacking.

Thanks

Heeter

---

### Post by Frogs Hair on 2013-06-05
I found an article , but have not used the method posted . The kernel package is not noted in the article either and I assume they are using recommend version . Check for driver ppas also. Installing anything outside the repository is at your own risk.


 [http://www.itworld.com/software/355978/install-nvidia-31917-drivers-ubuntu-1304](http://www.itworld.com/software/355978/install-nvidia-31917-drivers-ubuntu-1304)

---

### Post by Heeter on 2013-06-05
Thanks a whole bunch, Frog's Hair...

Exactly what I was looking for.

Was having graphics performance issues with 304/310 drivers, but it was resolved with the 319 drivers, thanks again,

Heeter

---

### Post by searchfgold6789 on 2013-06-05
Firstly, have you tried updating the package lists? You can do it from the terminal: ```
sudo apt-get update
```(type your password, which is invisible, and press enter.)
Are you using 32bit or 64bit?

---

### Post by Heeter on 2013-06-05
> **searchfgold6789 said:**
> Firstly, have you tried updating the package lists? You can do it from the terminal: ```
sudo apt-get update
```(type your password, which is invisible, and press enter.)
Are you using 32bit or 64bit?

Hi searchfgold6789,

I do a package update after every ppa I install.

I am using a 64bit system.


Thanks

Helder

---

