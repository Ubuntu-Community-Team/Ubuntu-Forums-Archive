---
title: "Highpoint RocketRAID"
date: 2008-05-31
forum: General Help
---

### Post by rienholt on 2008-05-31
Hello.

I just received my Highpoint RocketRAID 3120 in the card in the mail. The physical install went swimmingly and I was able to set my 1TB SATA drives to RAID 1. However when I load into Ubuntu it can't see anything. I expected this but it did say Linux compatible when I bought it so I figured Highpoint would have the needed info. Turns out they do have drivers on their website but they are for Redhat/Fedora and Suse. They also require floppy disks.

I am not really sure what to do at this point. I assume I have to compile drivers from binaries(maybe?) however I am unable to figure out where to get them. If you can provide any assistance I would be most appreciative..

Thank You in Advance,
A. Baker

---

### Post by fjgaude on 2008-05-31
You might try using **alien**, it's in the repository, to convert the .rpm to .deb... that may take a little study on how to use **alien**, but I'm sure you will figure it out.

---

### Post by quelx on 2008-05-31
from NewEgg :|

> Ok, This card does work in ubuntu (Hardy, 8.04), but you have to compile the kernel module from source found here: [http://www.highpoint-tech.com/BIOS_Driver/rr3120/Linux/rr3120-linux-src-v1.1-080307-1905.tar.gz](http://www.highpoint-tech.com/BIOS_Driver/rr3120/Linux/rr3120-linux-src-v1.1-080307-1905.tar.gz) This works fine... IF you can use it as a kernel module. If you plan on building it into your kernel (so you can boot from the array defined on the card) You'll find the support for this is quite weak. The patch script they provide doesn't work as advertised. You can get it complete successfully with some prodding, but it still doesn't show up in your `make menuconfig`. I imagine some more experienced kernel folks could just patch it by hand, but I'm not one of them :(

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816115047](http://www.newegg.com/Product/Product.aspx?Item=N82E16816115047)

After creating the module you will need to add it to your initrd for your kernel if you plan to boot off of the card. **update-initrd**

---

### Post by AllGamer on 2011-04-25
for anyone arriving to this topic from Google, the information is quite outdated.

for anyone on 10.x or the new beta 11.x

installing / upgrading the Rocket Raid drivers from source is simple and straight forward as

```
sudo make install
```

just run that after you untar the drivers from rocketraid download.

after the drivers gets installed, install the highpoint management console
[http://ubuntuforums.org/showthread.php?t=1737847](http://ubuntuforums.org/showthread.php?t=1737847)
to assign the drives/create the raid, and format the volume.

then if you want the RAID to auto-mount on boot, all you need to do is add the RAID volume disk info on /etc/fstab

```
sudo gedit /etc/fstab
```

you can Google HOWTO obtain UUID to use in fstab

---

