---
title: "How do I mount cramfs image?"
date: 2008-05-14
forum: General Help
---

### Post by kd7lxl on 2008-05-14
I'm trying to mount a cramfs image file. I used this command:
```
sudo mount -t cramfs -o loop /tftpboot/img-dnp9200 /media/cramfs/
```
and got this error:
```
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
dmesg | tail reports:
```
[ 1722.085732] cramfs: wrong magic
```

What do I need to do to mount (or otherwise read) this cramfs image?

---

### Post by anaconda on 2008-05-14
> **kd7lxl said:**
> I'm trying to mount a cramfs image file. I used this command:
```
sudo mount -t cramfs -o loop /tftpboot/img-dnp9200 /media/cramfs/
```
[/CODE]
What do I need to do to mount (or otherwise read) this cramfs image?

Interesting..
I tried your command and successfully mounted my cramfs image..

So. Are you sure the image is a uncorrupted cramfs image? and that you have crmfs support installed?

---

### Post by kd7lxl on 2008-05-14
> **anaconda said:**
> and that you have crmfs support installed?

This is probably my problem. If it's not supported by default 8.04, I don't know what I need to do to add support.

---

### Post by mindwarp on 2010-03-05
To mount a cramfs image in Ubuntu (tested on Karmic)

```

sudo apt-get install cramfsprogs fusecram
mkdir /tmp/image
fusecram /path/to/cramfs_image /tmp/image

```

---

### Post by peertje86 on 2010-11-30
> **mindwarp said:**
> To mount a cramfs image in Ubuntu (tested on Karmic)

```

sudo apt-get install cramfsprogs fusecram
mkdir /tmp/image
fusecram /path/to/cramfs_image /tmp/image

```

I have the same problem. 
I did the thing above.
After opening te image folder
cd image
i get
```
bash: cd: image: Transport endpoint is not connected
```
what does it mean?
after rebooting, the folder is empty.

---

