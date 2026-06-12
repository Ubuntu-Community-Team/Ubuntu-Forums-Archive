---
title: "dreamweaver reg file to ascii"
date: 2006-11-04
forum: General Help
---

### Post by chad01 on 2006-11-04
hi,I have been following the guids on installing dreamweaver and i get to “HKEY_LOCAL_MACHINE/Software/Macromedia/” to “macromedia.reg”, then copy it to your your Ubuntu and convert it to ascii with “$ recode ucs-2..ascii macromedia.reg”. Afterwards, type “$ sudo wine regedit macromedia.reg” 
which i do but when i run recode ucs-2..ascii macromedia.reg from the terminal it says  No such file or directory  I have copied the reg file from windos and have placed it on the desktop also in the home folder and in the .wine directory, can someone please tell me what folder it has to go in for the terminal to find it thanks

---

### Post by chad01 on 2006-11-04
I just got it running without converting the reg file i just started it with the command line wine "C:/Program Files/Macromedia/Dreamweaver 8/dreamweaver.exe"

---

