---
title: "adept crashes after installing wine"
date: 2007-04-24
forum: General Help
---

### Post by Himitsu on 2007-04-24
After using [this post]("http://doc.gwos.org/index.php/Wine_AMD64") to install wine on my amd64 box, I can no longer run adept. I get the following error if  I do it in a shell.

```
himitsu@amd64:~$ kdesu adept_manager
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kapture::PkgSystem::PkgSystem()

vmware-player-kernel-modules

ia32-libs

ia32-libs-gtk

libc6-i386

libssl0.9.7

debconf

vmware-player-kernel-modules

ia32-libs

ia32-libs-gtk

libc6-i386

libssl0.9.7

debconf

kdecore (KProcess): WARNING: _attachPty() 34
kapture::PkgSystem::CreatePM()
KCrash: Application 'adept_manager' crashing...
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

drkonqi: cannot connect to X server :0.0

```

Anobody have any idea what is wrong or what I did to jack up adept? I have the feeling that I broke something by installing all of those 32 bit libraries.

I really don't want to reinstall since aside from this problem, I really like kubuntu and the way it runs.

---

### Post by zvacet on 2007-04-24
I don´t know wich version of  Ubuntu you use,but this is all I found
[http://ubuntuforums.org/showthread.php?t=185557&highlight=wine+64]("http://ubuntuforums.org/showthread.php?t=185557&highlight=wine+64")

---

### Post by Himitsu on 2007-04-25
Weird, it somehow fixed itself. I didn't change anything, except I left it alone and went to work and when I came back was ready to reinstall Kubuntu. On a whim I tried to do an update and it worked.

---

