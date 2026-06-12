---
title: "Removable Media - How to save default behaviour"
date: 2023-05-01
forum: General Help
---

### Post by z7APXKm on 2023-05-01
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.6 LTS"

Hi

I've created a wrapper for abcde to auto-rip CDs when they're inserted into the CD draw.  (See here: [https://askubuntu.com/questions/67116/how-to-run-abcde-when-i-insert-music-cds](https://askubuntu.com/questions/67116/how-to-run-abcde-when-i-insert-music-cds) ). 

This shows up as an option in the desktop screen Settings > Devices > Removable Media.  

So I can select for CD audio - "abcde CD wrapper" - but there's no way of saving it - and it just defaults back to VLC.

Code:
/usr/share/applications/abcde.wrapper

```
[Desktop Entry]
Type=Application
Name=abcde CD wrapper
Icon=brasero
Exec=/home/myUser/rip_CD.sh %F
Terminal=false
Categories=AudioVideo;DiscBurning;
MimeType=application/x-cd-image;application/x-cdrdao-toc;application/x-cue;application/x-toc;audio/x-scpls;audio/x-ms-asx;audio/x-mp3-playlist;audio/x-mpegurl;application/x-brasero;x-content/audio-cdda;x-content/video-dvd;x-content/video-vcd;x-content/video-svcd;x-content/image-picturecd;
Keywords=abcde;disc;cdrom;dvd;burn;audio;video;
NoDisplay=false
X-Desktop-File-Install-Version=0.23

```

I also tried editing /usr/share/applications/defaults.list - which doesn't seem to do anything.

```

#x-content/audio-cdda=rhythmbox-device.desktop
x-content/audio-cdda=abcde.desktop

```

It used to work?!  Clearly I'm missing something - not sure what though. Any help gratefully received.

---

### Post by TheFu on 2023-05-01
Standard support for 18.04 ends this month.  Time to move to a supported LTS.  I'm in the same boat with a few systems here.  Can't put it off any longer.  Soon (days, not weeks), all the repos will be gone and upgrading will become much harder without a fresh install.

---

### Post by z7APXKm on 2023-05-01
Thanks for the warning!  That's done now..  A few more problems to fix.

---

### Post by Holger_Gehrke on 2023-05-02
The command 'xdg-mime' should allow you to query and set the association between mime-type and program.
```

xdg-mime query default x-content/audio-cdda

```
to check the currently set default
```

xdg-mime default abcde.desktop x-content/audio-cdda

```
should set abcde as the default.

Holger

---

### Post by z7APXKm on 2023-05-06
Thanks, 

This is what I have now:

```

root@Myth:/home/myUser# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=22.04
DISTRIB_CODENAME=jammy
DISTRIB_DESCRIPTION="Ubuntu 22.04.2 LTS"
root@Myth:/home/myUser#  xdg-mime query default x-content/audio-cdda
abcde.desktop

```

The Removable Media settings screen still shows VLC media player as the default against CD audio, although I can drop down to select abcde-CD wrapper.  Same issue though - it doesn't save (and I might be being dense but I don't see a save button).  So when you click off and back on to this screen it's back to VLC.

I have the abcde wrapper as a favourite on the left, so I can click it manually, but would be nice to have it run automatically.

---

### Post by Holger_Gehrke on 2023-05-06
This is the point where I actually tried it and found that on my XUbuntu it also didn't work. Associating things with a mime type is overridden by the settings in 'Removable Drives and Media'. But in XUbuntu you actually get to type in a command with some obvious variables you can use as parameters and it does store these settings and uses them. There is no save botton here either, but the 'close' button saves the settings.

Holger

---

