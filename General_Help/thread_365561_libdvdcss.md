---
title: "libdvdcss"
date: 2007-02-19
forum: General Help
---

### Post by Patrick-Ruff on 2007-02-19
hey all, I'm using dapper at the moment and every dvd player I try asks for libdvdcss but I can't find it anywhere on the repositories, anyone know  how I could get it?

thanks

---

### Post by yabbadabbadont on 2007-02-19
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

---

### Post by Patrick-Ruff on 2007-02-19
still didn't work, totem gave me some error about libdvdcss

---

### Post by Maestro23 on 2007-02-19
> **Patrick-Ruff said:**
> still didn't work, totem gave me some error about libdvdcss

Check the Restricted Formats page.  Has a link to get libdvdcss2.

[https://help.ubuntu.com/community/RestrictedFormats#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca](https://help.ubuntu.com/community/RestrictedFormats#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca)

---

### Post by Patrick-Ruff on 2007-02-19
same damn error . . .

---

### Post by Patrick-Ruff on 2007-02-19
is there any failsafe way of playing dvds on ubuntu dapper? or should I just give up and install edgy?

---

### Post by tr333 on 2007-02-19
take a look at [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs), specifically the section on installing libdvdcss2.  you will need to add an extra repository before you can install the libdvdcss2 package.

---

### Post by r4ik on 2007-02-19
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_DVD_playback_capability)

Note "ironss"

Good luck !

---

### Post by Patrick-Ruff on 2007-02-19
that didn't work EITHER. I swear this is more trouble then its worth.

---

### Post by aysiu on 2007-02-19
Paste these two commands in the terminal: ```
wget -c http://medibuntu.sos-sts.com/repo/pool/edgy/free/i386/libdvdcss2_1.2.9-2medibuntu2_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2_i386.deb
```

---

### Post by MeduZa on 2007-02-19
if nothing works, try another dvd disk, this error appear also when the dvd is scratch or damage.

---

### Post by Patrick-Ruff on 2007-02-19
```
patrick@eclypse:~$ sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2_i386.deb
(Reading database ... 78473 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.9-2medibuntu2 (using libdvdcss2_1.2.9-2medibuntu2_i386.deb) ...
Unpacking replacement libdvdcss2 ...
dpkg: dependency problems prevent configuration of libdvdcss2:
 libdvdcss2 depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
dpkg: error processing libdvdcss2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libdvdcss2
```

...anything else?

---

### Post by Patrick-Ruff on 2007-02-19
that's an invalid suggestion meduzu, I've played this dvd disc several times on ubuntu.

---

### Post by aysiu on 2007-02-19
What version of Ubuntu are you using? Dapper? Edgy?

I was trying to give you the easy way, but I don't know if you're using 6.06 or 6.10 or whatnot. I also don't know if you're using i386, AMD64, or PowerPC.

Follw these instructions for adding the right repositories--it's a bit more complicated, but you won't run into dependency problems:
[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

---

### Post by Patrick-Ruff on 2007-02-19
I stated in the first post that I'm using dapper.

---

### Post by aysiu on 2007-02-19
Then follow the instructions for adding the Dapper repository: ```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo wget http://medibuntu.sos-sts.com/sources.list.d/dapper.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get install libdvdcss2
```

---

### Post by Patrick-Ruff on 2007-02-19
see, here's the thing: libdvdcss2 is installed, but all my video players claim that it isn't.

---

### Post by Beuntje on 2007-02-20
> **Patrick-Ruff said:**
> see, here's the thing: libdvdcss2 is installed, but all my video players claim that it isn't.

have you tried to install the package totem-xine? It solved the issue on my pc to not be able to play DVD movies.
and off cause don't forget the firefox plugin to play WMV files from Internet :)

---

