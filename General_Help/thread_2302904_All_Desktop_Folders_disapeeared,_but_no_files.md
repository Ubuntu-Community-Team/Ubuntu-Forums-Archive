---
title: "All Desktop Folders disapeeared, but no files"
date: 2015-11-14
forum: General Help
---

### Post by Benjamin_Hall on 2015-11-14
I just locked my computer as per usual, and when I came back, entered my password, every single folder on my desktop had disappeared. All the individual files are still there, but every folder has disappeared. I've tried the “ls -l ~/Desktop” command but that doesn't return anything more than what I see. Please help.

---

### Post by ajgreeny on 2015-11-14
I don't understand what you mean; did you have all your /home folders showing on the desktop of your system, and if so were they symbolic links to the folders, or launchers for the file-manager pointing to the folders?

You say the individual files are still there; do you mean the files directly in the main home folder are still there, but none of those that were in Documents, Music, Downloads, etc etc?
```
ls -l ~/Desktop
```would not normally show all those folders, hence my question above but you can see if the folders are still in existence by running command ```
find -name Documents
```which should give output **./Documents** if the folder is still in your home.

---

### Post by Benjamin_Hall on 2015-11-14
All folders in my Desktop folder (/home/benjamin/Desktop/) have disappeared; all files in that folder (/home/benjamin/Desktop/) however are still there.

---

### Post by ajgreeny on 2015-11-14
What folders did you have in /home/benjamin/Desktop previously?

Normally there would be none, so I am still a bit uncertain what you are expecting to see.

Can you still get to all your docs, music, videos etc etc that would normally be in the main home folders, or are they what has disappeared?

---

### Post by Benjamin_Hall on 2015-11-14
I had around five folders that I had created. All the home folders are still present; I have never used those folders though, as I prefer having everying on my Desktop.

---

### Post by ajgreeny on 2015-11-15
Did you run that **find** command I suggested?

---

### Post by Benjamin_Hall on 2015-11-15
Yes, I did. it returns with "Permission denied"

---

### Post by ajgreeny on 2015-11-16
> **Benjamin_Hall said:**
> Yes, I did. it returns with "Permission denied"
That is very strange!  You are not asking it to do anything that should be denied to you so I think we need to look a bit further at ownership of your home folder.

Run command ```
ls -la
``` in a terminal and show us the output in code tags please.
See **Code-Tags** how-to in my signature if you don't know how.

---

### Post by Benjamin_Hall on 2015-11-16
```

jamin/.config/fontconfig/fonts.conf
-rw-r--r--   1 benjamin benjamin    137571 May 21  2014 free-shipping-canada.png
drwx------   4 benjamin benjamin      4096 Nov 14 09:40 .gconf
drwx------   2 benjamin benjamin      4096 Oct 13  2011 .gconfd
drwx------   4 benjamin benjamin      4096 Aug 31  2011 .gegl-0.0
drwxrwxr-x   2 benjamin benjamin      4096 Jun  8 12:55 .gervill
drwxr-xr-x  22 benjamin benjamin      4096 Apr  4  2013 .gimp-2.6
drwxr-xr-x  24 benjamin benjamin      4096 Nov  6 21:41 .gimp-2.8
-rw-r-----   1 benjamin benjamin         0 Apr  8  2014 .gksu.lock
drwx------   3 benjamin benjamin      4096 Oct 18  2011 .gnash
drwx------   8 benjamin benjamin      4096 Nov 13 07:54 .gnome2
drwx------   2 benjamin benjamin      4096 Aug 31  2011 .gnome2_private
drwx------   3 benjamin benjamin      4096 Jun 10  2014 .gnupg
drwx------   2 benjamin benjamin      4096 Oct 11  2011 .gnusound
drwxrwxr-x   4 benjamin benjamin      4096 Sep  5  2013 GNUstep
drwx------   2 benjamin benjamin      4096 Dec 28  2013 .gphoto
drwxr-xr-x   2 benjamin benjamin      4096 May 28  2014 .gstreamer-0.10
-rw-rw-r--   1 benjamin benjamin       212 Dec 18  2012 .gtk-bookmarks
-rw-r--r--   1 benjamin benjamin        82 Oct 24  2012 .gtkrc-2.0
-rw-r--r--   1 benjamin benjamin       285 Jan  3  2012 .gtkrc-2.0-kde4
-rw-rw-r--   1 benjamin benjamin       951 Dec 14  2011 .gtk-recordmydesktop
drwx------   2 benjamin benjamin      4096 Aug 31  2011 .gvfs
drwxr-----   2 benjamin benjamin      4096 Sep  2  2011 .hplip
-rw-------   1 benjamin benjamin    189422 Nov 14 09:40 .ICEauthority
drwxr-xr-x 247 benjamin benjamin     12288 Jun  8  2012 .icons
-rw-rw-r--   1 benjamin benjamin   1488880 Jun 23 10:22 image3.JPG
-rw-------   1 benjamin benjamin   3577958 Oct  5 06:24 IMG_0704.JPG
-rw-------   1 benjamin benjamin   3640877 Oct  5 06:24 IMG_0706.JPG
-rw-------   1 benjamin benjamin   4387493 Oct  5 06:24 IMG_0709.JPG
-rw-------   1 benjamin benjamin   3885824 Oct  5 06:24 IMG_0710.JPG
-rw-------   1 benjamin benjamin   4042350 Oct  5 06:24 IMG_0711.JPG
-rw-------   1 benjamin benjamin   3253223 Oct  5 06:24 IMG_3836.JPG
-rw-------   1 benjamin benjamin   3103800 Aug  7 20:18 IMG_7476.1.JPG
-rw-------   1 benjamin benjamin   3103800 Oct  5 06:24 IMG_7476.2.JPG
-rw-rw-r--   1 benjamin benjamin    479628 Aug  7 20:20 IMG_7476.JPG
-rw-------   1 benjamin benjamin   3208477 Oct  5 06:24 IMG_7477.1.JPG
-rw-------   1 benjamin benjamin   3208477 Aug  7 20:18 IMG_7477.JPG
-rw-------   1 benjamin benjamin   3517885 Oct  5 06:24 IMG_7478.1.JPG
-rw-------   1 benjamin benjamin    523540 Aug  7 20:20 IMG_7478.JPG
-rw-rw-r--   1 benjamin benjamin        92 May 14  2012 .iriverter.conf
-rw-rw-r--   1 benjamin benjamin      1131 Nov 21  2013 .iriverter.log
drwxr-xr-x   4 benjamin benjamin      4096 Jun  8 12:55 .java
drwxrwxr-x   3 benjamin benjamin      4096 Mar 27  2012 .k3d
drwx------   6 benjamin benjamin      4096 Mar 27  2015 .kde
-rw-------   1 benjamin benjamin       386 Sep 18  2012 .kderc
drwxr-xr-x   4 benjamin benjamin      4096 Oct 12  2011 .ktoon
-rw-rw-r--   1 benjamin benjamin       176 Apr 16  2012 .languagetool-ooo.cfg
drwxr-xr-x   3 benjamin benjamin      4096 Aug 31  2011 .libreoffice
drwxr-xr-x   3 benjamin benjamin      4096 Aug 31  2011 .local
-rw-rw-r--   1 benjamin benjamin         0 Feb 24  2012 .~lock.Untitled 1.odp#
drwx------   3 benjamin benjamin      4096 May  9  2012 .log
drwxrwxr-x   2 benjamin benjamin      4096 Jan  4  2012 .luciole
drwx------   3 benjamin benjamin      4096 Aug 31  2011 .macromedia
drwx------   3 benjamin benjamin      4096 Sep 13  2011 .mission-control
drwx------   5 benjamin benjamin      4096 May  2  2012 .mozilla
-rw-r--r--   1 benjamin benjamin   2982244 Mar 20  2014 mozilla.pdf
drwxrwxr-x   2 benjamin benjamin      4096 Nov 10  2011 .mplayer
drwxrwxr-x   4 benjamin benjamin      4096 Feb 20  2012 .mricron
-rw-rw-r--   1 benjamin benjamin    321168 Oct 16  2014 MuleDeerPattern1.pdf
drwxrwxr-x   8 benjamin benjamin      4096 Sep 10 10:28 MuseScore2
-rw-rw-r--   1 benjamin benjamin       261 Jan 10  2015 mwf_config
drwxrwxr-x   3 benjamin benjamin      4096 Nov  4  2014 My Digital Editions
drwxrwxr-x   2 benjamin benjamin      4096 Dec  1  2011 .nbprofiler
drwxrwxr-x   2 benjamin benjamin      4096 Dec  1  2011 .netbeans
drwxrwxr-x   2 benjamin benjamin      4096 Feb 20  2012 .npm
drwxrwxr-x   4 benjamin benjamin      4096 Dec 13  2011 .onboard
drwxr-x---   6 benjamin benjamin      4096 Oct 17 19:23 .openshot
drwxr-x---   6 benjamin benjamin      4096 May 23  2012 .openshot_backup
-rw-------   1 benjamin benjamin  85826620 Dec 11  2013 OtrHorizonsWest13Of13Eps.zip
-rw-------   1 benjamin benjamin 138817617 Dec 11  2013 OTRR_Frontier_Fighters_Singles.zip
-rw-r--r--   1 benjamin benjamin   3595535 Nov 11  2013 output.pdf
-rw-r--r--   1 benjamin benjamin        35 Oct 24  2012 .pam_environment
drwxrwxr-x   2 benjamin benjamin      4096 Oct 22  2013 .pdfedit
drwxrwxr-x   2 benjamin benjamin      4096 Jul 21 13:19 pdfscissors
-rw-r--r--   1 benjamin benjamin  29757486 Nov  6  2013 Pedal-Operated Wooden Scroll Saw.wav
-rw-------   1 benjamin benjamin 471423542 Oct 25  2013 peril_finders_1305_librivox.zip
drwxr-xr-x   5 benjamin benjamin     20480 May 12  2015 Pictures
-rw-------   1 benjamin benjamin 311545698 Oct 25  2013 pike_dyke_1003_librivox.zip
drwx------   3 benjamin benjamin      4096 Aug 31  2011 .pki
drwxr-xr-x  14 benjamin benjamin      4096 Nov 14 07:09 .PlayOnLinux
lrwxrwxrwx   1 benjamin benjamin        40 Mar 12  2014 PlayOnLinux's virtual drives -> /home/benjamin/.PlayOnLinux//wineprefix/
-rw-r--r--   1 benjamin benjamin       675 Oct 24  2012 .profile
-rw-rw-r--   1 benjamin benjamin    102776 Dec 12  2014 programform_theorypdf.pdf
drwx------   2 benjamin benjamin      4096 Oct 25 16:21 .pulse
-rw-------   1 benjamin benjamin       256 Aug 31  2011 .pulse-cookie
drwxrwxr-x   2 benjamin benjamin      4096 Mar  7  2013 .qt
drwxrwxr-x   3 benjamin benjamin      4096 Sep 10 19:57 Rallentando Software
-rw-------   1 benjamin benjamin    141969 Oct 18  2013 .recently-used
-rw-------   1 benjamin benjamin       363 Nov  2 09:47 .RLPlot
drwxr-xr-x   2 benjamin benjamin      4096 Nov 10 11:19 rosegarden
-rw-------   1 benjamin benjamin    673792 Jan 21  2014 Saw.doc
-rw-------   1 benjamin benjamin   2013611 Apr 17  2015 scan0046.pdf
-rw-------   1 benjamin benjamin   1468076 Apr 17  2015 scan0047.pdf
-rw-------   1 benjamin benjamin   1852883 Apr 20  2015 scan0049.pdf
-rw-------   1 benjamin benjamin    417147 Jun 13 19:43 scan0066.pdf
-rw-------   1 benjamin benjamin     48139 Oct  1 09:46 scan0089.pdf
-rw-------   1 benjamin benjamin   2499518 Oct  9 10:27 scan0096.pdf
-rw-rw-r--   1 benjamin benjamin     34096 Sep  2 14:35 Schedule.odt
-rw-------   1 benjamin benjamin   1436750 Dec  9  2013 Sharpening__1-day_Hands-On_-_Flyer-4_pg_updated_10-14-121.pdf
-rw-------   1 benjamin benjamin    375545 Dec  9  2013 sharpening.pdf
-rw-rw-r--   1 benjamin benjamin      9699 Sep 26 09:40 Sheet1.odt
drwxrwxr-x   3 benjamin benjamin      4096 Jun  4  2012 .shutter
drwx------   9 benjamin benjamin      4096 Nov  9 18:24 .Skype
drwx------   2 benjamin benjamin      4096 Nov 16 06:02 .spamassassin
drwx------   4 benjamin benjamin      4096 Nov 19  2012 .speech-dispatcher
drwxrwxr-x   2 benjamin benjamin      4096 May  9  2012 .spumux
drwx------   2 benjamin benjamin      4096 May  5  2012 .ssh
drwxr-xr-x   2 benjamin benjamin      4096 Feb 28  2012 .stopmotion
-rw-r--r--   1 benjamin benjamin         0 Aug 31  2011 .sudo_as_admin_successful
drwxr-xr-x   3 benjamin benjamin      4096 Nov  6  2013 .swt
drwx------   2 benjamin benjamin      4096 May 16  2012 .synaptic
drwxr-xr-x   4 benjamin benjamin      4096 May  2  2012 .themes
drwx------   5 benjamin benjamin      4096 May 29  2012 .thumbnails
drwx------   4 benjamin benjamin      4096 Mar 22  2012 .thunderbird
-rw-rw-r--   1 benjamin benjamin    228057 Oct 16  2014 Timeline1.png
drwxrwxr-x   2 benjamin benjamin      4096 Jun  7  2012 Ubuntu One
-rw-r--r--   1 benjamin benjamin     35219 Feb 21  2014 Untitled 2.pdf
-rw-rw-r--   1 benjamin benjamin       936 Nov 12  2014 Untitled.html
drwxr-xr-x   2 benjamin benjamin      4096 Nov  6 16:48 Videos
drwx------   2 benjamin benjamin      4096 May 23  2014 .VirtualBox
drwxrwxr-x   3 benjamin benjamin      4096 Dec  1  2011 .visualvm
-rw-rw-r--   1 benjamin benjamin    707495 Dec  6  2014 Volume1.pdf
drwxrwxr-x   3 benjamin benjamin      4096 Apr 19  2012 .wallpaper
-rw-rw-r--   1 benjamin benjamin        44 Apr 13  2012 .wav
-rw-rw-r--   1 benjamin benjamin        60 Jan 21  2012 .weather.cfg
-rw-rw-r--   1 benjamin benjamin    155844 Oct 16  2014 Wildlife in Relief Carving.pdf
drwxr-xr-x   4 benjamin benjamin      4096 Nov 13 15:23 .wine
drwxrwxr-x   2 benjamin benjamin      4096 Nov  6  2013 .winff
-rw-------   1 benjamin benjamin      1703 Nov 14 09:40 .Xauthority
-rw-rw-r--   1 benjamin benjamin       169 May 27  2013 .Xauthority.0MKYXW
-rw-rw-r--   1 benjamin benjamin       169 Sep 17  2013 .Xauthority.1QIC3W
-rw-rw-r--   1 benjamin benjamin       169 Apr 25  2013 .Xauthority.BEEUVW
-rw-rw-r--   1 benjamin benjamin       169 May  6  2013 .Xauthority.FSHYWW
-rw-rw-r--   1 benjamin benjamin         0 Sep 18  2013 .Xauthority.HSTP3W
-rw-rw-r--   1 benjamin benjamin       169 Apr 30  2013 .Xauthority.TZ8QWW
-rw-------   1 benjamin benjamin        88 Jan 26  2012 .xfigrc
-rw-rw-r--   1 benjamin benjamin      7458 Apr 16  2012 .xscreensaver
-rw-r--r--   1 benjamin benjamin       834 Sep 30  2011 .xscreensaver-getimage.cache
-rw-------   1 benjamin benjamin      1274 Nov 14 09:40 .xsession-errors
-rw-------   1 benjamin benjamin         0 Apr  1  2013 .xsession-errors-:1
-rw-------   1 benjamin benjamin         0 Jan 21  2012 .xsession-errors-:2
-rw-------   1 benjamin benjamin      1274 Nov 13 13:24 .xsession-errors.old
-rw-------   1 benjamin benjamin  45624481 Oct 25  2013 youngrobinhood_1203_librivox.zip
-rw-rw-r--   1 benjamin benjamin    636019 Apr 10  2012 .zip
benjamin@schoolroom-ben:~$ 



```

---

### Post by ajgreeny on 2015-11-17
Everything there belongs to you as it should, so lets see if we can find a folder called Documents anywhere in the filesystem with commands ```
sudo updatedb
locate Documents
```

This is getting very baffling, and I still do not understand why the find command returns a "Permission denied";  perhaps we should try that as root with ```
sudo find -name Documents
``` though that should not be necessary.

---

