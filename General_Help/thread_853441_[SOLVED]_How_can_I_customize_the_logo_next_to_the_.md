---
title: "[SOLVED] How can I customize the logo next to the Applications Menu?"
date: 2008-07-08
forum: General Help
---

### Post by pofigster on 2008-07-08
So, I've started tinkering around with GTK themes to make my own Dark theme and what not and I've run into one thing that I really can't figure out.

How do I change the icon next to the Applications menu?  I've tried changing /apps/panel/default_setup/objects/menu_bar in gconf-editor to use a custom icon.  Didn't work.

I tried changing the start-here.svg file in /usr/share/icons/Human/scalable/places but that didn't work.

I just want to be able to use my own, custom icon next to the Applications menu.  Does anyone know how to accomplish this?

Also, and this might not be simple, but I noticed in the Christian Edition, their button actually extends beyond the gnome-panel at the top of the screen.  Is that possible to do with a GTK theme or would that require Metacity/Emerald?

---

### Post by walkerk on 2008-07-08
```
gconf-editor
```

now navigate to
[ /apps/panel/objects/menu_bar_screen0/use_custom_icon ] or
[ /apps/panel/default_setup/objects/menu_bar/use_custom_icon ]

that'll get you headed in the right direction. i only remember reading this on the forum...

---

### Post by pofigster on 2008-07-08
The only options I have under /apps/panel/ are default_setup, general and global.

Under default_setup/objects there is only menu_bar, there isn't menu_bar_screen0

Any reason why this might be?

---

### Post by walkerk on 2008-07-08
> **pofigster said:**
> The only options I have under /apps/panel/ are default_setup, general and global.

Under default_setup/objects there is only menu_bar, there isn't menu_bar_screen0

Any reason why this might be?

Not sure... did you check the use_custom_icon option? If not do that and then set the custom_icon path above it...

That ought to do the trick. To be honest, it has been along time since I've used anything other than Openbox & Pypanel so I am going off of vague memories...

---

### Post by sayakb on 2008-07-08
If you have a custom png image for replacement, scale it to **22x22** size. Press Alt+F2 and type in **gksudo nautilus**. Copy the image to /usr/share/icons/active_icon_theme/22x22/places/start-here.png

Note: If you are using a self installed icon theme, goto .icons folder in your home folder and find the active_icon_theme folder there..

---

### Post by pofigster on 2008-07-08
LinuxIsInnovation - I installed the icon theme Gion just so I could try out what you suggested.  After installing it by dropping the .tar.bz2 file into the "Appearance" window I opened up ~/.icons/Gion/22x22/places/ and placed my custom start-here.png file (a blue horses head).

I then used killall gnome-panel to restart the gnome-panel - nothing.  I opened up the Appearance window, switched themes, then switched back.  Nothing changed so I again ran killall gnome-panel

The icon is still the same Ubuntu logo.  Anything I might be doing wrong?

---

### Post by pofigster on 2008-07-08
I'm also curious how to change the "Log off, switch user, lock screen or power down the computer" icon as well.  I've seen the default Ubuntu red power switch and the green running man.  I'd like to be able to manipulate that, but I don't know which file to rename, where it's at, etc...

Thanks!

---

### Post by sayakb on 2008-07-08
Was there a start-here.png file within the ~/.icons/Gion/22x22/places/ folder already? Also, change the icons of other sizes: 24x24, 32x32, scalable etc.
Also, the Shut Down, Restart etc should be in the Actions folder.
I use the AER-OS-XK icons pack (gnome-look.org)

---

### Post by pofigster on 2008-07-08
There wasn't a start-here.png icon already in the folder - do I need then to change the icons in the /usr/share/icons/hicolor folder to get it to change?  I will try adding the appropriatly sized start-here.png file to each of the other folders as well.  And a .svg file to the scalable as well.

---

### Post by sayakb on 2008-07-08
If there wasn't a start-here.png there already, the index.theme file for Gion will also not have an instance of the file. Change /usr/share/icons/gnome/22x22/places start-here.png
I would rather recommend some better looking complete icon theme like NuovoXT.2.2 or AER-OS-XK or Crashbit..

---

### Post by pofigster on 2008-07-10
Alright, so I went through each of the different size folders and added the appropriately sized start-here.png file.  Then I executed killall gnome-panel, but no change.  So, I installed nuovoXT.2.2 as per your suggestion and added the appropriately sized icons to those folders as well.  Again, no change.

I'm curious, do I need to be doing anything with an icon-cache or anything?  I read somewhere that I need to run gtk-update-icon-cache --force [icon set]
When I do this, however, it reports
```
gtk-update-icon-cache: No theme index file in 'nuoveXT.2.2'.
If you really want to create an icon cache here, use --ignore-theme-index.
```

Thanks for all your help thus far!  I'm hoping to get this thing whipped!

---

### Post by Joshuwa on 2008-07-10
Here is the simple, easy way:

[http://www.gnome-look.org/content/show.php/Give+me+Foot+(script)?content=81420](http://www.gnome-look.org/content/show.php/Give+me+Foot+(script)?content=81420)

By default it changes the Ubuntu (or Mint, Debian, etc) logo to the Gnome foot. But changed the foot graphic to anything of your liking, then running the script, will make the appropriate change.

---

### Post by pofigster on 2008-07-10
Ok - I figured it out! It's a combination of the last two suggestions. You have to copy the start-here.png file to whatever icon set you're using. Make sure you have a properly scaled image in at least the 16x16, 22x22, 24x24, 32x32 and scalable "action" folders.

Then, from the CL type:
```
gtk-update-icon-cache /home/user/.icons/icon set/
```where you, of course, enter the actual path to the icon set that you are using. Then run:
```
killall gnome-panel
```and - poof! - it should work!

Thanks everybody for your suggestions!

---

