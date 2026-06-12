---
title: "How to edit grub so that MS Windows entry is not SHOWN"
date: 2013-03-19
forum: General Help
---

### Post by wpshooter on 2013-03-19
Is this possible to edit the grub listing that is shown at boot so that the MS Windows OS that I have installed is just not SHOWN, i.e. don't want to uninstall Windows nor do I want to get rid of the grub entry for it, just don't want it to be SHOWN on the listing ???

If so, is this better done when the grub is displayed at boot or by editing the grub file after booting to Linux ?  

If after booting to Linux, what is the name of the grub file and where is it located ?

Thanks.

---

### Post by Enigmapond on 2013-03-19
The easy way: Install grub-customizer (you'll need the PPA) **&#8203;****ppa:danielrichter2007/grub-customizer**

---

### Post by oldfred on 2013-03-20
You also can turn off os-prober. It will not find any other systems if that is what you want.

       In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

You can then turn it back on later if you want.

---

### Post by wpshooter on 2013-03-20
> **Enigmapond said:**
> The easy way: Install grub-customizer (you'll need the PPA) **&#8203;****ppa:danielrichter2007/grub-customizer**

When I add this in, it says:   404 file not found !!!!

---

### Post by fantab on 2013-03-20
If you have only Ubuntu and Windows then disabling the 'os-prober' is best as suggested in post #3. 

As for [Grub-Customizer]("https://launchpad.net/~danielrichter2007/+archive/grub-customizer") add the following to your sources.list:

```

deb [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) YOUR_UBUNTU_VERSION_HERE main  
deb-src [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) YOUR_UBUNTU_VERSION_HERE main 
```

---

