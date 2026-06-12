---
title: "Resolution,dvd encryption and a newbie..."
date: 2006-12-01
forum: General Help
---

### Post by LudeLu on 2006-12-01
hi. its my first time on linux.

i want to change my resolution to 1280x800 (because i have a 16:9 screen) but when i go to the "preferences > screen resolution" i only have the option for 1024x768.
im using ubuntu 6.10 and gnome btw.

./etc/X11/xorg.conf :
```

Section "Device"
        Identifier      "Intel i810"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        8096
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-49
        VertRefresh     43-72
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel i810"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```

also. im trying to view some dvd's but none of them appears to play, i think it has something to do with the encryption(im trying to watch "Joe Satriani LIVE" and "Eric Johnson live from austin" if this may help) i have downloaded the "libdvdcss" from synaptic. but i still have problems.
im trying to view them using vlc or xine or totem but none of them works.

thanks.sorry for my bad english.

---

### Post by LLRNR on 2006-12-01
[Restricted formats](https://help.ubuntu.com/community/RestrictedFormats) (media files, DVD etc.) ;

[Resolution](https://help.ubuntu.com/community/FixVideoResolutionHowto) - also, are you *sure* that the values in xorg.conf (under section "Monitor") for your HorizSync and VertRefresh are the correct ones ? If not, look at this link ("Resolution" link) to see how the get them right. (If ddcprobe doesn't work, open a [terminal](http://www.psychocats.net/ubuntu/terminal) and type *sudo aptitude install xresprobe* and then re-run *ddcprobe*)

To install the driver for your Intel chip, see [here for Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28Intel.29) - in this link there's also a fix for resolution, as well. Before you do this, type in a terminal *sudo aptitude install alien*.

LLRNR

---

### Post by LudeLu on 2006-12-01
im sorry. i post the wrong conf file. 
i was playing with the conf file before posting and forgot to check what i actually did post ...

the original conf file had all resolutions "1280x800"(just this, no 1024x768 or 800x600) however, it was only giving me the 1024x768 option.

---

### Post by LudeLu on 2006-12-01
and im also sure that those are not the correct vertical and hor because the xserver is ruined,pushing me to use the live cd.

---

### Post by LLRNR on 2006-12-01
If they're not the correct values, then put this in a terminal:
```
sudo ddcprobe | grep monitorrange
```If you get a "command not found" error, do```
sudo aptitude install xresprobe
```first and then re-run *sudo ddcprobe | grep monitorrange* - the first pair is your HorizSync value, the second value is the VertRefresh one.

LLRNR

---

### Post by LudeLu on 2006-12-01
im doing sudo ddcprobe | grep monitorrange
but im dont get anything back. tried both in livecd and my X destroyed installation.

---

### Post by LLRNR on 2006-12-01
Oh, so in fact you ruined your actuall install... ? That shouldn't be too much of a problem if you boot normally (i.e. without the LiveCD), login (username + password) and then ```
sudo dpkg-reconfigure xserver-xorg
```and reboot (or maybe just hitting Ctrl+Alt+Backspace to restart the X Server would suffice).

LLRNR

---

