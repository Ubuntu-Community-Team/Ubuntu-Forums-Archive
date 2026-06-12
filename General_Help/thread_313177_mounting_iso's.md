---
title: "mounting iso's"
date: 2006-12-05
forum: General Help
---

### Post by crowquill on 2006-12-05
i used the diretions from this site:[http://ubuntu.wordpress.com/2005/10/24/nautilus-script-to-mount-iso-files/](http://ubuntu.wordpress.com/2005/10/24/nautilus-script-to-mount-iso-files/)

when i click the iso and choose mount a new drive named cd-rom 1 shows up but when i double click it gives me this error:
mount: special device /dev/hdc does not exist
perhaps there's a dependency issue i need to adress?

---

### Post by caricc on 2006-12-05
Since iso is windows related. you may need to install and setup ntfs3g. This will allow you  to mount a windows volume.

---

### Post by crowquill on 2006-12-05
how exactly go about that?

---

### Post by MJN on 2006-12-05
Thankfully, ISO images have nothing to do with Windows... ;)

To pinpoint where your problem lies (mount/Nautilus/other), try mounting the ISO image directly at the command line (i.e. not using Nautilus) using:

[B]sudo mount -o loop -t iso9660 <ISO image filename> <mount point>

[/B]Does it work? If not, what's the error?

Mathew

---

### Post by madcow72 on 2006-12-05
MJN is exactly right.  Mount the ISO by using his code.  Explicitly, do the following:
```
sudo mkdir /mnt/iso/
sudo mount -o loop -t iso9660 <ISO image filename> /mnt/iso/
```

You should then see the mounted iso file system under /mnt/iso.

---

### Post by crowquill on 2006-12-05
root@greg-laptop:/home/greg# sudo mount -o loop -t iso9660 /home/greg/disc2.iso /mnt/iso/
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by MJN on 2006-12-05
Are you sure it's an ISO image? Do you know what created it?

---

### Post by crowquill on 2006-12-05
its a final fantasy disc that i downloaded. i mounted it just fine on my windows machine...

i just mounted an ubuntu iso i have. it didnt give me any errors but i still cant access cdrom1

---

### Post by madcow72 on 2006-12-05
It sounds like the file may be corrupt, but it will be hard without the MD5Sum's to check, (I assume you don't have this if you downloaded it from PTP or torrent?)  Out of curiosity, how did you mount it in Windows?  Have you tried burning the iso to CDRW or something with k3b and checking the CD after burning?

---

### Post by crowquill on 2006-12-05
i mounted it in windows using daemon tools. im trying not to use cds because my drive is screwed up : / i dont think it is corrupt because i get the same error with any iso.

---

### Post by po0f on 2006-12-05
crowquill,

Here's an idea: buy the game and rip your own ISO.  As a pirated game is the topic of this discussion, I'm thinking about reporting it.

---

