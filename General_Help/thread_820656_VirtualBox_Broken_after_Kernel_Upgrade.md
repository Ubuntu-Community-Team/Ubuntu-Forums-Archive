---
title: "VirtualBox Broken after Kernel Upgrade"
date: 2008-06-06
forum: General Help
---

### Post by gavinjb on 2008-06-06
Hi,

After the recent Kernel upgrade to 2.6.24-18 VirtualBox will no longer run, the problem is that the VirtualBox-Modules is not available in the repositories yet for this Kernel version.

Can anyone tell me of an easy way to default Ubuntu to boot to kernel 2.6.24-17 as I need VBox on a regular basis I don't want to have to remember to load the right kernel or reboot all the time.

If not does anyone know how to force a rebuild of the VirtualBox-Modules, I did find the following in another post

```

sudo /etc/init.d/vboxdrv setup

```

But all I get is the following message

```

Usage: /etc/init.d/vboxdrv {start|stop|restart|status}

```


Thanks,



Gavin,

---

### Post by nunki on 2008-06-06
try this in the current 18 kernel
```

dpkg-reconfigure virtualbox

```

---

### Post by gavinjb on 2008-06-06
Thanks, but I get the following error

```

Package `virtualbox' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: virtualbox is not installed

```

I know VBox is installed as I can get to the VBox Control Panel, so not sure why it is giving that error

---

### Post by nunki on 2008-06-06
> **gavinjb said:**
> Thanks, but I get the following error

```

Package `virtualbox' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: virtualbox is not installed

```

I know VBox is installed as I can get to the VBox Control Panel, so not sure why it is giving that error

Try
```

dpkg -l |grep "virtualbox"

```
and post the output

---

### Post by forestpixie on 2008-06-06
I keep a copy of the deb I downloaded and just reinstall it when needed.

---

### Post by mannheim on 2008-06-06
How this works depends on whether you:
[LIST=1]
[*]downloaded and installed virtualbox as a deb file from the innotek/sun web site; or
[*]installed virtualbox-ose and friends from the ubuntu repositories.
[/LIST]

If you did the first, then the script /etc/init.d/vboxdrv does have a "setup" option which compiles the kernel module needed by virtualbox. If you did the second, then there is no "setup" option, but the ready-compiled modules can be downloaded instead from the repositories.

Perhaps the virtualbox-modules-2.6.24-18- packages are not yet available from the repositories?

---

### Post by forestpixie on 2008-06-06
I tried the command in the error message which gets you to run the /etc/init.d/vboxdrv bit it wouldn't work this time - it did last time.

Which is why I did a reinstall.

---

### Post by gavinjb on 2008-06-06
Hi Nunki,

I get the following

```

ii  virtualbox-ose                                 1.5.6-dfsg-6ubuntu1                                x86 virtualization solution - binaries
ii  virtualbox-ose-guest-modules-2.6.24-16-generic 24                                                 virtualbox-ose-guest module for linux-image-
ii  virtualbox-ose-modules-2.6.24-17-generic       24.0.1                                             virtualbox-ose module for linux-image-2.6.24

```

I installed via the Repsoitories rather than downloading from the website

Gavin,

---

### Post by ownaginatious on 2008-06-06
I'm having an identical problem. Any solutions yet?

---

### Post by spandanj on 2008-06-07
is there a solution to this problem? do we just wait for the updated Virtualbox-ose-modules-generic compatible with new kernel?

---

### Post by spandanj on 2008-06-07
> **spandanj said:**
> is there a solution to this problem? do we just wait for the updated Virtualbox-ose-modules-generic compatible with new kernel?

i.e. we are waiting for "virtualbox-ose-modules-generic-**2.6.24-18**?" and currently it is **2.6.24-17**. is that the problem?

---

### Post by forestpixie on 2008-06-07
I believe that is the problem yes - but as I use the vbox version not positive.

---

### Post by ownaginatious on 2008-06-08
Hope someone finds a fix soon... really need this for school :p

---

### Post by forestpixie on 2008-06-08
The updated version is available in proposed updates at the moment.

---

### Post by nikopol on 2008-06-08
I'm starting to wonder if the problem isn't deeper than just virtualbox. I borrowed a copy of VMware from a friend to see if it would work on the current kernel. Although windows installed (it won't under virtualbox now - it locks up on the disk format part), when starting it, the disk lock fault occurs making linux unresponsive and needing a hard reboot.

---

### Post by TenPlus1 on 2008-06-08
I opened a ROOT Terminal (dont use sudo) and typed this:

 /etc/init.d/vboxdrv setup

everything worked fine (make sure vbox isnt open)...

---

### Post by knutschr on 2008-06-08
> **TenPlus1 said:**
> I opened a ROOT Terminal (dont use sudo) and typed this:


Why not use sudo?

---

### Post by forestpixie on 2008-06-08
I've had no problem this time with the setup command for vbox - just appeared to be the last kernel (-18) to give vbox a hard time. Of course in addition I'm using the vbox version rather than the one in the repos.

---

### Post by ownaginatious on 2008-06-08
How'd you install virtualbox from outside of the repositories?

---

### Post by forestpixie on 2008-06-08
Donwload the deb - you have to uninstall the repo version first

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

Alternatively - enable the proposed repo and install the newest version of the -ose package and then disable proposed - I wouldn't do the updates with proposed enabled though - you might get a problem.

---

### Post by ownaginatious on 2008-06-08
That's odd. I installed the newest version, 1.6.2, and it worked, but Ubuntu doesn't recognize that it is there. When I try to run it from the terminal, it tells me that virtualbox isn't installed, and gives me the command I should run to install it through the terminal. It's not in the system tools menu either.

I installed it by using the debian installation manager, or whatever it is called. Anyone know why it is doing this?

---

### Post by forestpixie on 2008-06-08
reboot

---

### Post by ownaginatious on 2008-06-08
That might be a good idea :p. Thanks!

---

### Post by knutschr on 2008-06-08
> **forestpixie said:**
> 

Alternatively - enable the proposed repo and install the newest version of the -ose package and then disable proposed - I wouldn't do the updates with proposed enabled though - you might get a problem.

I have the proposed repositories enabled.
I have never had a problem with that.
Only benefits :-)

---

### Post by forestpixie on 2008-06-08
> **knutschr said:**
> I have the proposed repositories enabled.
I have never had a problem with that.
Only benefits :-)

Me as well - usually - but there have been problems. There was a good one last week with openoffice - and the way I see it is that if someone is having problems due to lack of experience chucking proposed into the mix could be problematic.

Which is the reason for the turn it on, turn it off suggestion. 

That said breaking it has helped me to learn more in the last year.

---

### Post by ownaginatious on 2008-06-08
Wewt! Upgrading VirtualBox completely fixed the problem. Thanks to all those that helped.

---

### Post by xolot1 on 2008-06-08
im having this trouble now, but i have an idea.
if you still have your old kernel entries in grub on bootup, select the old version and go from there.
chances are you dont necessarily need the new features of the kernel update, but you should be able to run virtualbox.

im gonna go try that now, cause i need powerpoint, and thats the only place i have it installed...

---

