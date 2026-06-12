---
title: "Rosetta Stone in WINE"
date: 2006-11-01
forum: General Help
---

### Post by machoo02 on 2006-11-01
Hi,

I was wondering if anyone has been successful in using the Russian language pack with Rosetta Stone through WINE.  RS does not display a Cyrillic font as it should, just whatever character is present on the us keyboard layout where a cyillic letter should be.  I've tried installing every cyrillic font/KDE language pack that I could find in the repos, but nothing.  I've also heard that this same problem occurs with other languages in RS (e.g., Chinese).  Any success stories out there?  Or any open source replacement for RS?

---

### Post by zorkerz on 2007-03-20
Hello I don't have the russian language pack. Ive been trying to do the french version through wine. my only problem is that i don't want to use the cd and cannot find a way to get rosetta stone to recognize the mounted iso.

---

### Post by scotttkd on 2007-03-20
i was able to get RS to work on a UMPC with no cd rom drive by using a virtual CD program.  (forget the name right now but there must be dozens of them around for both windows and linux)  RS is on my list of things to get working on my new edgy install as son as I can.

---

### Post by machoo02 on 2007-03-20
The easiest way to get RS to find the mounted iso is to tell wine to include that directory in its search path.  For example, if all of your language iso's are in /home/user/isos, then run winecfg and set ~/isos as a cdrom drive.  I have my language files in a folder, and not on an iso...when I run RS, I usually just mount that folder as an iso in /media, and RS finds it just fine.

Hope this helps.

---

### Post by kditty on 2007-06-21
> **machoo02 said:**
> The easiest way to get RS to find the mounted iso is to tell wine to include that directory in its search path.  For example, if all of your language iso's are in /home/user/isos, then run winecfg and set ~/isos as a cdrom drive.  I have my language files in a folder, and not on an iso...when I run RS, I usually just mount that folder as an iso in /media, and RS finds it just fine.

Hope this helps.

this worked great,  first i installed AcetoneISO2:
[http://ubuntuforums.org/showthread.php?t=463972&highlight=mount+iso](http://ubuntuforums.org/showthread.php?t=463972&highlight=mount+iso)

after installing AcetoneISO2 i mounted the spanish pack ISO. it mounted to /home/kditty/virtual-drives/1/

then i added my iso of the spanish pack through winecfg as a cd-rom drive. to do this i had to mess around with winecfg for a few before i figured it out, read on.

open winecfg, select drives tab, then click add. with your new drive highlighted, click browse. if you used AcetoneISO2 then it will have mounted at /home/USERNAME/virtual-drives/1/ browse to there, select the folder and hit ok.

now you need to set the drive to a cd-rom, click show advanced, select your drive and choose cd-rom from the drop down menu. thats it, thats what worked for me. good luck and thank you machoo02 for the help for a nub :D

---

### Post by jorwex on 2008-04-29
I tried the winecfg trick with an older version of Rosetta stone (2.0.8) and it couldn't find my korean language pack files. 

I just went to the language pack cd and blindly copied all of the folders that started with "KORXX_XX" to a directory. 

I didn't think to grab anything else at the time. I'm at work now, but I'll check to see if there are any indexing files or something like that.

Does anyone know offhand what else might be needed besides the folders themselves? Thanks

---

