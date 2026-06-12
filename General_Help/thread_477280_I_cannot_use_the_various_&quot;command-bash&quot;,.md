---
title: "I cannot use the various &quot;command-bash&quot;, (tty1-tty6)"
date: 2007-06-18
forum: General Help
---

### Post by Qu4k3R on 2007-06-18
Sorry if my title is not self-explainable.

I cannot see the tty 2. (The Framebuffer console mode)

I just press Ctrl+Alt+F2 and it does not appear.
Only appears a screen with "scratches" (a broken image).

After that, if I press Ctrl+Alt+F7 it gets back to my usual workspace.

And when I shutdown, or hibernate, the screen becomes the wallpaper but with "bugs" (the same broken image)

When I had Edgy-Eft, it worked perfectly.

I am working on a Feisty Fawn, generic kernel (vmlinuz-2.6.20-16-generic).
I am using beryl, nvidia graphics driver 
My username is "quake":

> 
quake@quake:~$ glxheads 
glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
Name: :0
  Display:     0x805e380
  Window:      0x4000002
  Context:     0x8079050
  GL_VERSION:  2.1.0 NVIDIA 97.55
  GL_VENDOR:   NVIDIA Corporation
  GL_RENDERER: GeForce Go 6800/PCI/SSE2


I am running with the resolution: 1440x900 (widescreen) 60Hz

What do I need to do to make the terminals work?

I would apreciate some help.
Thanks.

---

### Post by mali2297 on 2007-06-18
Hi Qu4k3r,

I share your problem, although I've got an ATI Radeon Mobility X700 card.
Hopefully some friendly soul here will come to our aid.:)

---

### Post by testube_babies on 2007-06-18
Here's what I had to do to get it to work.
Try forcing 1024x768 resolution on the TTY:
```
gksudo gedit /boot/grub/menu.lst
```

Add "vga=791" to the defoptions line as such:
```
# defoptions=quiet splash vga=791
```

Also add it to the kernel line, then reboot:
```
kernel  /boot/vmlinuz-2.6.some_long_name ro quiet splash vga=791
```

Undo these steps if it doesn't work.

---

### Post by Qu4k3R on 2007-06-19
This is my menu.lst file (I removed commented text and other options like default, colors, splashimage) :

> 
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
defoptions=quiet nosplash vga=791

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

title		Ubuntu Linux - Feisty Fawn
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=49e9547a-7ace-4207-8656-34229051bd8e ro quiet nosplash vga=791
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault


I think that is not the resolution.
Thank you anyway, testube_babies.


EDIT:

I am using AIGLX drivers.

---

### Post by mali2297 on 2007-06-21
Unfortunately, the advice didn't help me either.

I'm using the open source "radeon" driver with AIGLX. If I change to tty[1-6], the screen only show a broken image as described in the first post. The image is still broken when I return to the x-session, but I can get it back if I close and reopen the laptop lid.

I don't experience the same problem when I use the 'fglrx' driver without any extras, so maybe the   problem has to do with AIGLX.  But if it stands between the virtual consoles and beryl, I choose the latter. 

I've searched around for help but all I can find are advices like testube_babies'. Perhaps the problem will vanish when Gutsy arrives. :|

---

### Post by mali2297 on 2007-06-21
@Qu4k3R:

I think you should have left the defoptions line commented.
> 
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

It won't make testube_babies' advice work, but you should perhaps put the # back.

---

### Post by Qu4k3R on 2007-06-22
I had already commented the option. Thank you.

I am looking for even more info about this error.
I see only people who adds "vga=791" to menu.lst and then 

> 
sudo update-grub


I have tried it. It does not work either.


PS:

I'll try this:
[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#VESA_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#VESA_video_mode_numbers)

I'll try to change from 791 to another corresponding to VESA framebuffer :s
Let's see if I got those terminals working. (I'll post something)


EDIT:
Does not work

---

### Post by Qu4k3R on 2007-06-23
> **mali2297 said:**
> Unfortunately, the advice didn't help me either.

I'm using the open source "radeon" driver with AIGLX. If I change to tty[1-6], the screen only show a broken image as described in the first post. The image is still broken when I return to the x-session, but I can get it back if I close and reopen the laptop lid.

I don't experience the same problem when I use the 'fglrx' driver without any extras, so maybe the   problem has to do with AIGLX.  But if it stands between the virtual consoles and beryl, I choose the latter. 

I've searched around for help but all I can find are advices like testube_babies'. Perhaps the problem will vanish when Gutsy arrives. :|

When you start your computer, even before login in (I mean, before the session starts up) I cannot use the command lines, and I think that beryl hasn't started up yet.

A funny thing:
I installed warsow :D

I was changing the graphics and the game has frozen up. The screen appeared with only one colour: white.
After this, (the screen does not change) I could change from tty7 to anothers and login to killall warsow :D
funny.

I changed the opengl mode and the screen depth (16 bits).
The bug seems to be not in beryl..

---

### Post by mali2297 on 2007-06-24
I don't quite understand,  did you manage to permanently get tty[1-6] available? If so, what exactly did you do?

Since we use different graphics cards and drivers but have AIGLX in common, that made me suspect that the bug somehow is connected to AIGLX.  As I mentioned earlier, if I install the 'fglrx' driver (which is not compatible with AIGLX) and restart X, then I can use tty[1-6]. 

There is also the possibility that, although the symptom is the same, the cause to our problem is not.

---

### Post by Qu4k3R on 2007-06-24
I was trying to say that beryl was not the source of the bug.
Before I start the session, beryl hasn't started yet. But I cannot access those terminals.

I don't understand why I could access those terminals after the Warsaw "leak".

But after I restart the computer, I could not access the terminals again.
So it was only "accidental" but it worked just perfectly.
I have the bug again. (I don't want to use warsaw to get my terminals avaiable everytime I need them :D)

BTW:
What are the "major" differences between AIGLX and FGLRX drivers?

---

### Post by mali2297 on 2007-06-27
> **Qu4k3R said:**
> 
BTW:
What are the "major" differences between AIGLX and FGLRX drivers?


I have no real knowledge of this. All I understand is that I can choose between two drivers for my ATI card: radeon or fglrx. The first one comes with AIGLX and thus enables me to use beryl.  The fglrx driver provides only 2D display and doesn't support AIGLX, but one should be able use XGL instead for beryl (although I haven't managed to get that working).

I find it strange that nobody else seems to experience  this "bug" with the tty. If anyone reading this thread recognize the problem, make a post.

---

### Post by Qu4k3R on 2007-06-28
Do you have Beryl and compiz installed?

I am using beryl engine with heliodor, but I have also installed compiz and compiz core (and compiz stuff).

btw:
What is your beryl - eyecandy repository ?
My repository file has this for beryl:

> 
# deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy


The first line is commented (i don't use it anymore)

---

### Post by mali2297 on 2007-06-28
My beryl repository is the one you have commented out. I've also got compiz that came with ubuntu by default. However I don't think beryl/compiz are directly responsible (as you concluded yourself). It doesn't matter whether I have the desktop effects on or not. I rather think the bug is in the radeon/AIGLX driver.

---

### Post by Qu4k3R on 2007-06-29
I am installing new drivers for nvidia (hope they have the bug this fixed).

EDIT: It is not working. I had removed compiz ..

**< [COLOR=DarkRed]BIG BUMP[/COLOR] !  >**

quake 

PS: How can we reach the bug and how to find it without losing anything?

I am posting the processes i am actually running.
This might help someone..

> 
quake@quake:~$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
   30 ?        00:00:00 kblockd/0
   31 ?        00:00:00 kacpid
   32 ?        00:00:00 kacpi_notify
  136 ?        00:00:00 kseriod
  157 ?        00:00:00 pdflush
  158 ?        00:00:00 pdflush
  159 ?        00:00:00 kswapd0
  160 ?        00:00:00 aio/0
 1964 ?        00:00:00 ksuspend_usbd
 1965 ?        00:00:00 khubd
 1994 ?        00:00:00 ata/0
 1995 ?        00:00:00 ata_aux
 2001 ?        00:00:00 khpsbpkt
 2105 ?        00:00:00 scsi_eh_0
 2106 ?        00:00:00 scsi_eh_1
 2169 ?        00:00:00 knodemgrd_0
 2225 ?        00:00:00 scsi_eh_2
 2226 ?        00:00:00 scsi_eh_3
 2227 ?        00:00:00 scsi_eh_4
 2393 ?        00:00:00 kjournald
 2593 ?        00:00:00 udevd
 3491 ?        00:00:00 kpsmoused
 3522 ?        00:00:00 ipw2200/0
 3664 ?        00:00:00 hda_codec
 4019 ?        00:00:00 mount.ntfs-3g
 4179 ?        00:00:00 portmap
[b] 4307 tty4     00:00:00 getty
 4308 tty5     00:00:00 getty
 4311 tty2     00:00:00 getty
 4312 tty3     00:00:00 getty
 4313 tty1     00:00:00 getty
 4314 tty6     00:00:00 getty[/b]
 4584 ?        00:00:00 acpid
 4678 ?        00:00:00 syslogd
 4732 ?        00:00:00 dd
 4734 ?        00:00:00 klogd
 4759 ?        00:00:00 dbus-daemon
 4775 ?        00:00:00 hald
 4776 ?        00:00:00 hald-runner
 4782 ?        00:00:00 hald-addon-keyb
 4783 ?        00:00:00 hald-addon-keyb
 4785 ?        00:00:00 hald-addon-cpuf
 4786 ?        00:00:00 hald-addon-acpi
 4787 ?        00:00:00 hald-addon-keyb
 4788 ?        00:00:00 hald-addon-keyb
 4789 ?        00:00:00 hald-addon-keyb
 4799 ?        00:00:00 hald-addon-stor
 4812 ?        00:00:00 dhcdbd
 4827 ?        00:00:00 NetworkManager
 4845 ?        00:00:00 avahi-daemon
 4846 ?        00:00:00 avahi-daemon
 4859 ?        00:00:00 NetworkManagerD
 4874 ?        00:00:00 system-tools-ba
 4875 ?        00:00:00 dbus-daemon
 4925 ?        00:00:00 gdm
 4928 ?        00:00:00 gdm
** 4931 tty7     00:01:14 Xorg**
 4995 ?        00:00:00 cupsd
 5019 ?        00:00:00 hpiod
 5027 ?        00:00:00 python
 5148 ?        00:00:00 MoBlock-nfq.sh
 5216 ?        00:00:00 lockd
 5217 ?        00:00:00 rpciod/0
 5218 ?        00:00:00 nfsd4
 5219 ?        00:00:00 nfsd
 5220 ?        00:00:00 nfsd
 5221 ?        00:00:00 nfsd
 5222 ?        00:00:00 nfsd
 5223 ?        00:00:00 nfsd
 5224 ?        00:00:00 nfsd
 5225 ?        00:00:00 nfsd
 5226 ?        00:00:00 nfsd
 5253 ?        00:00:05 moblock
 5254 ?        00:00:00 rpc.mountd
 5270 ?        00:00:00 kondemand/0
 5276 ?        00:00:00 privoxy
 5296 ?        00:00:00 nmbd
 5298 ?        00:00:00 smbd
 5306 ?        00:00:00 smbd
 5323 ?        00:00:00 sshd
 5335 ?        00:00:03 tor
 5421 ?        00:00:00 rpc.statd
 5431 ?        00:00:00 rpc.idmapd
 5489 ?        00:00:00 atd
 5503 ?        00:00:00 cron
 5651 ?        00:00:00 gnome-session
 5696 ?        00:00:00 ssh-agent
 5699 ?        00:00:00 dbus-launch
 5700 ?        00:00:00 dbus-daemon
 5702 ?        00:00:00 gconfd-2
 5708 ?        00:00:00 gnome-keyring-d
 5710 ?        00:00:00 gnome-settings-
 5723 ?        00:00:00 dhclient
 5730 ?        00:00:00 dhclient3
 5747 ?        00:00:00 sh
 5748 ?        00:00:00 esd
 5757 ?        00:00:00 nautilus
 5759 ?        00:00:01 gnome-panel
 5762 ?        00:00:00 bonobo-activati
 5765 ?        00:00:00 gnome-vfs-daemo
 5766 ?        00:00:00 gnome-volume-ma
 5767 ?        00:00:00 gnome-cups-icon
 5771 ?        00:00:01 rhythmbox
 5773 ?        00:00:00 update-notifier
 5774 ?        00:00:01 beagle-search
 5778 ?        00:00:06 beagled
 5780 ?        00:00:00 nm-applet
 5781 ?        00:00:00 fs.sh
 5784 ?        00:00:01 checkgmail
 5787 ?        00:00:00 firestarter
 5803 ?        00:00:00 gconfd-2
 5805 ?        00:00:00 gnome-power-man
 5808 ?        00:00:00 beryl-manager
 5915 ?        00:00:00 trashapplet
 5952 ?        00:00:05 beryl
 5953 ?        00:00:00 heliodor
 6006 ?        00:00:00 notification-da
 6052 ?        00:00:00 stickynotes_app
 6054 ?        00:00:00 multiload-apple
 6056 ?        00:00:00 cpufreq-applet
 6067 ?        00:00:00 mixer_applet2
 6078 ?        00:00:00 mapping-daemon
 6102 ?        00:00:00 gnome-screensav
 6153 ?        00:00:02 acroread
 6307 ?        00:01:30 firefox-bin
 6334 ?        00:00:32 beagled-helper
 6600 ?        00:00:16 acroread
 7260 ?        00:00:00 gnome-terminal
 7268 ?        00:00:00 gnome-pty-helpe
 7269 pts/0    00:00:00 bash
 7295 pts/0    00:00:00 ps


Excused to say I need help.
PS: I have KDE and Those scripts are usefull

---

