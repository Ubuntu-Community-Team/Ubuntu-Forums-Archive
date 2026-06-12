---
title: "Resolution won't get on 1280x768"
date: 2007-04-29
forum: General Help
---

### Post by YSH on 2007-04-29
I would like to get my screen resolution set on 1280x768, but i can't select that. I know my monitor can handle it, since in XP i had it.

---

### Post by Findoo on 2007-04-29
In the terminal type "sudo dpkg-reconfigure xserver-xorg" then go through all the options until you reach screen resolution. Once you have selected the resolution you want, and finished configuring it, restart your X server then go to System -> Preferances -> Screen Resolution and change it there (if it hasnt done so itself :))

---

### Post by BRAXS69 on 2007-04-29
enter this command in the terminal window.
"sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak" makes a copy of the xorg. 
"sudo dpkg-reconfigure xserver-xorg" go thought the step by step make sure you enter the right things, and when it gets to the configure monitor you will be able to pick the resolutions your monitor can handle, (use the space bar to check the options enter is continue.)   

and then you should be all set.
but if the xorg crashes, get into the shell and enter "sudo dpkg-reconfigure xserver-xorg" again and retry till you get it right and if you grow sick of trying or just want to get it working again go 
"sudo cp /etc/X11/xorg.conf.bak  /etc/X11/xorg.conf" this will restore the backup you made then restart the computer and try again.

---

