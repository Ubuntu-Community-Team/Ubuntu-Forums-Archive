---
title: "No sound, please help"
date: 2008-01-28
forum: General Help
---

### Post by thebloggu on 2008-01-28
i have a notebook here that has no sound with ubuntu 7.10.sound does work with vista.

aplay -l

```
a@a:~$ aplay -l

**** Lista de Dispositivos de Hardware PLAYBACK ****

placa 0: Intel [HDA Intel], dispositivo 0: HDA Generic [HDA Generic]

  Subdispositivos: 1/1

  Subdispositivo #0: subdevice #0

placa 0: Intel [HDA Intel], dispositivo 6: Si3054 Modem [Si3054 Modem]

  Subdispositivos: 1/1

  Subdispositivo #0: subdevice #0
```

lspci

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

what do i have to do?

---

### Post by codesplice on 2008-01-28
Try using a newer version of the alsa drivers?  You can get version 1.0.15 by installing the linux-backports-modules package.

---

### Post by adn258 on 2008-01-28
This worked for me try the command below after you use it in a terminal restart your computer.

sudo apt-get install linux-backports-modules-generic

---

### Post by thebloggu on 2008-01-28
i need other solution. That doesn't work...

thanks

---

### Post by thebloggu on 2008-01-30
no one has ideas?

---

### Post by orbish on 2008-01-30
This may be very novice, but I once had the same problem and the solution was very easy.  The volume wasn't up.  Have you made sure the volume was up in alsamixer?

From the commmand line type alsamixer

make sure all the volumes are up and not muted (shows MM at the bottom, you can unmute by hitting the letter m) and give it another shot

---

### Post by thebloggu on 2008-03-04
[http://pastebin.ca/927937](http://pastebin.ca/927937)

still have this problem. help please

---

### Post by superprash2003 on 2008-03-05
maybe this might help [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

