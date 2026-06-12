---
title: "[SOLVED] thers no sound"
date: 2007-12-27
forum: General Help
---

### Post by drakebahamut on 2007-12-27
i just added gusty and now i have no sound. on my tool ber it shows the sound icon with a x in a box on it. when i click it it says (No volume control GStreamer plugins and/or devices found). well i have speaker pluged in and i have downloaded every gstreamer plugin i can find. help

---

### Post by forestpixie on 2007-12-27
can you do lspci in a terminal and post the output

---

### Post by drakebahamut on 2007-12-27
i dont no what that means

---

### Post by forestpixie on 2007-12-27
ok - I assume you're running ubuntu

open a terminal from applications>accessories 

paste this into the terminal and press enter

```
lspci
```

it will print a list of hardware on your pc, copy that output into a post here

and just as an aside - you shouldn't really post the same question :)

---

### Post by drakebahamut on 2007-12-27
00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8050 PCI-E ASF Gigabit Ethernet Controller (rev 17)
06:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

---

### Post by forestpixie on 2007-12-27
I think that you're audio device needs to have alsa recompiled from the search I've done

never done anything like that - will have a look in the forum/google and will be back later

in the meantime you can try searching the forum - also try using the [uboontu]("http://www.uboontu.com/") search site - it's what I use

this is the result I got to start with

[http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=No+volume+control+GStreamer+plugins+82801FB%2FFBM%2FFR%2FFW%2FFRW&sa.x=45&sa.y=24&sa=Search#1456](http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=No+volume+control+GStreamer+plugins+82801FB%2FFBM%2FFR%2FFW%2FFRW&sa.x=45&sa.y=24&sa=Search#1456)

This thread will probably be on the front page for a while so you might get some more posts yet

Just so you're aware - if you follow any threads to try and fix it - you might need to use 'sudo' - it'll want you're password - but you won't see it - it IS there :)

---

### Post by kpkeerthi on 2007-12-27
Open terminal and type **alsamixer** and press <enter>. Make sure all the sliders are 'up' and nothing is muted (Press 'M' key to mute and unmute). Press 'Esc' to quit.

---

### Post by drakebahamut on 2007-12-27
thanx if you do find a way to fix it my email is [email]richdragons@hotmail.com[/email]

---

### Post by drakebahamut on 2007-12-27
it says (alsamixer: function snd_ctl_open failed for default: No such device)

---

### Post by forestpixie on 2007-12-27
can you give us a bit more info - like pc or laptop - make etc. I'm guessing it's a laptop

---

### Post by drakebahamut on 2007-12-28
no its a desktop no internal sound only external ( i have speakers in the head phone jack 3.3 mm or what ever its called. i hade fiesty thene upgraded to gusty and lost my sound i just says (No volume control GStreamer plugins and/or devices found) i have th edevice the speakers and i have every thing that says gstreramer

---

### Post by drakebahamut on 2007-12-28
well it seems that i dont have any devicesthers a screen shot

---

### Post by forestpixie on 2007-12-28
there was a whole bunch of problems like this, can you do these in a terminal 

```

aplay -l
lsmod | grep snd
cat /proc/asound/cards
cat /proc/asound/version
cat /etc/modules

```

post those - but as I said I've never needed to do anything like this before - and no-one else appears to be looking, anyway lets see what happens

I will say though I had a few oddities when I upgraded and then (for another reason) I ended up having to reinstall and they went

---

### Post by ajmorris on 2007-12-28
hi there, the mixer error means it can not find the specified card, so, we are going to re-compile the alsa-drivers into the kernel :)
(I am assuming sound worked before the gutsy upgrade)

First Open up the terminal again
then do the following commands:```
cd /usr/src
sudo module-assistant update
sudo module-assistant prepare
sudo module-assistant auto-install alsa
sudo shutdown -r now
```

The last command there reboots the computer, once in, does your sound now work again? (try alsamxer again also)
If not, come back, and we'll try something else :)

---

### Post by Venoseth on 2007-12-28
This really helped me...

> **eamann said:**
> Hello!

I too have the same problem. Apparently it is due to "permissions". Further information on [http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/](http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/)

However, when I tried the solution proposed by Kamil
 chmod -R a+rwx /dev/snd
my terminal replied: su: invalid option -- R

How do I get round that?

from post... [http://ubuntuforums.org/showthread.php?t=591886](http://ubuntuforums.org/showthread.php?t=591886)

Hope that helps.

---

### Post by RockHaxor on 2007-12-28
I have a dell dimensions I had a similair problem. I had found a solution that worked but I don't have the link.

 I did copy the code in open office so I am pasting it below.

 I had just cut and paste this in the terminal and it did its thing. When i rebooted I had sound.

```
sudo apt-get install libc6-dev
sudo apt-get install patch
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
tar xvpjf alsa-driver-1.0.15.tar.bz2
cd alsa-driver-1.0.15
./configure --with-cards=hda-intel,emu10k1
make
sudo make install
```

---

### Post by drakebahamut on 2007-12-29
> **Venoseth said:**
> This really helped me...



from post... [http://ubuntuforums.org/showthread.php?t=591886](http://ubuntuforums.org/showthread.php?t=591886)

Hope that helps.

that did the job thank you sooooo much and thank you everybody esls for helping it is verrrrrrrrrrrrrrrrrrrrrrry appreciated.

---

### Post by forestpixie on 2007-12-29
excellent - glad you're sorted - can only imagine what it's like with no sound - I would go mad 8-[

don't forget to mark thread once you're happy

---

