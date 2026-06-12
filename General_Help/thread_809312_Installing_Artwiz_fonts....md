---
title: "Installing Artwiz fonts..."
date: 2008-05-27
forum: General Help
---

### Post by Izobalax on 2008-05-27
Hi all!

I wish to use these magnificent fonts [HERE](http://artwizaleczapka.sourceforge.net/).

However, I can't use them, no matter how many times I've tried to install them. 

I tried the usual method, that is, placing in them in my .fonts directory and running ```
sudo fc-cache -f -v
```, but to no avail. I've attempted to follow numerous guides on the net without success (mainly because a lot of them seem to be out of date). 

PLEASE can someone help me!

/izo\

---

### Post by pmaconi on 2008-05-27
Edit /etc/X11/xorg.conf and add the following section: 
```
Section "Files"
      	FontPath "/pathToFonts/.fonts"
EndSection
```

Then edit /etc/fonts/conf.avail/51-local.conf and add ```
<dir>/pathToFonts/.fonts</dir>
```

Remember to replace /pathToFonts/ with the actual path. Mine is /home/pmaconi/.fonts. Then run ```
sudo fc-cache -fv
``` in a terminal.

---

### Post by Izobalax on 2008-05-28
> **pmaconi said:**
> Edit /etc/X11/xorg.conf and add the following section: 
```
Section "Files"
      	FontPath "/pathToFonts/.fonts"
EndSection
```

Then edit /etc/fonts/conf.avail/51-local.conf and add ```
<dir>/pathToFonts/.fonts</dir>
```

Remember to replace /pathToFonts/ with the actual path. Mine is /home/pmaconi/.fonts. Then run ```
sudo fc-cache -fv
``` in a terminal.
Thanks for that pmaconi, unfortunately I'm still not able to select the fonts. 

/izo\

---

### Post by pmaconi on 2008-05-28
Then you probably need to reconfigure fontconfig to use bitmapped fonts.
```
sudo dpkg-reconfigure fontconfig
```
Followed by:
```
sudo dpkg-reconfigure fontconfig-config
```
Answer Native, Automatic, and Yes for the questions. Let me know if that works (you may need to redo the following code afterwards, I'm not sure. Let me know if that works).```
sudo fc-cache -fv
sudo dpkg-reconfigure fontconfig
```

---

### Post by Izobalax on 2008-05-31
That worked! You're a star! Thank you!

/izo

---

### Post by pmaconi on 2008-05-31
No problem!

---

### Post by TheFruitStandMan on 2010-11-01
I have the same problem, but i am using Ubuntu 10.10: Maverick Meerkat. The commands above didn't work when I attempted them. The account says I'm new, But I made a new one to go along with my new gmail and my Android "career". That aside, I've been using Ubuntu/Linux in general for 2-3 years now, but we all need help sometimes :)

Bottom line: The commands did not work when I tried them. Dose it matter that they are .pfc and not true type font?

Please and thank you in advance:
Cameron.

---

### Post by Hiim on 2011-02-04
Hi all. I'm having the same problem on 10.04, however, when I try to run "sudo dpgk-reconfigure fontconfig-config, it won't let me. It just waits a few seconds and goes to a new line. Is there any way to fix this?

Thanks in advance.

---

