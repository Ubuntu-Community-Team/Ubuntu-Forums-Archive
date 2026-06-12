---
title: "Strange behavior apt"
date: 2021-05-14
forum: General Help
---

### Post by Acharn on 2021-05-14
For reasons, I installed Groovy Gorilla 20.10 on a flash drive, and was doing the things necessary to use it daily. I have booted up from the flash drive, and the live DVD I installed from is not in the drive. When I tried to install VLC and GIMP from a terminal, I get a message: "Media change: please insert the disc labeled 'Ubuntu 20.10 _Groovy Gorilla_ - Release amd64 (20201022)' .in the drive '/cdrom/' and press [Enter]"

When I do that, I get a series of entries,
Get:1 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) groovy/main amd64 libmspack0 amd64 0.10.1-2 [38.0 kB]
Get:2 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) groovy/universe amd64 cabextract amd64 1.9-3 [23.4 kB]
Get:3 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) groovy/multiverse amd64 ttf-mscorefonts-installer all 3.8ubuntu2 [24.9 kB]
...
 and then it gives me "Media change: please insert the disc labeled 'Ubuntu 20.10 _Groovy Gorilla_ - Release amd64 (20201022)' .in the drive '/cdrom/' and press [Enter]" and I get some more "Get: #"
After "Get:60 [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) groovy/universe amd64 vlc-plugin-visualization amd64 3.0.11.1-2 [36.8 kB]" It just repeated the "Media change:" message. I finally got out of the loop by pressing <Ctl><C>.

Is this a common problem? Should I be reporting a bug? Anybody else see this?

---

### Post by scorp123 on 2021-05-14
> **Acharn said:**
>  Is this a common problem? 
No.

> **Acharn said:**
>  Should I be reporting a bug?  
Not a bug. You'd only get ridiculed. This is a misconfiguration on your part.

> **Acharn said:**
> Anybody else see this?
If I had to bet I'd say you still have the CD-ROM/DVD defined as a software source. Check this file:  **/etc/apt/sources.list**

What it looks like on my system:
```

# deb cdrom:[Ubuntu-Budgie 20.04 LTS _Focal Fossa_ - Release amd64 (20200423)]/ focal main multiverse restricted universe

( ... cut off the rest ...)

```

Chances are in your file that line about *"deb cdrom"* isn't commented out. So your system wants to see the CD-ROM because you told your system it is still a source of packages. That needs to be commented out, e.g. put a "#" in front of the line.

---

### Post by Acharn on 2021-05-15
You nailed it. Thank you.

---

