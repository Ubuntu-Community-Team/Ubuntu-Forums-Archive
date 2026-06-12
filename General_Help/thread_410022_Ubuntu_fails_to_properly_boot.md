---
title: "Ubuntu fails to properly boot"
date: 2007-04-15
forum: General Help
---

### Post by archonon on 2007-04-15
I managed to screw my Ubuntu server installation. Fortunately I was still testing it, but I'd like to recover it, since moving all files and configuring settings takes time...

Problems started when I decided to install unzip from Debian unstable repository. I have previously used Debian repositories without problems but weirdly enough, installing unzip was a mistake. 

So as usual i edited sources.list and uncommented Debian repo, -> apt-get update -> apt-get install unzip. And something went wrong, I don't remember anymore what it said, but after that apt didn't work. Now it only gives an error: 
```
apt-get: error while loading shared libraries: libapt-pkg-libc6.4-6.so.3.51: cannot open shared object file: No such file or directory
```

After failed unzip installation i tried to remove it with dkpg -purge unzip. Well, it didn't help and for some reason after that I booted the system. Not so surprisingly it didn't help. Now it seems Ubuntu always starts in recovery mode. No daemons whatsoever. No, sshd, no httpd, no mysql etc... even if I try to start them manually with /etc/init.d/sshd start, it doesn't even say anything and daemon doesn't start.

Booting goes like this, no matter what i select from Grup.
```

Starting up...
[numbers] PnPBIOS: Unknown tag '0x82', length '25'.
[numbers] PnPBIOS: Unknown tag '0x82', length '25'.
[numbers] piix4_smbus 0000:00:07.3: IBM Laptop detected; this module may corrupt your serial eeprom! refusing to load module!

* Activating swap...  [ ok ]
* Checking root file system...
fsk 1.39 (29-May-2006)
/dev/hda1: clean, 55860/4816896 files, 977910/9626943 blocks   [ ok ]

 * Checking file systems...
fsck 1.39 (29-May-2006)   [ ok ]

Ubuntu 6.10 Citadel tty1

Citadel login: _


```

Thanks for your help :)

---

