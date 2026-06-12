---
title: "External monitor shuts off when opening login screen"
date: 2007-10-21
forum: General Help
---

### Post by WallRunner on 2007-10-21
[COLOR=DarkGreen][B]Hello, I don't know if this is in the right section, if not, please move it.

I upgraded to Ubuntu 7.10 Gutsy Gibbon yesterday, and everything seemed to work fine when booting up, until it got to the login screen, and the screen would go blank (Go into sleep mode), I can see the TTY consoles fine, and since when I boot up it is all text, I can see that aswell, My computer is a Compaq Evo N1015v, 240 mb RAM, 1.19GHZ Processor, 16MB video (from 256 MB Ram making it 240), the backlight went out a little over 3 months ago, and that is why I have an external monitor (Sampo AlphaScan 712).

Could anybody help?

From,
Chris.
[/B][/COLOR]

---

### Post by lonald on 2007-10-24
I have a Compaq Presario 2700 laptop, and I used an external monitor without problems in Ubuntu 7.04, but now, in Ubuntu 7.10, my external monitor will not display. I've never been able to extend my desktop with an additional monitor in either version, but I at least wish that 7.10 would allow me to use the external monitor exclusively like 7.04 did.

One thing that is interesting is that the secondary monitor will indeed display until after login (where resolution changes). Also, I believe I recall it displaying when I first installed 7.10, but it was at a high resolution; since reducing my resolution to 1024X768, I've not been able to get the secondary monitor working. Now, even when I try to change the resolution back to the way it was, I still can't get the external monitor to be my default. It simply won't display.

Backward compatibility has been broken with Ubuntu 7.10. This problem is with my external monitor, but I'm also currently working on a problem with my sound card:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/156013](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/156013)

---

### Post by wormie_dk on 2007-10-24
I know this might be obvious but have you tried messing with the system -> administration -> screen and graphics dialog?

I had the same problem but after "fooling" around with that dialog a bit I got my external monitor to work (even over DVI which has not worked before)

---

### Post by mnewell on 2007-10-25
I have exactly the same problem.  I've been messing with it for a while and here's what I notice:

[LIST=1]
[*]Disable gdm by unlinking the "/etc/rc{2-5}.d/S13gdm" files.
[*]Log in to a normal account.  Run "startx" to start the GUI.  The display only shows up on the laptop display panel.
[*]Now do "sudo startx" to run your GUI in privileged mode.  The display now does NOT show up on the laptop screen (at least on mine where the cover is closed) but shows up fine on the external display.
[/LIST]

Of course under gdm when you log in you're logging as your (unprivileged) self so the display doesn't show up on the external monitor.  I suspect if you log in as "root" all will appear as it did.  Except, of course, nobody wants to log in as root...

This is on a Dell Lattitude 600m laptop with an ATI RADEON 9000 card (and a smashed screen).

I also tried using the Screens tool to disable the laptop screen and enable the external monitor as the default display.  The result was a trashed xorg.conf file which I had to manually repair.

Not sure where to go from here...

---

### Post by gabr1el on 2007-10-26
Same thing here.  External monitor displays fine at the GDM login screen, however after logging in, the monitor goes dead.  

Strangely the external monitor actually works if the resolution is set to 1400x1050 (which works on my laptop LCD, but causes scrolling on the external monitor).  However, if I set the resolution to 1280x1024 (the max for the external monitor) the screen goes dead.

The Screens & Graphics control panel is useless as it doesn't detect the monitors or allow me to alter the second screen past 800x600.  This is incredibly frustrating...

---

### Post by WallRunner on 2007-10-27
[COLOR=DarkGreen][B]Try the vesa driver, it worked for me, no pretty Compiz for now but it makes it usable, which is all I need. This is on a ATI Radeon Mobility U1

(Needs xubuntu-desktop to work, to get use ctrl-alt-f2, [/B][/COLOR]```
sudo apt-get update

sudo apt-get install xubuntu desktop
```
[COLOR=DarkGreen][B]
at this point you may want to reboot.

Press ctrl-alt-F2, login with your user name and password, and type this

[/B][/COLOR]```
sudo nano /etc/X11/xorg.conf
```

[COLOR=DarkGreen][B]Under devices--->Driver add
[/B][/COLOR]```
vesa
```

Device setting section of xorg.conf

```
Section "Device"
        Identifier      "ATI Technologies Inc Radeon Mobility U1"
        Driver          "vesa"
        BusID           "PCI:1:5:0"
        Option          "UseFBDev"              "true"
EndSection
```

[COLOR=DarkGreen][B]But here is where I ran into another problem, thank god I had xubuntu-desktop installed.refresh rate was to high (85 hz)

If all has gone well, you should be able to see the login screen when you press crtl-alt-f7, under sessions, select XFCE, once you are logged in, use the menu to get to gconf, select desktop-->gnome-->screen-->default-->0, change the rate to what you know your monitor can support, also change the resolution if you would like. log out, and back in to gnome, and all should work :D

Note, this has only worked (as far as I know) on my computer with Gutsy gibbon 7.10, and a ATI Radeon Mobility U1

From,
Chris.[/B][/COLOR]

---

