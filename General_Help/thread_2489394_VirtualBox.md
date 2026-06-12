---
title: "VirtualBox"
date: 2023-07-28
forum: General Help
---

### Post by grey1beard on 2023-07-28
I'm trying to install Win 10 in a virtualbox to run a Gazelle digital cutter.
Clicking on the 'Start' button at the end of setting up the VirtualBox, I get the following error window - 

> Failed to open a session for the virtual machine GazelleCutter.

VT-x is disabled in the BIOS for all CPU modes (VERR_VMX_MSR_ALL_VMX_DISABLED).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: ConsoleWrap
Interface: IConsole {872da645-4a9b-1727-bee2-5585105b9eed}

Grateful for advice on how to solve this.
John

---

### Post by ian-weisser on 2023-07-28
Reboot.

Go into your host machine's BIOS before the OS loads.

Enable VT-x in your machine's BIOS. It's a BIOS setting, not an OS setting.

---

### Post by ajgreeny on 2023-07-28
You need to go to the host's BIO/UEFI settings and make sure that the virtualisation setting for VT-x is enabled; at present according to that error message it is disabled.

You may need to search around in the BIOS/UEFI settings to find the VT-x setting and I believe some call it by a different name so if you have a problem finding it come back here and tell us what you can see.

---

### Post by grey1beard on 2023-07-28
Thanks both. 
Giving it a go now.

---

### Post by grey1beard on 2023-07-28
I went round three times, but couldn't find a likely candidate. I thought it might be helpful to attach these two shots, one from the hp support pages, and a shot of my screen with the Storage/Boot Order open[ATTACH=CONFIG]292519[/ATTACH][ATTACH=CONFIG]292520[/ATTACH]

I'm running 22.04 in an hp prodesk sff .

---

### Post by SeijiSensei on 2023-07-28
It won't likely be in the boot menu. Find the menu for system-level customizations.

---

### Post by grey1beard on 2023-07-28
**> menu for system-level customizations. **
I've tried looking for it, also googled the hp pages, but to no avail.

Grateful for further help in finding this.
John

---

### Post by Morbius1 on 2023-07-28
All I can offer is where it is on my system:

BIOS  > Advanced Mode > Advanced > Intel VT-x Technology ( Supported ) > Intel VMX Virtualization Technology > Change to ENABLE

---

### Post by grey1beard on 2023-07-28
Thanks Morbius, but **Bios > Advanced Mode** doesn't show a second Advanced option.
However, I googled **does hp prodesk support Intel VT-x Technology**, and though it didn't mention my pc by name, it did give me the clue to look in 'Security' and I found the switch to enable it !

---

### Post by #&amp;thj^% on 2023-07-28
What type computer??
Can you show us this please:
```
inxi -SM
```

---

### Post by grey1beard on 2023-07-28
Tried again, having just enabled the VT-x choice as above, but got a slightly different error message - 

> Failed to open a session for the virtual machine Gazelle.

The VM session was aborted.

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: SessionMachine
Interface: ISession {c0447716-ff5a-4795-b57a-ecd5fffa18a4}

---

### Post by #&amp;thj^% on 2023-07-28
Is this installed?
```
dpkg -l | grep virtualbox-dkms
ii  virtualbox-dkms                                             7.0.6-1kaisen                          amd64        x86 virtualization solution - kernel module sources for dkms

```
Some have better luck with good old DKMs,
If you end up installing DKMS you need to run: 
```
sudo /sbin/vboxconfig 
```
EDIT Is the Guest addition installed

---

### Post by grey1beard on 2023-07-28
Had to install inxi, so -
> System:
  Host: john-HP-ProDesk-600-G1-SFF Kernel: 5.19.0-50-generic x86_64 bits: 64
    Desktop: GNOME 42.9 Distro: Ubuntu 22.04.2 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop System: Hewlett-Packard product: HP ProDesk 600 G1 SFF v: N/A
    serial: <superuser required>
  Mobo: Hewlett-Packard model: 18E7 serial: <superuser required>
    UEFI: Hewlett-Packard v: L01 v02.21 date: 12/17/2013

---

### Post by #&amp;thj^% on 2023-07-28
> **grey1beard said:**
> Had to install inxi, so -

See my other post.
You found the switch for VT.

---

### Post by grey1beard on 2023-07-28
Sorry, ifallen, we seem to have got out of step !
Just got this -

> $ dpkg -l | grep virtualbox-dkms
ii  virtualbox-dkms                            6.1.38-dfsg-3~ubuntu1.22.04.1           amd64        x86 virtualization solution - kernel module sources for dkms

Do Ii now need to run your **sudo /sbin/vboxconfig** ?

---

### Post by #&amp;thj^% on 2023-07-28
> **grey1beard said:**
> Sorry, ifallen, we seem to have got out of step !
Just got this -



Do Ii now need to run your **sudo /sbin/vboxconfig** ?

No it is installed, This is not a problem that I've seen too often with VirtualBox, but there are instances when an installation will "hiccup". The /sbin/vboxconfig file is just a symbolic link, so you can resolve it yourself if you'd like:

    Open Terminal (if it's not already open)
    Create the symbolic link:
```

    sudo ln -s /usr/lib/virtualbox/postinst-common.sh /sbin/vboxconfig
```

---

### Post by grey1beard on 2023-07-28
Latest attempt -

    > Failed to open a session for the virtual machine gazelle.

The VM session was aborted.

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: SessionMachine
Interface: ISession {c0447716-ff5a-4795-b57a-ecd5fffa18a4}

---

### Post by grey1beard on 2023-07-28
Would it be any simpler trying to install the .iso from the file in my Downloads folder, or would I have the same problem ?

Still, I'm on a learning curve !

---

### Post by #&amp;thj^% on 2023-07-28
> **grey1beard said:**
> Would it be any simpler trying to install the .iso from the file in my Downloads folder, or would I have the same problem ?

Still, I'm on a learning curve !

It's been a few hours now, remind of what .iso your speaking of?
Where are you at this minute with the VB install? Have you yet added "Oracle_VM_VirtualBox_Extension_Pack-7.0.10.vbox-extpack"

---

### Post by grey1beard on 2023-07-28
Windows 10_22H2_English_x32v1.iso is the one I'm trying to install in the Vm.
The Oracle Box, plus the extension have both been installed, 

With help, I shall continue to try and resolve this, but I have also started to look at Gnome Boxes as an alternative.
Any thoughts ? 
I don't have any preconceived choice, only to get the digital cutter working with inkcut in a VM, as it produces weird anomalous behavior in Ubuntu.

---

### Post by #&amp;thj^% on 2023-07-29
Gnome Boxes is another good choice, I'm not sure about Windows though. (I'm not a Windows User)

Maybe you can use LinuxCNC. It's open source: [http://linuxcnc.org/](http://linuxcnc.org/)

LinuxCNC controls CNC machines. It can drive milling machines, lathes, 3D printers, laser cutters, plasma cutters, robot arms, hexapods, and more.
[list]
    [*]Runs under Linux (optionally with realtime extensions).

    [*]Simple installation on Debian and Ubuntu, or via our Live/Install DVD/USB images.

    [*]Accepts G-code input, drives CNC machines in response.

   [*] Active user community.

    [*]Several different GUIs available.

   [*] Compatible with many popular machine control hardware interfaces.

    [*]Supports rigid tapping, cutter compensation, and many other advanced control features.

   [*] Full source code available under the terms of the GNU GPLv2 (General Public License version 2).[/list]

LinuxCNC requires a realtime kernel if it is to be used to control machinery. There are two versions of the package, &#8220;linuxcnc-uspace&#8221; and &#8220;linuxcnc&#8221;

The Debian 10 Buster ISO will install a full Debian system with the required realtime kernel and the linuxcnc-uspace application. It uses a PREEMPT-RT patched kernel which is close to mainstream Linux but does not, in some cases, give quite such good realtime performance as the previous RTAI kernel. It is very often more than good enough. It should probably be the first version tried even if using a parallel port. This is compatible with all Mesa and Pico interface boards.

This one works in Virtual Box

---

### Post by grey1beard on 2023-07-29
Amazing coincidence !
I'm also in the process of building two cnc setups, one for me and one for step-son, both to use Linuxcnc.
I have Debian Buster ISO on a thumb drive, ready to install on both.

I've just managed to set up windows in a Gnome box, and getting the rest of the installation inside is just a matter of time, I hope !

Regards
John

---

### Post by SeijiSensei on 2023-07-29
It's always simplest to install directly from a downloaded ISO image. Create a new machine and point to the ISO when asked for the installation source.

I'll also throw out the option of avoiding VirtualBox entirely and using the built-in VM software in the Linux kernel ("KVM") instead. This piece does a good job of walking you through the steps required to install and use KVM: [https://www.tecmint.com/install-kvm-on-ubuntu/](https://www.tecmint.com/install-kvm-on-ubuntu/)

---

### Post by grey1beard on 2023-07-29
*....getting the rest of the installation inside is just a matter of time, I hope !*

Wherever I search, the instructions seem to be written in mind-numbing gobbledegook.
More later.

---

### Post by #&amp;thj^% on 2023-07-29
> **SeijiSensei said:**
> 
I'll also throw out the option of avoiding VirtualBox entirely and using the built-in VM software in the Linux kernel ("KVM") instead. This piece does a good job of walking you through the steps required to install and use KVM: [https://www.tecmint.com/install-kvm-on-ubuntu/](https://www.tecmint.com/install-kvm-on-ubuntu/)

+1
I just did not want to overwhelm grey1beard with even more information, Virt Manager is always my go to. :)

---

### Post by grey1beard on 2023-07-29
Good people, please accept my thanks for your ongoing help and consideration.
These 84 yo grey cells have been associated with problems electronic for the past 63 years, but I still don't really know what I'm doing !
Success in moving forward has been a matter of luck, built on top of the help I have received from many quarters, especially from this community.
Discovering Ubuntu was the first major advance, then Terminal, as a tool to perform its 'black magic'.
Being a fan maker, an 18th century(mostly) craft, trying to make use of 21st century tools to cover my inadequate skills, first came cnc carving machines, then the Glowforge laser, now trying to get a digital cutter up and running, it's become something of a 'tail-chasing' exercise. 
I live in hope that one day it will all come together.
John

---

### Post by grey1beard on 2023-07-29
[https://www.spice-space.org/download.html](https://www.spice-space.org/download.html) is a good example of what I meant in #24.
It certainly wouldn't win a prize from the 'Plain English Society' !

So far I've tried Flatpak Oracal, Gnome Box, Open-VM, and now KVM. In all cases I ran into stumbling blocks, so rapidly giving up hope.

---

