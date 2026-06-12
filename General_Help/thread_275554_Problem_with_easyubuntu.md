---
title: "Problem with easyubuntu"
date: 2006-10-11
forum: General Help
---

### Post by Echo35 on 2006-10-11
I tried using easyubuntu to do a new setup, but ran into a strange issue. When I try to install something with it, it returns the error:

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

I tried adding the url to my repository list, but I get the same problem. Does anyone else have this issue? This is on Dapper Drake.

---

### Post by electricshoes on 2006-10-11
After you add to your sources.list, do this.

```
wget http://easyubuntu.cafuego.net/969F3F57.gpg -O - | sudo apt-key add -
```

---

### Post by Echo35 on 2006-10-11
That didn't work either. Got it twice this time:

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

---

### Post by electricshoes on 2006-10-11
Ok, see if this works.

Remove   deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntu
from your sources.list

```
sudo apt-get update
```

download the .deb
[http://easyubuntu.cafuego.net/pool/main/easyubuntu/easyubuntu.deb](http://easyubuntu.cafuego.net/pool/main/easyubuntu/easyubuntu.deb)

then
```
sudo dpkg -i easyubuntu.deb
```

---

### Post by Echo35 on 2006-10-11
That's actually what I did in the first place. I think it has to do with the fact that PLF is shutting down the Ubuntu repositories, and easyubuntu uses PLF. Could this be the case?

EDIT: Worked that time, but it still gave me the error, it just ignored it and worked.

---

### Post by electricshoes on 2006-10-11
yeah it will work without the key, have fun with easyubuntu.

---

### Post by Echo35 on 2006-10-11
Yeah, except my nVidia card STILL doesn't work...

---

### Post by dagnabit dang doohickey on 2006-10-11
This key worked for me:

```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 0x12B83718 ;  gpg --export -a 0x12B83718 | sudo apt-key add -
```

---

### Post by ColinG on 2006-10-11
Re Nvidia driver, I don't think Easy Ubuntu sets up your Xorg.conf file - you have to do it manually. There are several howtos covering the subject.

I personally think Automatix is better. It certainly works for me, including Nvidia.

---

### Post by electricshoes on 2006-10-11
> **Echo35 said:**
> Yeah, except my nVidia card STILL doesn't work...

What does yer xorg.conf look like?
What have you done to install it?

---

### Post by dagnabit dang doohickey on 2006-10-11
This is how easyubuntu handles the nvidia install:

```
<subcat id="nvidia-legacy" arch="x86-amd64" de="gnome-kde">
    <label>Nvidia Legacy: install the official legacy driver to enable 3D on Nvidia graphics cards</label>
    <alert>nonfree</alert>
    <pkg>nvidia-glx-legacy</pkg>
    <pkg>nvidia-kernel-common</pkg>
    <config>nvidia-glx-config enable</config>
</subcat>

<subcat id="nvidia" arch="x86-amd64" de="gnome-kde">
    <label>Nvidia: install the official driver to enable 3D on Nvidia graphics cards</label>
    <alert>nonfree</alert>
    <pkg>nvidia-glx</pkg>
    <pkg>nvidia-kernel-common</pkg>
    <!-- <pkg>nvidia-settings</pkg> -->
    <config>nvidia-glx-config enable</config>
</subcat>

```

It installs two packages:
nvidia-glx (legacy driver: nvidia-glx-legacy)
nvidia-kernel-common

and this config:
nvidia-glx-config enable

You can find this info in the easyubuntu packagelist-dapper.xml file.

---

### Post by Echo35 on 2006-10-12
You are correct, Easyubuntu does not set up your Xorg.conf file. Not that it matters now though. I always heard bad things about Automatix, but decided to give it a shot anyway. Now, I have no idea why people were saying bad things about it. It works beautifully, uninstalls unwanted programs in a breeze, and even set up the Xorg.conf file and made my graphics card work! I'm definately using it in any further dealings with Ubuntu. Works way better than Easyubuntu, that's for sure.

---

