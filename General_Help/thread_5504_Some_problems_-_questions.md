---
title: "Some problems - questions"
date: 2004-11-19
forum: General Help
---

### Post by FeliceMente on 2004-11-19
Hi! :-)
I installed ubuntu 4.10 3 days ago, and started to tested it a lot... and... I love it! :-)
I love the choices made for it, it's being so clean, without a lot of futile litter installed, etc... I like to look, the hardware found and correctly configured, etc... and, still being Linux, wihout proprietary strange stuff, it's anywat cleany and easy to use... Mac OS X like! :-)

Anyway... I have some little problems... and questions! :-P

1) I have, during the boot process, two error messages about the hotplug system, just before setting the net. They say it can't be started, and, in fact, I found this, with 
dmesg | grep pci:
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
gameport: pci0000:00:0d.1 speed 1242 kHz
ehci_hcd 0000:00:10.3: irq 185, pci mem f8c64000

The strange thing is that my USB Flash Drive perfectly works under ubuntu, and when I connect it it's icon normally appears on the GNOME desktop, and I can normally write and read it's content.

2) I needed to set the PATH enviroment variable for allowing me to use Java from any user and position in the filesystem simply writing 'java', and tried to
add the path to the bin dir inside /etc/profile, but this didn't work, and in fact 'echo $PATH' printed the result without the addition I had made for Java. The Only way of making it work the way I wanted was to add "PATH=$PATH:[java_bin_path]" to
/etc/bash.bashrc.

3) I wanted to remove the intalled Firefox 0.9.3 and install the newest Firefox 1.0. I removed Firefox 0.9.3 package with Synaptic, and this made me remove ubunto Desktop, too. I then installed Firefox 1.0 sungin the installer. Was this a correct procedure? Was ubuntu desktop package important and so I did a bad thing unistalling it?

4) Anyway, I caould correctly set the link on the uper bar for pointing to the new installation of Firefox, and configured GNOME for opening HTML and HTM files using Firefox simply choosing to open a .hmf file using it. I can't anway get it to work with GNOME URL links (they worked with 0.9.3 before unistalling it). How can I configure GNOME so that I can create HTTP URLS as links on my GNOME desktop and have they opened i Firefox?

5) Anyway, Firefox option for opening every new link from external apps inside a new windows doesn't seem to work, and the page are always opened inside the active tab in the last window.

6) I now want to install OPenOffice.org 1.1.3 instead of 1.1.2, using the official installer. Can I just unistall any OpenOffice 1.1.2 package installed with ubuntu, and the normally install OOo 1.1.3 using the installer?

Thanx

---

### Post by TravisNewman on 2004-11-19
1) those errors look like they may be about your SoundBlaster (if you have one installed)
3) Ubuntu desktop is a meta-package that depends on all the Ubuntu desktop packages, including firefox. Since it's a meta package, it doesn't really do anything. The only issue you'll have is if you decide to upgrade to Hoary (the in-development version of Ubuntu). You didn't really need to uninstall the previous version of firefox to install the new one, but there's no harm in it.
4)Computer -> Desktop Prefs -> Preferred Applications. CHange your browser to reflect the change of path.

---

### Post by FeliceMente on 2004-11-20
[QUOTE=panickedthumb]1) those errors look like they may be about your SoundBlaster (if you have one installed)[/QUOTE]
Well, I have a Creative Audigy 2 Platinux eX, and it perfectly seems to work with Ubuntu (I can see all the right audio buses in GNOME mixer).

Anyway, during the boot process, I get something like this:
Starting hotplug subsystem...

and then the two errors:
modprobe: FATAL: error inserting shpchp
operation not permitted

and

modprobe: FATAL: error inserting pciehp
operation not permitted

> Ubuntu desktop is a meta-package that depends on all the Ubuntu desktop packages, including firefox. Since it's a meta package, it doesn't really do anything.
So, what's it's purpose?

> The only issue you'll have is if you decide to upgrade to Hoary (the in-development version of Ubuntu).
What will happen? Will I still be able to upgrade my system? Or what?

> You didn't really need to uninstall the previous version of firefox to install the new one, but there's no harm in it.
Ok, so... no problem doing the same thing, for installing last OpenOffice.org version from the installer, right?

> 4)Computer -> Desktop Prefs -> Preferred Applications. CHange your browser to reflect the change of path.
I'd had already done so, by substituting 'mozilla-firefox %s' with 'firefox %s', but this didn't work, despide I had inserted the path to Firefox into the PATH enviroment variable.
Anyway, changing it to '/usr/bin/firefox/firefox %s' made it work! :-)

Now... I no more have problem 5, too! :-)

The only problems that remain are:
1) The one about the errors during the boot process
2) The question about /etc/profile and /etc/bash.bashrc for setting the PATH enviroment variable,
3) About removing ubuntu_desktop package, and upgrading to the next release of Ubuntu Linux.

Thanx a lot! :-)

---

### Post by TravisNewman on 2004-11-20
as far as the shpchp and pciehp not being found, that happens to almost everyone with no detrimental effect.

ubuntu-desktop, like is said, depends on all the packages to make the desktop work essentially. One example, is that Hoary recently switched to Xorg instead of XFree86. When upgrading ubuntu-desktop, apt noticed the change in dependencies and said "Hey we have to uninstall XFree and install Xorg". Now, if Ubuntu-desktop was not installed, that change wasn't picked up, so people just got the newest version of XFree86 and no xorg.

---

### Post by FeliceMente on 2004-11-20
[QUOTE=panickedthumb]as far as the shpchp and pciehp not being found, that happens to almost everyone with no detrimental effect.[/QUOTE]
Well, but... what should they exactly do?

> ubuntu-desktop, like is said, depends on all the packages to make the desktop work essentially. One example, is that Hoary recently switched to Xorg instead of XFree86. When upgrading ubuntu-desktop, apt noticed the change in dependencies and said "Hey we have to uninstall XFree and install Xorg". Now, if Ubuntu-desktop was not installed, that change wasn't picked up, so people just got the newest version of XFree86 and no xorg.
So, if I want to correctly upgrade when Hoary will be available, and get X.Org in place of XFree, etc... I should have ubuntu_desktop installed, right?

Is there any way I can make this happen, for example creating by myself a ubuntu_desktop package that doesn't depend on Firefox, so that I can correctly upgrade to Hoary when it is available, without outomatically updating Firefox, letting me deal with Firefox, but ubuntu upgrade everything else, etc...?

I know this question can look stupid, but... do I have a way for allowing me to manually deal with some components (Firefox, OpenOffice.org, etc...), but still having the possibility of ugrading to the next Ubuntu release, having the remaining components correctly upgraded?

Thanx

---

### Post by FeliceMente on 2004-11-22
I suppose I'm the only one interested in this stuff... anyway, pciehp is pci express hotplug support, I suppose, but... what's shpchp?
I suppose none of these has to do with USB and FireWire, right?

And, anyway... if they controll things I don't have on my computer, shouldn't they simply 'undestand' this, and not try to get started? I mean, shouldn't their scripts be written so that only if those subsystems are actually present on a machine, the relative modules are started, so that no error message of that kind is given in case those components are not present?

---

### Post by thoms on 2004-11-22
Yeah, I get that exact same error but everything works fine and I wouldn't mind finding out why if anyone knows?

---

### Post by Marauder1 on 2004-11-22
Looks like it has something to do with your hardware !!!
I found this on the net about  your errors.

[http://lists.debian.org/debian-kernel/2004/10/msg00258.html](http://lists.debian.org/debian-kernel/2004/10/msg00258.html)

Something about an Intel pci bridge not being compatible
with kernel 2.6.8.1, check it out.

 :?

---

### Post by FeliceMente on 2004-11-22
[QUOTE=thoms]Yeah, I get that exact same error but everything works fine and I wouldn't mind finding out why if anyone knows?[/QUOTE]
Well, one of the things I love in Ubuntu is that it's so clean, so well integrated, so... two error messages during the boot process do look good...! ;-)

Anyway, does anyone know what do those two modules exactly do?

And, above all, I'm still interested in knowing about upgrading tho Hoary, etc...

Thanx

---

### Post by marcadams on 2004-12-03
Hello all;

I too have the same problem - for both my initial installation of i386 and now the K7 kernel.

The only noticable problems are:
- serious looking messages on boot up
- system seems to pause for 10-15 seconds while moving through two error lines - hence increasing boot time slightly.

Does it actually cause any problems?
Does anybody know how to correct this? Or will we have to live with this until the next kernel??

Many thanks
Marc

---

### Post by FeliceMente on 2004-12-14
The better solution (could someone consider it for the next release) would be to try to start that stuff only in case it is actually present on that machine, not giving and error message and slowing the boot process when the machine can't use those systems.

---

### Post by marcadams on 2005-01-03
Just in case anybody interested, there is a section in the Unofficial Ubuntu guide that shows you how to hide these error messages.

[http://ubuntuguide.org/](http://ubuntuguide.org/)

(Look for the  "modprobe: FATAL: Error inserting" section)

Hope that helps,
Marc

---

