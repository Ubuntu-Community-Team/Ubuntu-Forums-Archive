---
title: "Sound problems"
date: 2005-07-18
forum: General Help
---

### Post by claus on 2005-07-18
Hi,

since I updated to "Hoary" I am experiencing strange sound problems.

1. CDs are no longer being played (before the update I used gnomecd without any problems; now CDs are recognized and the first title is displayed, but the track isn't being played. When I deliberately select a different file on the CD, the display jumps back to the first file.

2. None of the players (noatun, xmms) plays *any* sound file on my harddrive.

3. RealPlayer 10 Gold did play files, but all of a sudden doesn't show up any more when invoked.

I added a symbolic link '/dev/cdrom', but apparently to no avail :-(! (I removes a directory /cdrom in the hope to solve the problem, since, as far as I know, cdrom belongs to either /dev/cdrom or /media/cdrom0. Was this a mistake?)

Generally sound *is* working. When I execute /etc/init.d/ ./alsa start, I hear noise coming out of the speaker; after 'alsa  stop', the noise stops. So at least alsa is working--but where is the problem with the players? Did I unintentionally uninstall some libraries in Synaptic? I don't know! :-( At least I can't recall uninstalling *anything* related to "sound".

Can anybody give me a clue about proper debugging and how to get RealPlayer working again?

THX,

Claus

---

### Post by claus on 2005-07-18
I had a *brief* success: 'gnomecd' *did* play a track from a CD, but when I tried to adjust the volume  the system crashed. Now the volume control doesn't show up any more. 'noatun' *does* play a file from the harddisk now, but I can't hear anything! :-(

P.S.: RealPlayer starts again, too, but I get the error message 'audio device can't get started'.

---

### Post by firenurse4 on 2005-07-18
I don't know if it will help or not, but my sound problems were from the output source in Multimedia Settings being diffrent from the settinds on XMMS. Once the matched, I was able to get it working.

---

### Post by claus on 2005-07-19
[QUOTE=firenurse4]I don't know if it will help or not, but my sound problems were from the output source in Multimedia Settings being diffrent from the settinds on XMMS. Once the matched, I was able to get it working.[/QUOTE]I checked this right now (the default values fro Audio in 'Multimedia Settings' being ESD). When I changed this to ALSA and pressed 'test', I got```
Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'
```but I don't know how to solve this problem! :-(

---

### Post by firenurse4 on 2005-07-19
[QUOTE=claus]I checked this right now (the default values fro Audio in 'Multimedia Settings' being ESD). When I changed this to ALSA and pressed 'test', I got```
Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'
```but I don't know how to solve this problem! :-([/QUOTE]

I was getting this too. What I did was to use one of the sound options that played a test sound, then matched that with the sound output option in the program that was not working.

---

### Post by JoeUbuntu on 2005-07-19
Hi claus, have you tried following the ubuntu guide?

[http://www.frankandjacq.com/ubuntuguide/5.04/#configuresoundproperly](http://www.frankandjacq.com/ubuntuguide/5.04/#configuresoundproperly)

Regards

Joe

---

