---
title: "Add/Remove and Synaptic broken"
date: 2008-04-30
forum: General Help
---

### Post by Yoguess on 2008-04-30
I get this error now, I was trying to install picasa and some other apps earlier then did a restart

"E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."

help me fix this

---

### Post by jimv on 2008-04-30
Open a terminal and type:

sudo rm /etc/apt/sources.list.d/medibuntu.list

then

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

(You might need to replace the word "gusty" in that line with whatever version of Ubuntu you are using.)

---

### Post by forestpixie on 2008-04-30
Made an assumption that you have Hardy - open the file to edit it and delete contents, save and close. Then run the 2 commands from the terminal

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```If you aren't running Hardy get the correct repo from here
[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by Yoguess on 2008-04-30
Thank you guys that fixed the problem

another problem i've been having after the install was when i do reload in synaptic it reloads most of the repos but then i get the error at the end

"Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead."

---

### Post by forestpixie on 2008-04-30
Open software sources in System > Admin menu - untick cdrom box - close and it will want to reload.

If there's still a problem psot back.

---

### Post by Yoguess on 2008-04-30
ignore the last request, i unchecked cdrom box in repo and the error stopped

now off to get my dual screen working with ATI card

---

