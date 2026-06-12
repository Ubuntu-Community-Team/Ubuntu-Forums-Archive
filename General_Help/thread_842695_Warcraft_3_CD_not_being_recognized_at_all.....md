---
title: "Warcraft 3 CD not being recognized at all...."
date: 2008-06-27
forum: General Help
---

### Post by zapree on 2008-06-27
Ok so i put my WC3 cd into the drive *buzzzz* drive starts up then..... nothing, i go into places>computer look at the cd/dvd drive icon and its normal as if nothing were in the drive... i know that the drive works because i installed my system off the drive and it worked on X.P. 
anyways im starting to get despirate here cause ive been looking for an answer for a good 2 hours (im a tottal noobie but i like finding out how to do it bymyself) and i already posted 1 thread, but that diddnt fly too well and anyways this nOOb needs help.
oh and also when i click on the drive icon it says "unable to mount location  cant mount file"
thanks to all who make this happen
Patrick

---

### Post by mitchell19 on 2008-06-27
does your WarcraftIII cd work under windows?

---

### Post by zapree on 2008-07-06
yeah as i said in the above post it worked in X.P.

---

### Post by Spalatum on 2008-07-06
You know games do not install the same way in linux as they do in windows. For starters you will need to install wine or some similar application in order to install Warcraft III in linux.

---

### Post by zapree on 2008-07-06
of course, but to install the application with wine i have to have access to the files on the cd. and when i put in ls /media and then ls /media/cdrom it comes up with nothing and just skips to a new line

---

### Post by shae on 2008-07-06
First follow the link in my signature to get Wine with some patches to help in Warcraft 3 FT.

Then place the cd in your cd rom and run the following command for RoC:

```
winecfg
wine /media/cdrom/install.exe
```

After that installs, place the FT CD in and run the following:
```
wine /media/cdrom/install.exe
```

---

### Post by zapree on 2008-07-06
for RoC (what is that)? not in terminal?

---

### Post by zapree on 2008-07-08
patrick@patrick-desktop:~$ winecfg
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
patrick@patrick-desktop:~$ wine /media/cdrom/install.exe
wine: cannot find '/media/cdrom/install.exe'
patrick@patrick-desktop:~

thats what happens when i tryed what u told me :P

---

