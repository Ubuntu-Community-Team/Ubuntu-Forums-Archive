---
title: "Can't launch an exe file"
date: 2008-06-28
forum: General Help
---

### Post by Nothingpp on 2008-06-28
says there's no installed application...

---

### Post by |{urse on 2008-06-28
do you have wine installed? 

open a terminal 

menu > accessories > terminal

type in this command

> sudo apt-get install wine

when thats done run this command

> winecfg

no need to mess with the settings until you need to so click apply aNd close the winecfg window.

now right click on the exe you were trying to run and select "open with wine windows emulator"

---

### Post by knutschr on 2008-06-28
Install wine first.
.exe is windows.
What program is it?

---

### Post by kellemes on 2008-06-28
> **Nothingpp said:**
> says there's no installed application...

I hope you understand an exe isn't made for Linux?
Still previous poster explains how to bypass this for some applications.

---

### Post by Nothingpp on 2008-06-28
Thanks guys, I'm new to Ubuntu and Linux overall so, I didn't know..

---

### Post by |{urse on 2008-06-28
welcome to linux by the way. If you need to know what the linux equivalents to any windows programs are, be sure to ask. :guitar:

---

### Post by Nothingpp on 2008-06-28
When excecuting winecfg:

> preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on C-Media USB Headphone Set  , disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:jack:JACK_drvLoad error loading the jack library libjack.so.0, please install this library to use jack



---

### Post by kellemes on 2008-06-28
ignore this post.

---

### Post by |{urse on 2008-06-28
okay, rerun winecfg.
click the tab entitled audio. (this may take a few seconds to load)
select the OSS driver in the tree menu.

---

### Post by Nothingpp on 2008-06-28
ok i right clicked the program, clicked open with wine, but it doesn't work..

---

### Post by knutschr on 2008-06-28
Why do you want a windows program?
What program is it?
You have 24.000 free programs to choose from.
Open Synaptic from terminal
```
gksu synaptic
```
Open all repositories.
Click reload? at left.
Search!

---

### Post by |{urse on 2008-06-28
okay. What program is it that you are trying to run? and is it the installer for that program?

---

