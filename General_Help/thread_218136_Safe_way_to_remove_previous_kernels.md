---
title: "Safe way to remove previous kernels"
date: 2006-07-18
forum: General Help
---

### Post by wifiabc on 2006-07-18
After installing updates recommended by update manager, I found the following in /boot and also additional entries in menu.lst. 

What is the safest way to remove the older ubuntu kernels?  

                          
abi-2.6.15-26-386     
abi-2.6.15-23-386

System.map-2.6.15-26-386
System.map-2.6.15-23-386
  
initrd.img-2.6.15-26-386 
initrd.img-2.6.15-23-386 

config-2.6.15-26-386 
config-2.6.15-23-386 
            
vmlinuz-2.6.15-26-386
vmlinuz-2.6.15-23-386

---

### Post by yopnono on 2006-07-18
Just remove them in synaptic.

---

### Post by Ramses de Norre on 2006-07-18
```
sudo aptitude purge linux-image-2.6.15-23-386 linux-restricted-modules-2.6.15-23-386
```
Do this for all kernel versions you want to remove (as example I did it for the 2.6.15-23-386 kernel)
```
dpkg -l|grep 2.6.15|grep linux
``` will give you a list of installed kernels and restricted modules, don't remove things as linux-386!

---

### Post by wifiabc on 2006-07-18
Hi,
Thanks. As a comparison, I also tried synaptic. It offers 2 options when I mark the linux-image for removal. One of the options being "Complete removal including configuration". Is this the option that I should select for removing old kernels if using synaptic?

---

### Post by Ramses de Norre on 2006-07-18
You should always remove config files when you're not planning to reinstall the package, they only take disk space.. In aptitude you use the option purge to delete config files too and remove to only remove the package and not the config files.

---

### Post by wifiabc on 2006-07-18
Thanks Ramses.

---

