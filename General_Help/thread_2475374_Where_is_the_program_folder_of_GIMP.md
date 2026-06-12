---
title: "Where is the program folder of GIMP ?"
date: 2022-05-25
forum: General Help
---

### Post by satimis on 2022-05-25
Hi all,

Where is GIMP program folder on Ubuntu 20.04 ?

I need to install GMIC, GIMP plugin

GMIC
[https://gmic.eu/](https://gmic.eu/)

GIMP version 2.10.18

$ apt policy gmic```

gmic:
  Installed: (none)
  Candidate: 2.4.5-1.1
  Version table:
     2.4.5-1.1 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages

```

$ apt policy gmip-gmic```

satimis@PCIeSSD1T:~$ apt policy gimp-gmic
gimp-gmic:
  Installed: (none)
  Candidate: 2.4.5-1.1
  Version table:
     2.4.5-1.1 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages

```

They are repo

Where is GIMP program file?

I need to install GMIC on the plugin folder of GIMP 

Please advise.  Thanks

Regards

---

### Post by Impavidus on 2022-05-25
According to the file list of gimp-gmic, it will install the plugin in /usr/lib/gimp/2.0/plug-ins/. But you don't need to know. Just install the package and it happens automatically.
[https://packages.ubuntu.com/focal/gimp-gmic](https://packages.ubuntu.com/focal/gimp-gmic)

---

### Post by satimis on 2022-05-25
> **Impavidus said:**
> According to the file list of gimp-gmic, it will install the plugin in /usr/lib/gimp/2.0/plug-ins/. But you don't need to know. Just install the package and it happens automatically.
[https://packages.ubuntu.com/focal/gimp-gmic](https://packages.ubuntu.com/focal/gimp-gmic)

Thanks for your advice.

Whether just run following command on Terminal
```

$ sudo apt install gmic gimp-gmic

```

GMIC will be automatically installed on the Plug-in folder of GIMP ?

Thanks

Regards

---

### Post by ActionParsnip on 2022-05-25
[https://linuxhint.com/gmic-pre-image-processing-plugin-gimp/](https://linuxhint.com/gmic-pre-image-processing-plugin-gimp/)

---

### Post by satimis on 2022-05-25
> **ActionParsnip said:**
> [https://linuxhint.com/gmic-pre-image-processing-plugin-gimp/](https://linuxhint.com/gmic-pre-image-processing-plugin-gimp/)
Thanks for your link.

GIMP is already running

Performed following steps
```

sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt update
sudo apt install gimp-gmic

```

Installation went throught without complaint.  After finished start GIMP

-> Filters
G'MIC-Qt..
grey out

How to fix it?

Edit
==
I have to open an image then G'MIC-Qt.. not grey out

Regards

---

