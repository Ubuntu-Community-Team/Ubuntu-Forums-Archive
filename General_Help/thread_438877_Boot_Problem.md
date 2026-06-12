---
title: "Boot Problem"
date: 2007-05-10
forum: General Help
---

### Post by mole25 on 2007-05-10
wheni boot into ubuntu i get passed the loading screen then it just asks for me to login, once i login i just geta camand line and i have no clue what to type! please help. i have tried booting off the live cd and this worked but didnt know what to do from there.

---

### Post by Xeor on 2007-05-10
Have you edited a file in particular, or just installed something new that would have changed your Xorg.conf ?

---

### Post by mole25 on 2007-05-10
it comes up with a message when i try and shutdownsaying that TIMIDITY needs to be confuigered so could that have something to do with it?

---

### Post by ikonia on 2007-05-10
First of all - have you ever had a desktop / window manager login, or has it always gone to the command line.

what version of ubuntu did you install (version/product/arch - eg: 6.10/server/x86)

---

### Post by mole25 on 2007-05-10
no it has never gone to comand line before, it used to come up with a log on window then go straight to my desktop once i loged on. i am using ubuntu feisty 7.10 standard.

---

### Post by ikonia on 2007-05-10
and have you changed anything, updated anything ??

do "grep EE /var/log/xorg.0.log" and post the output here.

---

### Post by mole25 on 2007-05-10
i cant check at the moment because i am in collage but i will try it when i get back at about 6. and will post it. thanks

---

### Post by mole25 on 2007-05-10
heres the results of "grepp EE /var/log/xorg.0.log

(WW) warning, (EE) error, (NI) not implemented, (??) unkown

(II) loading exstension MIT-SCREEN-SAVER
(EE)xf86OpenSerial: Cannot open device /dev/input/wacom
(EE)xf86OpenSerial: Cannot open device /dev/input/wacom
(EE)xf86OpenSerial: Cannot open device /dev/input/wacom

---

