---
title: "Ps3 ubuntu Screen Resolution HUGE problem."
date: 2007-07-31
forum: General Help
---

### Post by TommytheCat42 on 2007-07-31
Ok, I have Ubuntu 7.04 fiesty fawn installed on my PS3, and I went in the terminal and entered a command (don't remember what it was) to change screen resolution. I changed it but when I restarted for the effect the take place I got an error during the boot that said  "falied to start the X server(your graphical interface). It is likely that it is not set up properly" It than says it will not load the graphical interface, or shut it down, and while still in the black screen white text DOS like mode, tons of numbers followed by "assuming drive cache: write through"flys down the screen with numbers increasing. It also still lets you log in, but with no graphical interface. any help on how to reset screen resolution or something else to fix this?:confused:

---

### Post by AlexThomson_NZ on 2007-07-31
The file you likely changed was /etc/X11/xorg.conf, if you can change the value back to what it was, or restore your backup of this file (you did back it up right? :) )

You probably specified a resolution the PS3 can't support, so it is normal behaviour to get errors and the console.

You can look at the detailed warnings/errors in /var/log/Xor.0.log

---

