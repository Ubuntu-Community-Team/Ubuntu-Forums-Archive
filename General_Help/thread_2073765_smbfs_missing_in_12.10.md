---
title: "smbfs missing in 12.10"
date: 2012-10-20
forum: General Help
---

### Post by Alan.Brown on 2012-10-20
I have a 32GB USB flash drive connected to my modem/router.   This was always mounted on startup by the line in **/etc/fstab** - 
> **//192.168.0.1/USB     /home/user/USB    smbfs umask=000,uid=1000,gid=1000,guest,_netdev     0       0**This worked well up to 12.10 - now it doesn't work.   
BTW - it took me a long time and a lot of effort to find out how to do this!!!  :)

In Synaptic Package Manager **smbfs** is no longer available!! :confused:

I have tried **cifs** in **fstab** but that doesn't work.

I can mount the drive manually by using 
> **sudo mount -t cifs //192.168.0.1/USB /home/user/USB**Why will this not work in **fstab**?

TIA

Alan

---

### Post by mvidberg on 2012-10-20
I upgraded to 12.10 yesterday and noticed my networked samba HD was not mounting anymore as well.. but changing the "smdbfs" in /etc/fstab to "cifs" worked for me.

---

### Post by Alan.Brown on 2012-10-20
I tried that but it didn't work in **fstab** but does work if I mount the drive manually.

I think one or more of the options are incorrect in **fstab** - 

[B]umask=000,uid=1000,gid=1000,guest,_netdev

[/B]I know _netdev is required because the drive is connected to the network and that must be up before the drive can be mounted.  I am not sure about **umask**, **uid**, **gid** and [B]guest.

[/B]They worked with **smbfs** before

Alan

---

### Post by Alan.Brown on 2012-10-20
OK!!

I took out **umask=000** in **fstab **and the drive has mounted OK.   

I don't know why - so if anyone can explain to me I would be grateful.

Alan

---

### Post by djoh on 2012-10-21
Try this:
sudo apt-get install cifs-utils

It solves the issue on my 12.04 -> 12.10 server upgrade.

---

### Post by Alan.Brown on 2012-10-21
Thanks for your suggestion - I already have **cifs-utils**.  I have changed the type to **cifs **in **fstab **- it now works OK.

Why did **smbfs** disappear??

Alan

---

