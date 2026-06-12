---
title: "please help me uninstall xen"
date: 2015-11-21
forum: General Help
---

### Post by freddyfields on 2015-11-21
So if you noticed my other post about android, you will see ive been messing with virtual machines. Well i downloaded xen i believe by apt-get xen or whatever and then decided i dont want it. Now i have two extra items in the grub menu.  something like ubuntu/ xen low lantency and ubuntu/xen advance options (not exactly what it says).  When i run wireshark on windows, i can see a virtualization network of some kind. Please, how can i uninstall this?  apt-get remove doesnt seem to work..

[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

---

### Post by grahammechanical on 2015-11-21
You could try

```
sudo update-grub
```

---

### Post by freddyfields on 2015-11-22
all that did was make ubuntu/ xen my default boot. 

```
falcor@falcor-NE56R:~$ sudo update-grub
[sudo] password for falcor: 
Including Xen overrides from /etc/default/grub.d/xen.cfg
WARNING: GRUB_DEFAULT changed to boot into Xen by default!
         Edit /etc/default/grub.d/xen.cfg to avoid this warning.
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-33-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-33-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-33-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-33-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-33-generic
Found initrd image: /boot/initrd.img-3.19.0-33-generic
Found linux image: /boot/vmlinuz-3.19.0-33-lowlatency
Found initrd image: /boot/initrd.img-3.19.0-33-lowlatency
Found linux image: /boot/vmlinuz-3.19.0-33-generic
Found initrd image: /boot/initrd.img-3.19.0-33-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
Found Windows 7 (loader) on /dev/sda3
done
falcor@falcor-NE56R:~$ 



```


cant find any solution online about how to actually remove it

---

### Post by freddyfields on 2015-11-28
Bump.. any help? its quiet annoying.

---

### Post by tridentlead on 2015-11-29
Firstly run:
```

sudo apt-get autoremove

```
This will (hopefully) remove any leftover kernels and headers. If that doesen't do it run:
```

sudo dpkg -l | grep linux-image

```
This will list all leftover linux kernels and headers, use apt-get remove to remove all the unwanted xen related kernels. Lastly run:
```

sudo update-grub

```
This will update grub, this time hopefully without the extra xen options.


EDIT: Reading the above term output, you may also want to try removing /etc/default/grub.d/xen.cfg and then updating grub

---

### Post by flocculant on 2015-11-29
> **freddyfields said:**
> ...  apt-get remove doesnt seem to work..

...

Ok.

So rather than have people guess - what does it actually say when you try apt-get remove in a terminal? 

Looking about elsewhere 

sudo apt-get remove xen-hypervisor-amd64 should work, so the terminal output might shed some light on the situation.

---

### Post by flocculant on 2015-11-29
> **Daniel_Stutman said:**
> Firstly run:
```

sudo apt-get autoremove

```
This will (hopefully) remove any leftover kernels and headers. If that doesen't do it run:
```

sudo dpkg -l | grep linux-image

```
This will list all leftover linux kernels and headers, use apt-get remove to remove all the unwanted xen related kernels. Lastly run:
```

sudo update-grub

```
This will update grub, this time hopefully without the extra xen options.


EDIT: Reading the above term output, you may also want to try removing /etc/default/grub.d/xen.cfg and then updating grub

Not sure how removing kernels is going to help remove the whole package.

Would it not also be wise to see what is in xen.cfg before you tell people to remove it?

---

### Post by flocculant on 2015-11-29
> **freddyfields said:**
> Bump.. any help? its quiet annoying.

Ok. 

I installed xen-hypervisor in a vm. Rebooted (couldn't actually get anything to work - I guess virtual inside virtual ending up on the other side of the universe or something) however

I went of to a vt, ran

```
sudo apt-get remove xen-hypervisor-4.4-amd64
```

Which left a bunch of packages behind so

```
sudo apt-get autoremove
```

cleared them up - result was a normal boot into the vm.

---

### Post by freddyfields on 2015-12-01
> **flocculant said:**
> Ok. 

```
sudo apt-get remove xen-hypervisor-4.4-amd64
```




This code is working. before it was saying 

```
falcor@falcor-NE56R:~$ sudo apt-get remove xen-hypervisor-amd64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xen-hypervisor-4.4-amd64' instead of 'xen-hypervisor-amd64'
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

Thanks guys.  your the best

---

