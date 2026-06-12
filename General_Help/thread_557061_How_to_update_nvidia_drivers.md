---
title: "How to update nvidia drivers?"
date: 2007-09-22
forum: General Help
---

### Post by mikeym on 2007-09-22
How do I update the nvidia drivers from the nvidia website?

I want to update them but when I run 

```

sudo /etc/init.d/dm stop
sudo ./NVIDIA-Linux-x86_64-100.14.19-pkg2.run

```

It tells me that the nvidia module can't be unloaded. I've tried it by hand (modprobe -r nvidia) and it tells me its in use. 

```

$lsmod | grep nvidia
nvidia               8119352  54 
i2c_core               26496  3 i2c_ec,nvidia,i2c_nforce2

```

Any ideas?

---

### Post by distroman on 2007-09-22
Did you remove the old drivers?
```
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86_64-100.* --uninstall 	#old drivers
sudo sh NVIDIA-Linux-x86_64-100.*		#new drivers		
sudo /etc/init.d/gdm restart
```

---

### Post by whistlingtony on 2007-09-22
I think you're doing it the hard way. Which version of Ubuntu are you using? Feisty has a wonderful manager for restricted drivers...

If you install the package for restricted drivers (will give you lots of goodies. Madwifi, Nvidia, etc) and then enable them with the restricted driver manager... It automagically works.

The problem with using downloaded drivers is... I THINK...  you'll have to reinstall them each time you upgrade your kernel.  That's annoying.

Apt-get is your friend.

Look for:
linux-restricted-modules
restricted-manager

You may have to enable the universe or multiverse package repositories

-T

---

### Post by mikeym on 2007-09-22
I have to use the NVidia drivers because I have an 8600GTS and it's not properly supported yet but the restricted drivers.

Distroman , you mke it sound simple (well it was).  Thanks.

---

