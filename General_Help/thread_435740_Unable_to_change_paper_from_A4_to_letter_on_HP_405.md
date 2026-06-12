---
title: "Unable to change paper from A4 to letter on HP 4050"
date: 2007-05-07
forum: General Help
---

### Post by wjhildreth on 2007-05-07
Hello all,

   I have managed to install my networked HPLJ 4050 buta am having a problem. When I first tried to print, the printer gave me a message to load A4 into the paper tray. Ooops ... I should have told it that I was using letter. I deleted the job from the printer and went back to the printer properties and changed it to letter and tried printing again. My printer insists on me loading A4. I am running Feisty Faun. The printer tray is set up for letter in the printer settings on the printer itself and set to letter on the printer property page in Ubuntu. Can someone please explain how I can fix this, or point me to somewhere I might be able to read about?

Many thanks for your time and energy.

Warm Regards,

Joe Hildreth

:confused:

---

### Post by fragos on 2007-05-07
Check out the HP toolbox in administration.  Also, some applications have their own paper size parmeters.  Also edit /etc/papersize to change from "A4" to "letter".  I'm not sure how this configuration file is used but its a logical change to make.

---

### Post by wjhildreth on 2007-05-07
Fragos:

    Thank you so much for helping me.

    I went to Administration to open the HP Tools, only to find they were not there. I looked everywhere in the menus and they are not listed.

    I checked with the add / remove programs to see if they were installed, they were. I tried removing and re-installing them and still they do not show up.

    Next, I edited the /etc/papersize file and changed it from 'a4' to 'letter' and looked at the page setup in firefox (what I was trying to print in) and found no other settings for papersize. I tried to print, but this time it works. Thanks for your help. I truely appreciate it.

   Now, I have other issues making the transistion from Windows to Linux, but they I will post them as a separate topic. But while we are on it, any ideas on how I can get the HP tools to show up? Can I create a link to them? What do they link to?  Many thanks.

Regards,

Joe Hildreth

---

