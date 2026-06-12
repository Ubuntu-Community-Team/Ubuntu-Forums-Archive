---
title: "The fonts in Gome are too small"
date: 2007-05-31
forum: General Help
---

### Post by fearevilleet on 2007-05-31
Hi guys,

I have posted about this before and after several months of trying I still can not figure out this font issue. Since I have upgraded to fiesty the fonts in gome and many other applications are very small. I have tried increasing the text size and tried different fonts from the fonts menu but it end up looking like wrong as seen in the screen shot.   Other applications like firefox the font is fine. I am sure the nvidia drivers are correctly installed because all the effect in fiesty work fine. Is there any way I can adjust the gome font size?

---

### Post by fragos on 2007-05-31
What does System-> Preferences-> Fonts tell you.  It allows you to select a different font for use in different parts of the desktop.  When selecting specific fonts you can also change the point size.  What looks best will depend on your screen resolution and your personal preferences.  With my 1440x900 19" wide screen I use 10 for all except the window title where I use 11 bold.  You separately change the default fonts for applications, document, desktop, window title and fixed width.  Application will use these as defaults but also allow different selections unique to that application.  Acording to your thumbnail you currently have very different point sizes foe each of these.

---

### Post by fearevilleet on 2007-06-01
When I go to s System-> Preferences-> Fonts I have all the fonts set at 32 (but I did try and put all of the options as high as 72), it  did change the menu fonts. and application fonts but not the fonts in the gome file menu at the top.  I also tried changing the dpi from the fonts menu  from 10 all the way up to 150 but I did not see any changes in the fonts. 


In certain applications like amarok you can increase the font size with in the application but it only partially  worked as seen in the attached screen shoot. The text on the left hand side is too small yet the songs on the right hand side look ok after I increased the font size. This happens in other applications as well.  You can also see how the fonts in firefox look normal.  

I am really at a loss at what to do, and i do appericate any help you can give me.

---

### Post by fearevilleet on 2007-06-02
I filled out a bug report at the[ ubuntu launch pad. ]("https://bugs.launchpad.net/ubuntu/+bug/118327") for this issue.

---

### Post by skip27 on 2007-06-02
> **fearevilleet said:**
> Hi guys,

I have posted about this before and after several months of trying I still can not figure out this font issue. Since I have upgraded to fiesty the fonts in gome and many other applications are very small. I have tried increasing the text size and tried different fonts from the fonts menu but it end up looking like wrong as seen in the screen shot.   Other applications like firefox the font is fine. I am sure the nvidia drivers are correctly installed because all the effect in fiesty work fine. Is there any way I can adjust the gome font size?

First, are you running @ 96x96DPI? In the console, do:

xdpyinfo | grep resolution

If that's correct, then check if you have a .fonts.conf. If you do, delete .fonts.conf after backing it up and then check your /etc/fonts directory. You should only have two directories in /etc/fonts: conf.avail and conf.d. You should only have two files in /etc/fonts: fonts.conf and fonts.dtd. Backup and remove everything else. Run sudo dpkg-reconfigure fontconfig-config and select the settings best suited for your screen (for LCD: Native/Automatic/No). Log out, restart X (ctrl-alt-backspace) and log back in. Additionally, FOR NOW, make sure that you're only using Bitstream Vera Sans and/or DejaVu Sans. If these fonts can render correctly, we can start exploring /w other fonts.

Another thing you might want to try is creating another user and logging in as that user. If the fonts render correctly as another user, we've isolated the problem and know that it's user-dependent and not system-wide.

Oh, and we should probably check the basics: fontconfig is installed on your system, right? If you couldn't execute what I told you above (sudo dpkg-reconfigure fontconfig-config), there's something wrong. I know it's the proverbial "is your computer plugged in question," but just in case something went awry when upgrading from Edgy to Feisty, this is a good place to check first.

Oh, one more thing: even if you run Gnome, run 'kcontrol' and see what the font settings are there. Even though I use Ubuntu, I have to use 'kcontrol' to fine-tune certain KDE-based applications, like Amarok. kcontrol always creates a ~/.fonts.conf file, so delete it afterwards.

---

### Post by Bloch on 2007-06-02
Hi fearevilleet,
I've got the same wallpaper :-)

---

### Post by fragos on 2007-06-02
xdpyinfo gave me 89x87 even though my resoltion was set 96.  I tried setting my resolution to 88 and fonts on the screen did shrink a little but I believe the end result sharper than before so I'll keep it that way.  One thing interesting is the xdpyinfo still says resolution 89x87.  This leads me to believe that although related these parameters don't effect each others value but being different negatively impacts the visual appearance of fonts.

---

