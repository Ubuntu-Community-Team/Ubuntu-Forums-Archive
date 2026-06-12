---
title: "Can't change photo import program"
date: 2008-05-02
forum: General Help
---

### Post by empthollow on 2008-05-02
I am using Hardy,  F-spot is the default photo import program.  When i insert my SD card into my usb reader f-spot automatically opens.  I would like to change/disable the photo import program.  Normally i would just go to preferences -> Removable drives and media and uncheck digital camera or change the command.  However, i have tried both and neither has any effect.  I cannot find in the gconf-editor where gnome is looking for the fspot import program.  i have tried changing settings and rebooting.  Any ideas would be appreciated.

---

### Post by OldGrey on 2008-05-03
I have a similar issue. I would like to change the default import programme to gThumb, but I do not have clude what the import command is.

---

### Post by Zeratul7 on 2008-05-04
> **OldGrey said:**
> I have a similar issue. I would like to change the default import programme to gThumb, but I do not have clude what the import command is.

I had the same problem, but luckily my laptop still runs gutsy so I managed to copy the g-thumb command to my hardy desktop.
```
gnome-volume-manager-gthumb %h
```

---

### Post by empthollow on 2008-05-04
I changed that command and it does nothing when i insert my sd card.  I ended up removing f-spot altogether and have no import program which works fine for me but i am curious why my changes to the removable drives and media have no effect.

---

### Post by tomasiek on 2008-05-18
It's simple.
1. sudo cp /usr/share/applications/gthumb.desktop ~/.local/share/applications/gthumb.desktop
2. sudo gedit ~/.local/share/applications/gthumb.desktop
3. change in line 138** Exec=gthumb** to   **Exec=gthumb [COLOR="Red"]--import-photo[/COLOR]**
4. In Nautilus go to Edit>Preferences> and choose gthumb... that's all

---

### Post by strabes on 2008-05-18
You could do all that, **OR** you could just open a nautilus window, go to Edit > Preferences, go to the "Media" tab, and change the "Photos" item.

I'm not sure why in Hardy they separated Removable Drives & Media and hid the most useful options away in a nautilus preferences window, but they did.

---

### Post by empthollow on 2008-05-18
Thanks to you both for the posts, i've tried it both ways but in my nautilus preferences after photos it says no programs found.  Just for fun i changed line 138 in the /usr path but it yeilds the same result.

---

### Post by tomasiek on 2008-05-19
@empthollow - i don't remember... but i think that you have to change "run" permissions for ~/.local/share/applications/gthumb.desktop...
[QUOTE="strabes"]open a nautilus window, go to Edit > Preferences, go to the "Media" tab, and change the "Photos" item.[/QUOTE]
In my HH in that place i couldn't change to any else program than f-spot. So i have to find any other solutions.


(uf... jak to dziwnie jak cz&#322;owiek nie u&#380;ywa przez jaki&#347; czas angielskiego a nagle musi w nim pisa&#263;... 

Sorry, but my English is not so good...)


//edit


Oh! I also change in sudo gedit /etc/gnome/defaults.list in this part:
x-content/image-dcf
x-content/image-picturecd

from f-spot to gthumb.

//edit 2

i found this - that's explain all
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD)
(ther is vlc.... but you can use this instruction to change from f-spot to gthumb...)

---

### Post by empthollow on 2008-05-19
great link, thanks to everyone.  Here is the process i used to make it all work.

```
cp /usr/share/applications/gthumb-import.desktop ~/.local/share/applications/gthumb.desktop
```
```
2. gedit ~/.local/share/applications/gthumb-import.desktop
```
```
3. change in line 138 Exec=gthumb to Exec=gthumb --import-photo
```
```
4. gedit ~/.local/share/applications/mimeapps.list
```
5. Changed x-content/image-dcf line to look like so:
```
x-content/image-dcf=gthumb-import.desktop;f-spot-import.desktop;

```
6. Opened nautilus and went to Edit > Preferences, go to the "Media" tab, and change the "Photos" item to gthumb image viewer.

Gnome now uses gthumb to import photos instead of f-spot.  I think gnome has some work to do here.  I don't mind editing files but it seems like the general user would benefit from a more user friendly way to change their import program.

Thanks again to all of you.

---

### Post by Ti-nérisson on 2008-07-05
It works for me with

cp /usr/share/applications/**gthumb.desktop** ~/.local/share/applications/**gthumb-import.desktop**
instead of
cp /usr/share/applications/**gthumb-import.desktop** ~/.local/share/applications/**gthumb.desktop**

and
change in line 138 Exec=gthumb to Exec=gthumb --import-photo**s**
instead of
change in line 138 Exec=gthumb to Exec=gthumb --import-photo

Thanks a lot anyway. :)
I'm going to try with digiKam now.

Edit : It doesn't work with digiKam. I don't understand why.

Here is what I did :
```
cp /usr/share/applications/kde/digikam.desktop ~/.local/share/applications/digikam-import.desktop
```

```
gedit ~/.local/share/applications/digikam-import.desktop
```
changed "Exec=digikam -caption "%c" %i %m" to "Exec=digikam --detect-camera"

```
gedit ~/.local/share/applications/mimeapps.list
```
and added "digikam-import.desktop;" at the end of this line : "x-content/image-dcf=gthumb-import.desktop;f-spot-import.desktop;"

Then I chose digiKam as default application in Nautilus.

This creates a second launcher for digiKam in the menu  with the command "digikam --detect-camera" and it works very well, but when I plug in a sd card or when I right clic on the sd card icon on the desktop and choose digiKam nothing happens.

Any idea?

Edit2 :For Gthumb try "Exec=gnome-volume-manager-gthumb" if you only want to launch the import manager and not the whole application.

Edit3 : Digikam works with this line :"Exec=digikam --download-from %m" (instead of "Exec=digikam --detect-camera").

---

### Post by fragos on 2008-07-05
> **strabes said:**
> You could do all that, **OR** you could just open a nautilus window, go to Edit > Preferences, go to the "Media" tab, and change the "Photos" item.

I'm not sure why in Hardy they separated Removable Drives & Media and hid the most useful options away in a nautilus preferences window, but they did.

I selected "Open Folder" for the photo application. I drag images to the folders I want to store them in. I've already changed the "Open with" Properties for .jpg to Gthumb. Click any image and I'm in Gthumb.

---

### Post by _uli_ on 2008-08-09
A nice and easy way for replacing F-Spot with Digikam or other software under Gnome as default photo import program:

- Open a commandline with Alt+F2 and run "gconf-editor"
- Navigate to "desktop / gnome / volume_manager"
- Change the line "autophoto_command" to read "digikam --detect-camera"

Now every time I plug in my camera, Gnome asks to import fotos, then starts digikam which shows (and imports) the fotos from the camera.

Works for me with Ubuntu 8.04 Hardy.

Hope this helps!

---

### Post by SoCalChris on 2008-08-28
I'm having the same issue. I followed the steps listed above, and have 'digikam --detect-camera' in the Media menu of Nautilus. When I insert the SD card, a button is added to my task list that says "Opening D40", and then it disappears with nothing happening. Digikam runs fine from the menu, and 'digikam --detect-camera' works properly fro the command line. Any suggestions?

Thanks

---

### Post by Ti-nérisson on 2008-09-04
Using "Exec=digikam --detect-camera" in my digikam-import.desktop file didn't work but all I had to do was to replace it with "Exec=digikam --download-from %m". Now it works fine :).

---

### Post by SoCalChris on 2008-09-22
I never got this resolved in 8.04, but it appears to be fixed in 8.10.

I'm using the "Exec=digikam --download-from %m" command that Ti-nérisson suggested, and it's working great.

---

### Post by PhilOSparta on 2008-09-23
> **_uli_ said:**
> A nice and easy way for replacing F-Spot with Digikam or other software under Gnome as default photo import program:

- Open a commandline with Alt+F2 and run "gconf-editor"
- Navigate to "desktop / gnome / volume_manager"
- Change the line "autophoto_command" to read "digikam --detect-camera"

Now every time I plug in my camera, Gnome asks to import fotos, then starts digikam which shows (and imports) the fotos from the camera.

Works for me with Ubuntu 8.04 Hardy.

Hope this helps!

For those that want gthumb: change the autophoto_command to read "**gthumb --import-photos**"

---

