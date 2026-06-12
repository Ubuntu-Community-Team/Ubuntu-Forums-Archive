---
title: "nrg2iso and mounting problems"
date: 2006-11-11
forum: General Help
---

### Post by lungdart on 2006-11-11
I have a nrg file which I found out is a nero image file of some sorts. A quick glance in synaptic showed me there was a nrg2iso program.

I used nrg2iso
```

nrg2iso ./*.nrg ./*.iso 

```
and created the iso file I want.

I then preceded to mount the iso file with:
```

sudo mount -t iso9660 /public/*.iso /media/* -o loop

```

Which gives me the following error
```

mount: wrong fs type, bad option, bad superblock on /dev/loop2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

So I did some searching to see if theres anyway to mount a .nrg and I find this
```

# NRG
mount -o loop,offset=307200 imagen.nrg /path/mount_directory

```

I use that and I get an error telling me to specify the filesystem with -t. I try it with iso9660 and I get the same error as before. Is there anything Im missing out of this? Is this an indication that the file might be bad? Id hate to wast a DVD on a small immage (300 megs). Any help would be appreiciated.

---

### Post by CatKiller on 2006-11-11
Maybe the original image wasn't ISO9660. Maybe it was UDF or something.

---

### Post by taurus on 2006-11-11
Or how about mount one file at a time instead of all of them at once!!!

```
sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop <filename>.iso /mnt/iso
```

---

