---
title: "open zip files"
date: 2008-01-21
forum: General Help
---

### Post by davehenton on 2008-01-21
Hi. anyone out in the big wide world who can please help me.I have installed Ubuntu 7.10. on a new motherboard "Asrock 939nf6g-vsta" but the problem is it takes about 4mins. to get to the Ubuntu boot. I want to update the bois . I can download the updates but they come as a zip file. my problem is I don't know how to open and and install a zip file.any help would be much appreciated

---

### Post by njparton on 2008-01-21
"gunzip" will unzip them for you I think.

Try:

```
sudo apt-get install gunzip
```

You'll need to create a bootable floppy and then stick the unzipped files on there.  Reboot from floppy.

---

### Post by renzokuken on 2008-01-21
don't even have to do that. you can just right click on the file (in Gnome) and select "Extract Here"

---

### Post by njparton on 2008-01-21
Aha, gunzip must be included with gnome...

---

### Post by oldos2er on 2008-01-21
> **njparton said:**
> Aha, gunzip must be included with gnome...

 No, gunzip is a CLI tool located in /bin

---

