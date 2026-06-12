---
title: "problems with C-Media Sound card."
date: 2007-10-03
forum: General Help
---

### Post by dany_tab on 2007-10-03
hey. i have a computer with amd 3800+ dual core processor, M2N-E asus mother board with an on board sound card HDA NVidia. unfortunatly, i have burned it while trying to build a linking leds electronic circuit. 
month ago i bought a C-Media  PCI CMI8738 sound card, and installed it.
[IMG]http://www.gearxs.com/gearxs/images/8738.jpg[/IMG]
since then i have problens with the sound. the sound card works sometimes and sometimes not, the microphone doesn't work at all, and if i can hear music i can hear only from ubuntu media player and not from sites.
i think the problem is that the soundcard is'nt default.   
that you suggest me to do??? 
please help!

---

### Post by dany_tab on 2007-10-04
help anyone?

---

### Post by jokersmild on 2007-10-04
I have this exact same card and I am having the exact same problem that you are having.
I can't seem to find a solution...so I'll just comiserate with you

---

### Post by geraldm on 2007-10-04
Try  
[http://www.alsa-project.org/main/index.php/Matrix:Module-cmipci](http://www.alsa-project.org/main/index.php/Matrix:Module-cmipci)

Gerald

---

### Post by dany_tab on 2007-10-05
i have downloaded the driver to the desktop from alsa and here are the installation instructions:
```
Quick install
=============

1) You must have full configured source for the Linux kernel which you
   want to use for the ALSA drivers. Note that ALSA drivers are part
   of the kernel, so there is necessary to resolve all symbol dependencies
   between the used kernel and ALSA driver code. Partly installed kernels
   (for example from distributor makers) can be unuseable for this action.

2) You must turn on sound support (soundcore module).

3) Run './configure' script.

 * General Options
   If you do not want ISA PnP support, use --with-isapnp=no switch.
   If you do not want sequencer support, use --with-sequencer=no switch.
   If you do not want OSS/Free emulation, use --with-oss=no switch.
   If you have udev or devfs and want to use more than eight cards, use
   --enable-dynamic-minors switch.
   If you want to turn on debug mode, use --with-debug=full switch.
   If you want to debug soundcard detection, try --with-debug=detect switch.

 * Kernel Source Tree
   On 2.4/2.6 kernels, the location of the kernel source tree is
   parsed automatilly from the running kernel.
   If it's not in the standard place, specify the path via
   --with-kernel=<kernel_directory>. 
   On 2.6 kernels, the build directory has to be given via
   --with-build=<kernel_build_dir> option additionally, too.

 * Drivers to Compile
   The card drivers to be compiled can be selected via --with-cards option.
   Pass the card driver name without "snd-" prefix.  To specify
   multiple drivers, list names with comma (,).
   Passing "all" will compile all possible drivers (and this is the
   default choice).
   Some drivers have compile options.  They can be passed via
   --with-card-options option.  Multiple options can be passed with comma,
   too.  The default is "all".
   For available cards and options, see ./configure --help.

 * Example
      ./configure --with-debug=full
      ./configure --with-cards=sb16,emu10k1 --with-card-options=sb16-csp

4) Run 'make'.

5) Run 'make install' as root.
   If you have already a system with ALSA init script, you should install
   just only modules via 'make install-modules' so that the existing init
   script won't be replaced.

6) Run the './snddevices' script to create new sound devices in /dev directory.
   Skip this step, if you have already /dev/snd/* files, or if you're
   using a DEVFS or udev.

7) Edit your kernel module config (either /etc/modprobe.conf or
   /etc/modules.conf, depending on the kernel version). If you are not
   sure, what to do, you may try the alsaconf script available in
   the alsa-utils package.

8) Run 'modprobe snd-xxxx' where xxxx is the name of your card.
   Note: All ALSA ISA drivers support ISA PnP natively, so you don't need
         isapnptools any more.  Don't use both together.  It will
         conflict.  For disabling the ALSA ISA PnP support, specify
         --with-isapnp=no configure switch.

You can also look at the utils/alsasound file. This script is designed for
the RedHat distribution, but it can be used with other distributions which
use System V style rc init scripts.

Note: All mixer channels are muted by default. You must use a native
      or OSS mixer program to unmute appropriate channels (for example a
      mixer from the alsa-utils package).

Note: This document notices the /etc/modules.conf file. Many current
      distributions uses the old /etc/conf.modules file. Both names are
      valid.
```
i dont really understand what i have to write in the terminal.
help me please

---

### Post by kvonb on 2007-10-05
Don't waste your time with drivers and suchlike, you were right, it isn't being set as the default card.

See the _**[SIZE=3]Configuring default soundcards / stopping multiple soundcards from switching [/SIZE]**_section in this thread:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by dany_tab on 2007-10-05
look, when i entered alsa mixer from the terminal:
[[IMG]http://img03.picoodle.com/img/img03/9/10/5/t_Screenshotm_f55bfe4.jpg[/IMG]](http://www.picoodle.com/view.php?img=/9/10/5/f_Screenshotm_f55bfe4.jpg&srv=img03)
it writes thet my on board card is defult. 
how do i make my c-media card defult ?

---

### Post by kvonb on 2007-10-05
OK, I'll assume you are using standard Ubuntu 7.04.

On the main menu go to:

Applications->Accessories->Terminal

and click on it.

Now type this: (you can simply copy and paste these instead of typing)

```
sudo su
```

Enter your normal logon password

```
cat /proc/asound/modules
```

You should see something like this:

```
kev@kevs-laptop:~$ cat /proc/asound/modules
 0 snd_intel8x0
 1 snd_usb_audio
kev@kevs-laptop:~$
```

Where 0 (the first line) will be your onboard nvidia sound card, and the 2nd line should be your CMI one.

Now write down the part right after: snd_.  For me it would be snd_usb_audio, I'm not sure what yours will be, maybe something like snd_cmixxx.

```
gedit /etc/modprobe.d/alsa-base
```

[SIZE=2]At the very end of the file, add the following:

[/SIZE]```
options snd_cmixxx index=1
options snd_nvidia index=2
```

[SIZE=2]Now don't forget you have to replace **cmixxx** and **nvidia** in the lines above with the information you got from [/SIZE]*cat /proc/asound/modules* above.

Save and exit gedit, then simply close the terminal.

Reboot, all should be ok.

---

### Post by dany_tab on 2007-10-05
thank you

I solved the problem!!!

[SIZE="6"]the solution to problems with c media sound card[/SIZE]

1)i made the c media card the c media card defult according to this "how to": [http://www.lockergnome.com/nexus/linux/2007/09/23/setting-the-default-sound-card-usb-headset](http://www.lockergnome.com/nexus/linux/2007/09/23/setting-the-default-sound-card-usb-headset)

2)from the terminal i opened the alsa mixer:
```
alsamixer
```
and turned on the microphone. using the link that **kvonb** gave me.

---

