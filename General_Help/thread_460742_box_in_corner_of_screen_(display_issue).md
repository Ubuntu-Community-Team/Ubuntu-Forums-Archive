---
title: "box in corner of screen (display issue?)"
date: 2007-06-01
forum: General Help
---

### Post by tk03759 on 2007-06-01
I've just installed Ubuntu on a new computer.

When I log into a user (the user I created with the Ubuntu installation), something goes funny with the display. When the user name and password is typed in, the screen flashes and distorts for a second, goes blank, and then the desktop starts to load. Once loaded, in the top left corner of the screen, a small "box" appears that is black with "lines" through it. It's hard to describe so I took pictures (it doesn't appear in screen shots???).

This problem appears on any monitor I use with this computer and goes away after about 10 minutes or so. It's really weird. I'm assuming it's something with the display settings, but I'm confused as to what might be causing it. Any suggestions?

Some images are attached.

---

### Post by Iokua on 2007-06-01
That is definitely very strange. What driver are you using? Are you using desktop effects? If I remember correctly, some distortion problems can be caused on certain monitors if the the horizontal and vertical refresh rates aren't set in xorg.conf.

---

### Post by benford on 2007-06-01
Have you tried reinstalling with a new monitor, or did you swap out monitors post-install? I had this exact same problem with one display (Apple CRT) which persisted on other monitors (Dell LCD). After doing a reinstall with the Dell LCD plugged in at the time the problem went away.

Less drastic methods like editing your xorg.conf will probably be best. Definitely check your scanline and vertical/horizontal refresh parameters, or switch drivers if your hardware allows.

---

### Post by tk03759 on 2007-06-02
I didn't enable desktop effects. I tried that on one computer a while back and got some really confusing issues and haven't used it since.

I got to the xorg.conf file by backing it up with "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup" and then opening it with "gksudo gedit /etc/X11/xorg.conf"

I couldn't much decipher it, so I'll attach a text copy here (that doesn't seem to have retained it's formatting).

Hope that's enough info.

---

### Post by Iokua on 2007-06-02
> **tk03759 said:**
> I didn't enable desktop effects. I tried that on one computer a while back and got some really confusing issues and haven't used it since.

I got to the xorg.conf file by backing it up with "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup" and then opening it with "gksudo gedit /etc/X11/xorg.conf"

I couldn't much decipher it, so I'll attach a text copy here (that doesn't seem to have retained it's formatting).

Hope that's enough info.

I did some searching based upon your xorg.conf and your monitor appears to be a ViewSonic Optiquest Q71-3. Is that correct? Did your monitor come with a manual? If so, check in the technical details section for horizontal and vertical frequencies. They may be listed under "Frequency" with "Fh" being horizontal and "Fv" being vertical. Write these down and then add them to your xorg.conf in the "Monitor" section. To do this, use the same commands you listed above (make a backup like you did before, then type: gksudo gedit /etc/X11/xorg.conf). Once opened, modify the Monitor section so it looks like this:

```
Section "Monitor"
	Identifier	"Q71-3"
	Option		"DPMS"
	HorizSync	28-49       
	VertRefresh	43-72
EndSection
```


The horizontal frequency goes next to the HorizSync option and the vertical next to the VertRefresh option. The example above is from a monitor similar to yours, so if you can't find your monitor's default values, try using the ones I provided here. Once you've made the changes, save the file, log out, and then press CTRL+ALT+BACKSPACE to restart X.

If X doesn't start and you lose your GUI, just log in and restore your backup xorg.conf and then reboot. To restore your backup, type:

```
cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by tk03759 on 2007-06-02
It worked.

That seemed like such a simple fix. Of course, the first time I tried I typo-ed Horiz and lost the GUI, but I fixed it and now it's working fine. No more box. =)

Thank you.

---

### Post by Iokua on 2007-06-02
> **tk03759 said:**
> It worked.

That seemed like such a simple fix. Of course, the first time I tried I typo-ed Horiz and lost the GUI, but I fixed it and now it's working fine. No more box. =)

Thank you.

Great! Future versions of Ubuntu are supposed to include better video card/monitor detection and a more robust configuration of the X server, so hopefully manual configuration of xorg.conf will soon be a thing of the past. Let's hope we see this in Gutsy or in the next LTS.

---

### Post by andrewpmk on 2007-06-16
I had the same problem. I have an LG 790SC monitor. Changing the Monitor section of my xorg.conf fixed it.

From:

Section "Monitor"
       Identifier      "Generic Monitor"
       Option          "DPMS"
       HorizSync       28-80
       VertRefresh     43-60
EndSection

To:

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-100
        VertRefresh     40-200
EndSection

Notice that the horizontal sync was slightly out of range with the autodetection.

---

### Post by andrewpmk on 2007-06-16
Oops, that didn't fix the problem.

---

