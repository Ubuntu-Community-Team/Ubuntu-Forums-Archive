---
title: "minimizing installation clutter"
date: 2008-04-23
forum: General Help
---

### Post by screwballl on 2008-04-23
One area that has gotten worse with most linux distros is the inclusion of all the extra junk that has slowed down the installation and OS performance. The extra junk like SCSI drivers, server hardware drivers, PCMCIA drivers (when installing on a desktop), and so on. Laptops and desktops only need the IDE/ATA and SATA based drivers loaded. It would be much easier if there was an interactive installation and loading phase, for example: "hda not found on IDE or SATA channels, load SCSI driver? Y/N".... or even a simple "Choose the system this is being installed on: Laptop, desktop, server" so that only the server choice will load a SCSI driver, and only the laptop would load a PCMCIA driver...

Is anyone working on a reduced clutter version of ubuntu or any variants? 

I know most of the builds are really geared towards servers so any actual bugs found on desktop/laptop installations are only taken seriously if it also pertains to a server environment. This is slowly turning into the equivalent of a Micro$oft bloatware installation event with hundreds of extra resources and drivers that are being loaded but is not needed or used.
I know there are minimal distros out there but where they skimp on the software, they also skimp on the hardware compatibility.
We need a "probe" to catch what hardware is present and only load drivers relating to the hardware present, and if it unable to find a specific driver, ask the user to load one after the OS install. Then if new hardware is introduced once the OS is installed, restart the PC and upon startup the probe finds the new hardware and installs the needed drivers for that. This helps prevent all the extras junk and clutter from poisoning our OS as has been seen recently.

---

### Post by ryanhaigh on 2008-04-24
As far as I know driver modules are only loaded when the hardware is detected. SCSI is a tricky one because some types of drives are treated as scsi to make things easier. The options you are talking about are kernel compilation options. You could always recompile the kernel yourself taking out what you don't need but remember that ubuntu (and even more so debian) is installed on a WIDE range of hardware and just because yours and mine don't have high end raid cards, real scsi drives or whatever obscure device does not mean that the guy down the road doesn't.

---

### Post by screwballl on 2008-04-25
Look at any normal Ubuntu installation and startup log... it tries to load pcmcia drivers, SCSI drivers and all sorts of other hardware items that are not present in at least 90% of desktop computers that this is installed on. Also a stripped down version for laptops that removes the desktop or server only items would help people specify what they are using it for and help the developers see some real world stats on who is downloading what and which version is being reported with more problems.

---

### Post by ebelog on 2008-04-25
There is a trade-off between ease of use and what you consider to be installation clutter. In order to keep things as easy to use as possible and to cut down on the number of questions during the install, some extra drivers and packages are installed. I think that's a conscious decision on the part of Ubuntu developers, because it makes for a simpler install, and it's better able to deal with hardware changes. If you are interested in digging in and creating a small footprint install for your specific hardware, that opportunity is there for you with a customized installation or a different distribution. Not every user knows or cares whether they have SCSI or SATA or IDE drives, PCI or PCMCI cards, and asking people to answer such hardware questions during an install would keep many from even trying out Linux.

---

### Post by screwballl on 2008-04-25
Thats part of the problem... most of the actual developers for most linux distros only care about server based setups and if their fix also fixes a desktop then great... otherwise a majority of the issues with a given system remains unfixed until another completely different distro is tried. 
For example on my main desktop system, the only linux dirsto out of the 10 that I have tried that actually works and works well is Fedora. Ubuntu gives strange PCMCIA panic errors. Other distros come up with SCSI load boot failed since it uses SATA hard drives.
With all the extra clutter bundled into these install packages, I have run into a good deal of systems that the install process mis-identifies some hardware and refuses to let it install or boot properly, many times refuses to even give a CLI to attempt to fix it.
Removing the extra clutter and minimizing the builds to specific desktop, laptop and server based build will help identify the problem areas.

---

