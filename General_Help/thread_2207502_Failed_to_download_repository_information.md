---
title: "Failed to download repository information?"
date: 2014-02-23
forum: General Help
---

### Post by andreadixon825 on 2014-02-23
Hi eveytime I try to update or it looks for updates it say this, here is a copy for my error details, its been doing this for like 2 months, And I been geting errors to when I tune on the computer, and error when trying to shutdown it will not let me so I have to press the restart button on my desktop. Sorry if i posted this in the worrng topice I could not find a xubuntu fourm. thanks.

Error Details. Oh and I have the cd in and it still says this.

W:Failed to fetch cdrom://Xubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016)/dists/saucy/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Xubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016)/dists/saucy/multiverse/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Xubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016)/dists/saucy/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Xubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016)/dists/saucy/universe/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Xubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016)/dists/saucy/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Xubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016)/dists/saucy/multiverse/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Xubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016)/dists/saucy/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Xubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016)/dists/saucy/universe/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Thanks.

Andrea Dixon

---

### Post by llamabr on 2014-02-23
please copy the output of:

```
cat /etc/apt/sources.list
```

---

### Post by sammiev on 2014-02-23
Easy fix, see the pic attached and unchecked the first line with CDROM.

---

### Post by andreadixon825 on 2014-02-23
Thanks sammiev I did just what you said and now it updates now thanks.:p

---

### Post by sammiev on 2014-02-23
Thanks for reporting back and marking this thread as solved. Glad I was able to help. :p

---

