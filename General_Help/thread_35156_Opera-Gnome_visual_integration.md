---
title: "Opera-Gnome visual integration"
date: 2005-05-17
forum: General Help
---

### Post by tread on 2005-05-17
For anyone here who uses opera in gnome ..  I finally got it looking integrated with clearlooks .. I'll post a screenshot when I get home. But I was thinking, maybe a thread that collects info about the customizations made would be nice. Otherwise if you have no kde, it just looks awful in gnome.

I can put up clearlooks-opera visual integration steps.

---

### Post by tread on 2005-05-18
[Screenshot](http://www.d.umn.edu/~salu0005/wallpapers/Screenshot.png)

Gnome theme: Clearlooks
Opera theme: Marina

Opera:
Interface menus font set to: Bitstream Vera Sans, adjust size to taste. I am using that font for all almost all the dialogs.


Download and install qtconfig.
Qtconfig options: GUI style - CDE
Click Tune palette, change the button and background colours to:
h/s/v: 30 13 231
r/g/b 231 225 219

Change .fonts.conf in your home to: (note, not my own, got this from another howto)
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>

---

### Post by Pedric on 2005-08-03
Tread, what opera package did you install? I cannot get anti-aliased fonts in the opera menues with the statically linked package from opera.com...

---

### Post by bugmenot on 2005-08-04
[QUOTE=Pedric]Tread, what opera package did you install? I cannot get anti-aliased fonts in the opera menues with the statically linked package from opera.com...[/QUOTE]

This is a well known problem. The static package (.1) simply does not support antialiasing. You should go for the .5 package if possible. Available on [Opera's FTP](ftp://ftp.opera.com/pub/opera/linux/802/final/en/i386/shared/).

---

### Post by Pedric on 2005-08-04
That did it, thanks.

---

### Post by cowlip on 2005-08-10
This isn't exact, but if you go into "Appearance" under the Tools menu, you can choose different colour schemes at the bottom.  I like to choose them to match Gnome, and sometimes not :D

---

### Post by tread on 2005-08-10
Thanks, I'll try that out. I use qtconfig to change colours, but its a pain. This reminds me, I better post some other themes I matched, if only for my own record :)

---

### Post by matt_madison on 2005-08-17
A quick question.  Do the menus/dialogs look good after this modification too?  Or is it just what can be seen in the screenshot?  Personally I do not use Opera because it looks like absolute crap imo (the dialogs/menus), but if this would fix it, that would be great.  Thanks  :)

---

### Post by tread on 2005-08-17
The menus/dialogs don't look so great, I'm afraid. But you can tweak them till they are at an acceptable level of non-greatness :) I really like the usability opera gives me, which is why I prefer it. But if appearance is substantially more important, its better to stick with firefox.

---

### Post by matt_madison on 2005-08-17
Well combining the info from a few threads, I think I have now figured out how to make the menus look good.  

First you must have the shared-qt version of Opera, not the static.  Which you can get here:  [ftp://ftp.opera.com/pub/opera/linux/802/final/en/i386/shared/opera_8.02-20050727.5-shared-qt_en_sarge_i386.deb](ftp://ftp.opera.com/pub/opera/linux/802/final/en/i386/shared/opera_8.02-20050727.5-shared-qt_en_sarge_i386.deb)

Here is the part I do not know about.  If you have kde installed, just do this:  Change your opera link to:  "opera --style default"

Note:  "default" could also be the name of a theme.


If you don't have kde installed, do whatever it is you need to do, sorry but I have no clue.


Also, you can use this theme, which look similar to clearlooks on gnome (according to another thread, I have not checked this out yet):  Polymer QT Theme

---

### Post by james_mad on 2005-08-17
Here is a screenshot of the right click menu with the kde theme "plastik."  (Also using the defualt opera theme)

[[IMG]http://img140.imageshack.us/img140/3452/operarightclickmenu4gg.th.png[/IMG]](http://img140.imageshack.us/my.php?image=operarightclickmenu4gg.png)

Ignore the ugliness of my Gnome and Opera :)

---

### Post by tread on 2005-08-18
Thanks for the --style tip Matt! And James, I think you forgot the screenshot  :razz:

---

### Post by matt_madison on 2005-08-18
[http://img140.imageshack.us/img140/3452/operarightclickmenu4gg.png](http://img140.imageshack.us/img140/3452/operarightclickmenu4gg.png)


Here is the screenshot, not sure why it did not show.

edit... Still not working, I will post it when I jump on to linux later.

---

### Post by Pedric on 2005-08-31
Also, change Tools->Preferences->Advanced->Programs->Source viewer to gedit (or some editor of your choice). 

Next, click "handlers for saved files" and there, change the program for files and directories to gnome-open. This will enable you to open downloaded files through Opera using gnome's mimetype settings.

---

