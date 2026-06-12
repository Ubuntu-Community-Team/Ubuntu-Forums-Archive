---
title: "New monitor goes to sleep upon login (blank NOT black screen)"
date: 2014-02-06
forum: General Help
---

### Post by dannyboy79 on 2014-02-06
I had a syncmaster 225bw connected via DVI from my newly built haswell rig (just using the HD4600 igpu) and things were working just fine. Ubuntu loaded up the default i915 intel driver and graphics were working awesome. Can even play Trine 2 on ultra settings.

The syncmaster took a crap and it only displays red now, bad invertor or something. My friend gave me an older HP w1907 (it does work, I verified on another computer) so I connected my haswell rig to this new monitor (still using the same DVI port on the motherbaord) and I am presented with the lightdm login screen (i can see my background in the background of the login prompt dialog box), as soon as I enter my password and hit login, the screen just goes blank (as if it's not receiving a signal) and the monitor states, "Monitor is going to sleep". It's like X server isn't seeing the HP screen or doesn't know what refresh rates to send out???  


I can't figure out why it would be doing this? I don't have an xorg.conf so that's not the issue. I don't see anything blaring out at me via Xorg.0.log and nothing in .xsession-errors. I can view text just fine within tty1 so I am at a loss of what to do to fix this issue. 

Any help would be appreciated.

---

### Post by grier-devon on 2014-02-06
do these monitors support HDMI? If so have you tried to run the HDMI cable. Are you able to get to your display settings and see if it is fully detecting the monitor?

---

### Post by dannyboy79 on 2014-02-06
it doesn't have HDMI no. only DVI and VGA. How do I get to my display settings if i can't get X-server to boot BUT I can get to tty1 so whatever info you'd like to see I can provide. What info would you like?

---

### Post by pqwoerituytrueiwoq on 2014-02-06
does the guest account work?
 if so you just need to delete a file or 2, namely:
~/.Xauthority
~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-display.xml (may be desktop instead of display)
if it does not work on the guest account try the 3.13.1 kernel

---

### Post by dannyboy79 on 2014-02-07
SOLVED. I have no idea why I have to do this for this particular HP monitor but adding the following to my grub boot line WORKS
```
i915.i915_enable_rc6=1 acpi_osi=Linux acpi_backlight=vendor video=1440x900-24@60
```
*NOTE* change the end resolution to whatever resolution you're runnning. I also removed "quiet splash" as well because i prefer to see the text scroll by, it allows me to see things are working.
I did also uncommand GRUB_GFXMODE and I made it say text. so it is
```
GRUB_GFXMODE=text
```

---

