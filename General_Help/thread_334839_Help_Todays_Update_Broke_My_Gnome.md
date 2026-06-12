---
title: "Help Todays Update Broke My Gnome"
date: 2007-01-09
forum: General Help
---

### Post by fokuslee on 2007-01-09
Help I updated the security update today some thing about X core if i remember correctly
now i have the GUI login prompt still then after i log in nothing happens 
nautillas did not load neither did gnome menubars (panel) and desktop nothing loaded 
it was just a blank screen with solid color background

Reinstalling and removing both beryl and nvidia-glx did not help me

i am able to login to gnome fail-safe 
it does not run any startup scripts (maybe thats where it goes wrong how do i check this? fix this? )
Also i get this pop up error
There was an error starting the GNOME Settings Daemon.
Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

any ideas?
SOLVED problem was caused by gDesklets
dpkg-reconfigure gnome-applets fix it temporarily had to reinstall

---

### Post by mega on 2007-01-09
Same here, gdm starts, but I cant get into the desktop

tried failsafe, that did not work either

I have the default set to auto load beryl, not sure what the problem is yet

---

### Post by mega on 2007-01-09
Ok, my xorg.0.log.old shows this

Backtrace:
0: /usr/bin/X.schedreal(xf86SigHandler+0x81) [0x80c3971]
1: [-xffffe420]

fatal server error:
Caught signal 11. server aborting

---

### Post by ato on 2007-01-09
I solve reinstalling NVIDIA drivers

---

### Post by mega on 2007-01-09
weird, my nvidia splash screen comes up, and gdm starts fine

I cant reinstall nvidia drivers, I tried, but the update also installed a new kernel, without linux-restricted-moudles-2.6.17-10-generic, it says its' being kept back

linux installer fails because of missing module source folders

seems I cant win today

---

### Post by mega on 2007-01-09
removing beryl fixed mine

but no pretty desktop now

---

### Post by fokuslee on 2007-01-09
i remedied with adduser just created another user but yeah everthing back to default and i still can't get back to my normal login, i don't no why removing beryl help u i made a seperate session for beryl and even when i log in using the default metacity i still get the samething.   edgy is not that good to me im thinking of going back to dapper
: (

---

### Post by _simon_ on 2007-01-09
> **ato said:**
> I solve reinstalling NVIDIA drivers

Ditto.

Reinstalling your graphics drivers solves the problem.

---

### Post by fokuslee on 2007-01-09
Reinstalling does not work for me, removing beryl does not work either
i am able to login to gnome fail-safe 
it does not run any startup scripts (maybe thats where it goes wrong how do i check this? )
Also i get this pop up error
There was an error starting the GNOME Settings Daemon.
any ideas?

---

### Post by emperon on 2007-01-10
I got the same problem. Installing NVIDIA fixed the issue.

---

### Post by mega on 2007-01-10
I cant install nvidia because part of the kernel is being held back for some reason

it wont let me dist-upgrade and get the kernel modules, so I'm stuck until it's resolved

---

### Post by mahiyar on 2007-01-10
When i got today's install list it included NVidia's glx driver for update, could u all be having beta drivers of NVidia?

The instruction also told about mod probing NVidia drivers using the -i option.

---

### Post by mega on 2007-01-10
I use the beta driver so composting works without xgl

but I cant install it until the kernel modules is released, it's being held back for some reason, it's too bad it does not say why it's being held back

---

### Post by mahiyar on 2007-01-10
Try enabling the driver using "sudo nvidia-glx-config enable"

---

### Post by mega on 2007-01-10
driver is enabled, I get the splash screen

I cant recompile the driver until the kernel-modules is no longer held back

I'm not alone, there's a thread going on the beryl forum now too

---

### Post by currentshades on 2007-01-10
> **mega said:**
> driver is enabled, I get the splash screen

I cant recompile the driver until the kernel-modules is no longer held back

I'm not alone, there's a thread going on the beryl forum now too

something goofy is going on with the kernel for me as well.  I'm getting this error when trying to install NVIDIA.

"unable to determine the nvidia kernel module filename"

---

### Post by umattu on 2007-01-11
chaeck this thread
[http://www.ubuntuforums.org/showthread.php?t=335080&highlight=nvidia-kernel](http://www.ubuntuforums.org/showthread.php?t=335080&highlight=nvidia-kernel)

---

### Post by emperon on 2007-01-11
can someone figured out why this has happened to some minority of users ?

What we have in common ?

I am using nvidia binary (from nvidia website) with 2.6.19.1 custom compiled kernel

---

### Post by rahulthewall3000 on 2007-01-12
Hi!

None of my gnome-applets are working, I checked the Synaptic Package Manager and my gnome-applets are not installed. When I tried to install them, it said that the repositories are not enabled. I am posting my sources list here, and as I used the Internet to generate it automatically, I think there are a lot of problems with it, but I don't know what they are.

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy main restricted
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy universe multiverse
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) edgy-seveas all

deb-src [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) edgy-seveas all

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

# Upstream Wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

# Upstream Beryl
# GPG key: ed8a569e
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main-edgy

deb-src [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free

deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free

# Canonical Commercial packages
# GPG key: 437D05B5
deb [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb-src [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main

Please help urgently, I am having a hell lot of problems.

---

### Post by currentshades on 2007-01-12
Perhaps a reinstallation will help at this point considering the numerous system files that are having problems.  I think part of the problem is a customized font-rendering that I used in conjunction with a repository that installed some files for the linux-header...

---

### Post by balloons on 2007-01-12
take a look at this..

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

btw, this problem WILL be fixed in fiesty, so you don't go to a black screen when things break like that. A word of caution, if you use nvidia's binary drivers, there can/will be problems. That's why we want open source drivers - they aren't tied to a specific kernel, or module and won't break when you update.

EDIT: there's also this

nvidia-xconfig

---

### Post by currentshades on 2007-01-12
Thank you for the reply, guitara.  It brings much hope for me!  ^_^  I'll surely make use of the website.

---

### Post by Wingless on 2007-01-22
Hi I've been having the same problem described in the very first post, and I tried reinstalling the nvidia drivers and nothing changed.

I just wanted to know if someone knew the why of this problem, and another possible solution.

Thanks

---

### Post by jocksontour on 2007-02-21
Can anyone tell me in simple text how to reinstall the NIVIDA drivers? I have this same problem and no matter how many reboots I try, it just keeps on coming back.

Cheers.:confused:

---

