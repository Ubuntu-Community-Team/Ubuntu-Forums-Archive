---
title: "How Can I Share Swap Area Between Linux and Ubuntu?"
date: 2016-01-22
forum: General Help
---

### Post by Rocky_Bennett on 2016-01-22
I have a little system that is running a Haswell 4690 CPU and an Asus Z97-A motherboard with 16 GB of DDR3 memory running at at 1866 mhz. I don't really need to run a swap area but I set up a little area on one of HDDs to have approx. 5 gb of swap. I have this configured to both my Linux Mint 17.3 installation and my Ubuntu 15.10 installation. My question is can I have this swap area be activated automatically upon turning on my computer. Right now when I restart into either Linux or Ubuntu, the swap area is off and I have to manually turn on the swap area. It is quick and easy to turn on the swap area, so it is not really a big hassle, but I would like it be turned on automatically. Is there anyway to accomplish this.

Thanks in advance for any help in this matter.

---

### Post by sisco311 on 2016-01-22
Yes, you have to create an entry in  /etc/fstab for the swap partition.


For more details, see:
[uhelp]community/SwapFaq[/uhelp]
[uhelp]community/Fstab[/uhelp]
[uhelp]community/UsingUUID[/uhelp]

---

### Post by Topsiho on 2016-01-22
1. your question is "incomprehensible". Ubuntu is a Linux itself.
2. of course one can understand quite well what you are asking :). People are not computers ...
3. during the install of Linux Mint, and of Ubuntu, one can dedicate a partition to swap. Both can use the same swap partition.

I think you have to study the /etc/fstab file in Mint and see what line mounts the swap partition when the system is booted in Linux Mint.
Copying this line, as root, using sudo, exactly into the /etc/fstab of Ubuntu should work (I think). The UUID number identifies the swap partition.

Topsiho

---

### Post by ajgreeny on 2016-01-22
You need a line with the following syntax in /etc/fstab but with your own swap partition UUID.
```
UUID=0707fdc8-1299-4c11-9f93-8158d3c313d0 none            swap    sw              0       0
``` which is what you will see in The mint installation if that is the OS that has swap enabled at boot.
If none of your systems have swap enabled at boot you will need to get the UUID of the swap partition from command ```
sudo blkid -c /dev/null
```

---

### Post by Rocky_Bennett on 2016-01-22
Thanks all. I went ahead and edited my fstab folder in my editor and I added the correct partition to the UUID line and it fixed the whole thing.

Thanks again,

Rocky Bennett

---

### Post by ajgreeny on 2016-01-22
Great!

Please mark as SOLVED from the Thread Tools menu at the top of the thread.

---

### Post by Topsiho on 2016-01-22
Great your problem is solved.

I was to give you the blkid advise too, but there was a problem with the webpage of ubuntuforums.org, which prevented it reloading after I discovered my advise was not complete. Fortunately ajgreeny could give the full advise :) .

Topsiho

---

