---
title: "Emulate ISO as original CD"
date: 2007-02-26
forum: General Help
---

### Post by cisforcojo on 2007-02-26
Hey guys, 

I'm trying to get eyeQ, a speed reading program, working in Ubuntu and it's a pain in the *** inserting the CD every time (you're supposed to do it every day). Anyway, is there any way I can use an iso and configure wine so that it's read as the original cd?

So far, I've mounted the iso:

mount eyeQ.iso /media/eyeq -t iso9660 -o loop

and added the drive in 'winecfg'. Are there any special settings I should put there?
I specified it as a CD-ROM drive under 'Advanced Settings'. 

Nevertheless, when I run the program, no dice.

Any luck? This works perfectly fine using DAEMON Tools in Windows.

Thanks!

---

### Post by nereid on 2007-02-26
Normally you've done it right. Is it the same ISO which you use with Windows? It could be an entry in the wine registry which specifies your /media/cdrom as target cdrom and not /media/eyeq. Maybe you just try to mount the ISO to the /media/cdrom directory and take a look if it works.

---

### Post by cisforcojo on 2007-02-26
You, sir, are a filthy genius.

That worked perfectly! Does anyone know how to edit my wine reg so that /media/eyeq registers as a CDROM drive? Thank ya!

---

### Post by nereid on 2007-02-26
Sure, I'm a filthy genius! Just open up your favorite text editor and go through the wine registry or start regedit.

---

### Post by cisforcojo on 2007-02-26
I'm not sure exactly what to change. I've done what I think it needs but no result.

I edited system.reg with:

[Software\\Wine\\Drives] 1089668326
"c:"="hd"
**"E:"="cdrom"**
"y:"="%CXOFFICE_DRIVE_TYPE_HACK%"
"z:"="%CXOFFICE_DRIVE_TYPE_HACK%"

where E: is /media/eyeq at least according to 'wincfg'

I installed the program with CrossOver Office but I'm not sure which system.reg I need to modify. I'd like to think that when I run the program, it's using the system.reg from the EyeQ bottle but I'm not so sure. So I changed the .wine/system.reg, .cxoffice/default/system.reg and .cxoffice/EyeQ/system.reg


Still nothing. Dammit this is much harder than I thought it would be. There is one line that I don't understand. Perhaps this has something to do with it. (from system.reg)

[System\\CurrentControlSet\\Control\\Class\\{4D36E965-E325-11CE-BFC1-08002BE10318}] 1101109729
@="DVD/CD-ROM drives"
"Class"="CDROM"
"UpperFilters"=str(7):"Cdralw2k\0"

[System\\CurrentControlSet\\Services\\CDROM] 1011804099
"DisplayName"="CD-ROM Driver"


Thanks!

---

### Post by nereid on 2007-02-26
No, everything you should have to change should be at the keys from the eyeQ installation. Don't change anything from the default wine installation. It is the same as Windows.

---

### Post by cisforcojo on 2007-02-26
Got it. Had to delete a symlink in a 'dosdevices' directory and then create a new one to /media/eyeq. 

Thanks for all your help!

---

