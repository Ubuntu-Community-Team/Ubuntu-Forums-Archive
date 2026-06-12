---
title: "NOOBEE Needs help copying files from desktop to /usr/src/alsa"
date: 2007-10-04
forum: General Help
---

### Post by jonel on 2007-10-04
Hello folks i'm a bit frustrated since I can't get any sound on my Toshiba P100 PSPA3C-SD402E Laptop. As you can probably tell i'm absolutely new to Ubuntu. By the way i have version 7.04.
Anyway i downloaded the alsa-driver package, and tried to copy the tar package to /usr/src/alsa, but i get  the message "[COLOR="Blue"]cp: cannot stat `alsa-driver-1.0.15rc3.tar.bz2': No such file or directory[/COLOR]" which of course is not true because i just created it previously. It might have to do with permissions or other, but i'm not experienced enough to know. Of course i issued the sudo cp command but i just get that message over and over. If someone can tell me the right way to copy please list detailed instructions for me. I thank that person very much in advance.
As a side note. Could instructions be posted on the forum on copying files and directories using the right permissions. I'm guessing it might save people a lot of headaches if they could find these instructions before posting anything on the forums.

---

### Post by aschaetter on 2007-10-04
Open a terminal and type "sudo nautilus" then enter your password.

---

### Post by jonel on 2007-10-05
You are most Gracious! I Thank You Very Much!!!!!!!!!!!!!!!!!!1http://ubuntuforums.org/images/smilies/icon_biggrin.gif

---

### Post by jonel on 2007-10-06
Maybe someone can untangle me from my web?
While working on getting my sound card to  give me at least a beep i got stumped.
Ok, here's the deal. I followed the instructions on Modifying the DSDT.dsl file but after having done that i noticed that the compiler didn't create a DSDT.aml file, it only created the  DSDT.dat and DSDT.hex file. What do i do and where do i go from here? I would like to finish this method that i'm trying. Who knows maybe it'll work. If it helps i have a Toshiba P100 PSPA3C SD402E Model Laptop. Thanx in advance!8-)[http://ubuntuforums.org/images/smilies/icon_cool.gif](http://ubuntuforums.org/images/smilies/icon_cool.gif)

---

### Post by jonel on 2007-10-13
Please Help this mixed up NOOB!!!!!!!!!!!
i'm still trying to get the sound working on my Toshiba Satellite P100 model PSPA3C - SD402E.
Basically i've tried just about all the techniques that we're posted, but no luck so far. From what i can tell the sound card is not being detected, but i have 2 mixer options in the volume control; one hda intel (alsa mixer), and one  conexant cx20551 (Waikiki) mixer. Strange. Though i can't explain it. I've also installed the latest alsa driver and alsa utilities. I tried the acpi=off option. The sound works perfect and fan blows continuosly, but  the Internet connection goes out. This isn't a really good solution. I don't mean to be ungrateful i would just prefer to find the problem, and fix it without any side effects. If there is someone out there who would be kind enough to offer me assistance, it would be tremendously appreciated. Thank You.

---

