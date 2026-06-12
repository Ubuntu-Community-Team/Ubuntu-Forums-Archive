---
title: "Cannot copy content of .img (I/O error)"
date: 2022-02-21
forum: General Help
---

### Post by gratus2 on 2022-02-21
Hello,

I have a .img file (14,6 MB) with .cue that I want to be able to mount on Windows.

On Windows's side, it only give me an error when trying to mount. So it's why I try to use Ubuntu instead since it's less "narrow minded" OS.

When I try to mount the .img by clicking on it, it appear on "disk" but I can't (or dont know) access to the content.

If I try to mount: 

```

sudo mount -o loop '/home/xxx/Bureau/isocele/xxx.img' /mnt/xxx
mount: /mnt/xxx: wrong fs type, bad option, bad superblock on /dev/loop20, missing codepage or helper program, or other error.
```

If I try to extract with 7zip: "Can not open file as archive".

If I try to convert to iso with ```
iat '/home/xxx.img' '/home/xxx.iso'
``` I can mount and see the content, but I get an Input/Output error for each files. With cp: ```
cp: erreur de lecture dans '/media/xxx': Erreur d'entrée/sortie
```

The .img is pretty old (~2005). I dont know if it can help.

Thank you for any suggestion.

---

### Post by Holger_Gehrke on 2022-02-21
There's a tool named cdemu; it's similar to the DaemonTools on Windows and gives you a virtual CD/DVD drive on which all kinds of unusual image files - including various proprietary / raw image formats -  can be mounted. There should be a PPA for it on launchpad.net.

Holger

---

### Post by yetimon_64 on 2022-02-22
> **Holger_Gehrke said:**
> ...There should be a PPA for it on launchpad.net...
Yes there is...
[[COLOR=#0000ff]https://launchpad.net/~cdemu/+archive/ubuntu/ppa[/COLOR]]("https://launchpad.net/~cdemu/+archive/ubuntu/ppa")

---

### Post by gratus2 on 2022-03-26
I have the same error: I/O error when I try to open a file.

---

