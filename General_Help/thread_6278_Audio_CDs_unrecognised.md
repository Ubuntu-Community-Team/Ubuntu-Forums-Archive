---
title: "Audio CDs unrecognised"
date: 2004-11-27
forum: General Help
---

### Post by dhamil on 2004-11-27
Just started using linux (two days old) and after a stumble over the modem (thanks for the fix azz) I now find myself in a bit of a jam. I can read data CDs and even burn CDs but for some reason whenever I put in a audio CD (store original) I get:

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.
[I]
and when I click to show details it has[/I]

mount: wrong fs type, bad option, bad superblock on /dev/hdc, or too many mounted file systems.

Hmmmm. I have no idea how to fix this. The only thing to do with audio I have done is followed the instructions at [http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats) to get MP3s playing. Which they do. Any help getting my audio CDs working would be a great help.

Even with these little teething problems I am still loving this alot more than using me old windows 2000.  :-P

---

### Post by TravisNewman on 2004-11-27
In your /etc/fstab file, is the type set to auto? If not, it might be trying to force it to read data instead of audio.

---

### Post by dhamil on 2004-11-27
Thanks for the help panickedthumb. It was set to noauto so I set it to auto and now I can play it in programmes but no sound comes out (just ripped one to .ogg and the files work perfectly O.o). And I still get that error message when I try to mount it (is that normal?). 

The little cable (for analog I believe) that came with the CD-ROM has long since gone and I have no trouble with audio in Windows. Could the cable hold the key???

---

### Post by Burgundavia on 2004-11-27
Yes, the cable transmits sound when the cd is running as a straight 1x audio player. DVD's are not affected. 

Corey

---

### Post by dhamil on 2004-11-27
Damn. Anyway to force it into sending the data any other way?


^
That above sentence was very close to not being in english.

---

### Post by zenwhen on 2004-11-27
[QUOTE=dhamil]Damn. Anyway to force it into sending the data any other way?


^
That above sentence was very close to not being in english.[/QUOTE]


Install XMMS. Go into the preferences. Configure the CD Audio plugin and make sure to select Digital Audio Extraction. You can then add the cdrom mount point to your xmms playlist and enjoy your tunes after you insert a disc.

Problem solved.

---

### Post by dhamil on 2004-11-27
Thanks everyone for your help. Very good of you.  :D

---

