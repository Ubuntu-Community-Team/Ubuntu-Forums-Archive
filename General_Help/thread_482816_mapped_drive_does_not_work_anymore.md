---
title: "mapped drive does not work anymore"
date: 2007-06-24
forum: General Help
---

### Post by monitordawg on 2007-06-24
I have fiesty fawn. I had edited the fstab file to map a drive to a windows computer. My network settings were using dhcp. I recently changed my network settings to a static ip address. 

Upon making this change my mapped drive no longer worked. I could not even ping the windows computer I was connecting to. but when I added the client to the hosts file in network settings on my linux machine I was now able to ping the windows server I was mapping to. However my mapping no longer works at all. When I double click on the mapped drive I get a message saying "opening 'filesrv' you can stop this operation by clicking cancel". 

I've rebooted my linux machine and it makes no difference. I don't understand why changing from a dhcp to a static ip why this would make a difference. My fstab file looks like this. 

"//192.168.5.110/home /mnt/filesrv smbfs username=administrator,password=xxxxxxxx,uid=xxxxx 0 0"

Let me know what you think.

---

### Post by monitordawg on 2007-06-25
I've worked through my problem further. I've determined if all I change is my eth0 from dhcp to static my mounted drive in FSTAB no longer works. I've changed back to dhcp and the fstab mount works everytime.

When I go to my mounted drive point and try to perform a ls on the directory I get this result
ls: .: Input/output error

Here is my fstab line I've been using.

//192.168.5.110/home /mnt/filesrv smbfs username=username,password=password,uid=name 0 0

I've looked into this as much as I can and am unable to determine what is causing this issue. I know the static ip address works because I can manually mount the samba drive to a different mount point. However I don't want to have to do it manually. I want it automated thus the edit in the fstab file.

---

