---
title: "Dual booter's computing after death of XP"
date: 2013-10-28
forum: General Help
---

### Post by cecilieaux on 2013-10-28
I currently dual boot Ubuntu 12.04 and Windows XP. However, XP dies in April 2014 and to install Windows 7 I have to do a clean install, which would wipe out programs, including some that I don't know where the CDs are. Moreover, every time one installs Windows, it erases grub and access to Linux has to be redone. 

Sooo ... here are a few potential strategies:

1) Ditch Windows, run irreplaceable programs in Wine. I'd love that, but I have problems with some of them (posted query in Wine subgroup, we'll see ...)

2) Keep Windows but offline (so it doesn't get viri) and use only Ubuntu for the net.

3) Break down and go through the hassle of Windows 7. (I have done this at work, where Linux is not yet possible.)

Any opinions and/or suggestions? I am a moderately advanced user, not a programmer, not a huge geek.

Thanks in advance! I always get good ideas here.

C

---

### Post by sudodus on 2013-10-28
> **cecilieaux said:**
> I currently dual boot Ubuntu 12.04 and Windows XP. However, XP dies in April 2014 and to install Windows 7 I have to do a clean install, which would wipe out programs, including some that I don't know where the CDs are. Moreover, every time one installs Windows, it erases grub and access to Linux has to be redone. 

Sooo ... here are a few potential strategies:

1) Ditch Windows, run irreplaceable programs in Wine. I'd love that, but I have problems with some of them (posted query in Wine subgroup, we'll see ...) Which programs do you need? There might be alternatives in linux.> 

2) Keep Windows but offline (so it doesn't get viri) and use only Ubuntu for the net.I know several people will do this.> 

3) Break down and go through the hassle of Windows 7. (I have done this at work, where Linux is not yet possible.)

Any opinions and/or suggestions? I am a moderately advanced user, not a programmer, not a huge geek.

Thanks in advance! I always get good ideas here.

C

If your computer has enough horsepower and memory, you can install XP in a virtual machine for example Virtualbox. It works well enough in a 'middle-aged' computer with a dual-core or core2duo CPU and 2 GB RAM. I have such a system in a computer with and AMD Athlon dual core 4400+ CPU. That computer was new in April 2008.

---

### Post by oldfred on 2013-10-28
I had one app in Windows that I really liked, Quicken and had used since DOS, so lots of history. At first the Linux equivalents were not really good enough, but finally I decided just to use Kmymoney. I do not consider it as good as Quicken but now it is good enough.
So some of the change to Linux apps may be just that you are used to the Windows ones. And some Linux apps are just as good or even better but may have  learning curve on change.

---

### Post by mörgæs on 2013-10-28
> **cecilieaux said:**
> 
2) Keep Windows but offline (so it doesn't get viri) and use only Ubuntu for the net.


It's difficult to know when and how Windows communicates with rest of the world. In Buntu you can control which daemons are active, but services in Windows are a different matter. As posted above I would recommend to keep XP in a virtual environment, if you really need Windows applications.

---

### Post by cecilieaux on 2013-10-28
> **sudodus said:**
> Which programs do you need? There might be alternatives in linux.I know several people will do this.

If your computer has enough horsepower and memory, you can install XP in a virtual machine for example Virtualbox. It works well enough in a 'middle-aged' computer with a dual-core or core2duo CPU and 2 GB RAM. I have such a system in a computer with and AMD Athlon dual core 4400+ CPU. That computer was new in April 2008.

The programs I would really like to be able to use are Corel Ventura 10 (and no, Scribus doesn't come close), WordPerfect Office (I have the version 8 for linux but there are libraries missing or something and it doesn't install) and for fun Civilization II (FreeCiv doesn't quite do the trick).

 I have 4GB RAM dual core, but I can't get Virtualbox to load right in Ubuntu.

The error I get is: 

> "Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary."

---

### Post by cecilieaux on 2013-10-28
> **mörgæs said:**
> It's difficult to know when and how Windows communicates with rest of the world. In Buntu you can control which daemons are active, but services in Windows are a different matter. As posted above I would recommend to keep XP in a virtual environment, if you really need Windows applications.

This is an interesting observation. I could, since I'm using a USB wireless adapter, simply unplug the thing physically. I don't think even Windows can beat no physical connection.

---

### Post by Habitual on 2013-10-28
> **cecilieaux said:**
> XP dies in April 2014

Support may end but the OS certainly won't "quit working".

---

### Post by sudodus on 2013-10-28
> **cecilieaux said:**
> The programs I would really like to be able to use are Corel Ventura 10 (and no, Scribus doesn't come close), WordPerfect Office (I have the version 8 for linux but there are libraries missing or something and it doesn't install) and for fun Civilization II (FreeCiv doesn't quite do the trick).

 I have 4GB RAM dual core, but I can't get Virtualbox to load right in Ubuntu.

The error I get is:

Well, I think you want to continue running XP. And yes, unplugging the USB wifi device would be safe as long as you remember it ;-) So dual boot can be OK.

It might work better to run the VirtualBox version, that is downloaded directly from Oracle. There is also the alternative to use KVM-qemu according to these links, provided that you can activate virtualization extensions (Intel VT or AMD-V) in your computer.

[https://help.ubuntu.com/community/KVM/VirtManager](https://help.ubuntu.com/community/KVM/VirtManager)

[http://www.linux-kvm.org/page/Main_Page](http://www.linux-kvm.org/page/Main_Page)

---

### Post by cecilieaux on 2013-10-28
But won't the hordes of hackers come blow up my computer?

---

### Post by sudodus on 2013-10-29
> **cecilieaux said:**
> But won't the hordes of hackers come blow up my computer?

???

Do you mean when running Ubuntu or Windows?

See this link [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by geoaraujo on 2013-10-29
To solve 

> "Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or  there is a permission problem with /dev/vboxdrv. Please reinstall the  kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the  DKMS package first. This package keeps track of Linux kernel changes  and recompiles the vboxdrv kernel module if necessary."

Open a terminal and enter ```
sudo /etc/init.d/vdboxdrv setup
```
This should work...

---

### Post by mastablasta on 2013-10-29
> **cecilieaux said:**
> But won't the hordes of hackers come blow up my computer?

yes. and it will implode when they pull the plug :-D

BTW you can just install firewall and turn off network access. unless you still want LAN access then it will be a bit more complicated but still it'd doable...

---

### Post by Lars Noodén on 2013-10-29
ReactOS is still in the alpha stage.  If they make some decent progress by next spring then it might be an option.  I'm not holding my breath though.

---

