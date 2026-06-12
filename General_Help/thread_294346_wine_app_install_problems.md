---
title: "wine app install problems"
date: 2006-11-06
forum: General Help
---

### Post by mrehorst on 2006-11-06
I bought a low-end PC for my son at a swap meet because it had Win XP on it and I need it to run his Lego NXT programming software.  When I got it home I discovered that the XP install was botched- they used a Dell XP disc to install XP over win2k on a Gateway machine!  Amazing that it even booted, but it did.  

So I got smart and installed ubuntu instead.  I use it on my other PC and like it a lot.  

I still have the problem of running the Lego NXT software.  I decided to try installing wine, then install and run the Lego program.  I sucessfully installed wine, I think, but when I try to install the Lego program from the CDROM using the following command, I get the error message shown.  Can anyone tell me what I'm doing wrong?

alex@REHORST:~$ wine /media/cdrom0/setup.exe
wine: could not load L"Z:\\media\\cdrom0\\setup.exe": Module not found

I have also tried calling it cdrom instead of cdrom0 and the result in the same.

Thanks!

MR

---

### Post by ashmew2 on 2006-11-07
I think first of all make sure that there IS a setup.exe in your CD . IF there is then u can copy all the files in the CD to some folder and try and execute it from there , if from the terminal cd to the folder's directory and wine setup.exe or if u want to run it graphically , right click setup.exe goto permissions then enable Allow executing as program and then apply. after that right click again and Run using "Wine"
Hope that helps.

---

