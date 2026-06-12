---
title: "Wallch wallpaper changer"
date: 2016-06-06
forum: General Help
---

### Post by hornetster on 2016-06-06
Have installed Wallch on a newly installed 16.04 x64, but can't get it to show any pictures.
Seems to run ok, and allows me to configure it, but I never get a wallpaper (have the desktop configured otherwise as just a solid colour). Even in the setup page, I can see the thumbnails of the pictures (just standard photos, straight off a number of different cameras), but clicking on a thumbnaiil, in the preview window, just remains blank, and clicking on a pic and selecting set as wallpaper does nothing. Apart from that, no errors etc.
Thanks.

---

### Post by yetimon_64 on 2016-06-06
There is one setting you could check with the next terminal command, copy and paste the command to a terminal, press enter, and see what it reports ... ```
gsettings get org.gnome.desktop.background draw-background
``` If it comes back as "false", run the next command then try using wallch again ... ```
gsettings set org.gnome.desktop.background draw-background true
``` That key is reported to be deprecated and is supposedly ignored but without it set here my 16.04 install wouldn't give me any background image just a blank colour initially. According to the description for it in dconf-editor ... > Have GNOME draw the desktop background. DEPRECATED: This key is deprecated and ignored. May be worth a try changing it if it reports "false" to the first command box, the second command box above will actually change it to "true".  

**Edit**: an afterthought, also check the "picture-options" at the same key "org.gnome.desktop.background" is set to any setting other than "none". That can also block images showing at times if it is set to "none". Set it to stretched or scaled etc. example code: ```
gsettings get org.gnome.desktop.background picture-options
```... to test. ```
gsettings set org.gnome.desktop.background picture-options stretched
```... to set as "stretched". **Edit 2: ** just below the wallch preview window is a drop down menu to set this, you don't really need these last two terminal commands. Just ensure that settings box is NOT blank.

---

### Post by hornetster on 2016-06-06
Thanks for those suggestions.
First setting was set to True, and 2nd to None.
Changing the second to stretched didn't achieve anything, unfortunately...

---

### Post by yetimon_64 on 2016-06-06
> **hornetster said:**
> Thanks for those suggestions.
First setting was set to True, and 2nd to None.
Changing the second to stretched didn't achieve anything, unfortunately...

Ok, one last thought, have you actually run the wallch command from terminal to check for any other errors that may not be obvious in the GUI ?

---

### Post by hornetster on 2016-06-07
Nope, no errors, just a nice "See ya next time!" when you quit.....
Very polite! :-)
Thanks.

---

