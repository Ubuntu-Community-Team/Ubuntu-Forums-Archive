---
title: "&quot;The update information is outdated.&quot;"
date: 2013-10-16
forum: General Help
---

### Post by Jorge_Gonzalez on 2013-10-16
This keeps popping up, so I went to the terminal and typed ```
sudo apt-get update
``` and everything seemed fine except these:
```
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring Release.gpgIgn cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring Release
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main Translation-en_US
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main Translation-en
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted Translation-en_US
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted Translation-en
```

and 

```
Err http://ppa.launchpad.net raring/main amd64 Packages  404  Not Found
Err http://ppa.launchpad.net raring/main i386 Packages
  404  Not Found
```

and 

```
W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/raring/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

I'm fairy new to Ubuntu, and to be honest, I don't know what half of these things are. Can someone be of assistance?

---

### Post by Frogs Hair on 2013-10-16
There doesn't appear to be any 13.04  packages for the deluge PPA in the terminal output . Open Software & Updates  and remove the source from the Other Software tab. Run the following command after doing so and post the output if there is a problem. ```
sudo apt-get update

```
[https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

---

### Post by deadflowr on 2013-10-16
You can also uncheck anything for cdrom in the software and updates.
I think those are in "other software" as well, but might be in "Ubuntu software" section
That would clear up half the errors.

---

