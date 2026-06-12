---
title: "Help!!"
date: 2006-12-19
forum: General Help
---

### Post by CCBalla10 on 2006-12-19
Hey guys, well i had my Edgy all set up correctly with Beryl 0.1.3 and i install Enemy Territory...well the game installed fine, but i noticed a little black box on the screen that flickered.  Being the genius that i am i edited my xorg.conf file and under the Device section i added VideoRam  13000 to boost my video card since i have an Intel :(  but anyways, i saved it, ctrl + alt + backspace to restart my X....and broke.  I realised that you can't add VideoRam option to Edgy's Xorg file.  So now i can't boot.  Any way to edit my xorg.conf file from the grub so i don't have to re-install everything all over again?
I just wanna delete the VideoRam option...

---

### Post by CCBalla10 on 2006-12-19
^Bump

---

### Post by DarkN00b on 2006-12-19
At the command line type ```
sudo nano /etc/X11/corg.conf
``` 
Enter your password and you will have your xorg.conf file opened in a command line text editor called nano. Make sure the "X" in "X11" is capitalised. Go down with the arrow keys and delete the line you added, then press ctrl+o (that is the letter o, not a zero) to save. Then press ctrl+x to exit. Restart and you should be good to go.

---

### Post by CCBalla10 on 2006-12-19
Thank u so much...but the sudo isn't needed since you are automatically logged in as root...but thank u...it works again!

---

### Post by DarkN00b on 2006-12-19
You are very welcome! Anytime I can help...

---

