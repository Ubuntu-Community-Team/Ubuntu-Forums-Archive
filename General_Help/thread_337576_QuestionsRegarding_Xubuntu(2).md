---
title: "QuestionsRegarding Xubuntu(2)"
date: 2007-01-13
forum: General Help
---

### Post by DougieFresh4U on 2007-01-13
Good Morning Community!:)  I have very recently switched to Xubuntu (from Ubuntu) on my one older Intel machine. My 2 questions are: Some one please tell me where the "Take Screenshot" can be found and also, after installing Swiftfox browser from Automatix 2 and creating desktop launcher, the launcher is not the symbol for Swiftfox but some 'ugly' little square nothing box and if I new how to take screenshot I would show it! ](*,)  Thanks for listening to my pettiness :)

---

### Post by taurus on 2007-01-13
You can use Gimp to take a snapshot of your desktop or just a window.  And if you want to do that from a terminal, then you need to install imagemagick and use the import command then.

Use the right button and click the launcher for swiftfox.  Go to property and change the icon for it.

---

### Post by DougieFresh4U on 2007-01-13
Ah, good morning taurus. I cannot change that swiftfox icon

---

### Post by taurus on 2007-01-13
What does ~/Desktop/swiftfox.desktop look like anyway?

```
cat ~/Desktop/swiftfox.desktop
```

---

### Post by DougieFresh4U on 2007-01-13
dougie@DougiesToyBox:~$ cat ~/Desktop/swiftfox.desktop
cat: /home/dougie/Desktop/swiftfox.desktop: No such file or directory
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-13
How did you place a launcher on your desktop for swiftfox?  What about the output of this command?

```
ls -la ~/Desktop
```

---

### Post by DougieFresh4U on 2007-01-13
dougie@DougiesToyBox:~$ ls -la ~/Desktop
total 76
drwx------  2 dougie dougie 4096 2007-01-12 15:58 .
drwxr-xr-x 38 dougie dougie 4096 2007-01-13 09:38 ..
-rw-r--r--  1 dougie dougie  222 2007-01-10 02:19 Amarok.desktop
-rw-r--r--  1 dougie dougie  182 2007-01-12 12:05 aMSN.desktop
-rw-r--r--  1 dougie dougie  214 2007-01-10 02:19 Exaile!.desktop
-rw-r--r--  1 dougie dougie  248 2007-01-10 02:18 FreeCell Solitaire.desktop
-rw-r--r--  1 dougie dougie  233 2007-01-10 00:22 FrostWire.desktop
-rw-r--r--  1 dougie dougie  222 2007-01-10 02:21 Gaim Internet Messenger.desktop
-rw-r--r--  1 dougie dougie  258 2007-01-10 02:20 GNOME ALSA Mixer.desktop
-rw-r--r--  1 dougie dougie  204 2007-01-10 02:18 KMahjongg.desktop
-rw-r--r--  1 dougie dougie  215 2007-01-10 02:20 Listen Music Player.desktop
-rw-r--r--  1 dougie dougie  241 2007-01-10 02:18 Mahjongg.desktop
-rw-r--r--  1 dougie dougie  225 2007-01-10 02:24 Rhythmbox Music Player.desktop
-rw-r--r--  1 dougie dougie  201 2007-01-10 02:22 Shisen-Sho.desktop
-rw-r--r--  1 dougie dougie  213 2007-01-10 02:19 streamtuner.desktop
-rw-r--r--  1 dougie dougie  249 2007-01-13 09:38 Swiftfox Browser.desktop
-rw-r--r--  1 dougie dougie  193 2007-01-10 02:21 Terminal.desktop
-rw-r--r--  1 dougie dougie  231 2007-01-10 02:21 Thunderbird Mail.desktop
-rw-r--r--  1 dougie dougie  175 2007-01-10 02:19 XMMS Music Player.desktop
dougie@DougiesToyBox:~$ 
created launcher this way and when I started typing swiftfox dropdown gave swiftfox browser option and that is how created

---

### Post by taurus on 2007-01-13
Click the "**No Icon**" and look in /usr/share/pixmaps (which is a default) to see if you see a picture (icon) of swiftfox.

---

### Post by DougieFresh4U on 2007-01-13
nadda!!

---

### Post by taurus on 2007-01-13
Look in /opt/swiftfox to see if there is an icon for it.

```
ls -la /opt/swiftfox
```

---

### Post by DougieFresh4U on 2007-01-13
drwxr-xr-x  6 dougie dougie     4096 2006-10-25 02:42 res
-rwxr-xr-x  1 dougie dougie    10492 2005-10-01 01:36 run-mozilla.sh
drwxr-xr-x  2 dougie dougie     4096 2007-01-10 01:54 searchplugins
-rwxr-xr-x  1 dougie dougie     5264 2007-01-09 23:24 swiftfox
-rwxr-xr-x  1 dougie dougie 13172408 2006-10-25 02:42 swiftfox-bin
**-rwxr-xr-x  1 root   root          4 2007-01-09 23:19 swiftfoxversion**
-rwxr-xr-x  1 dougie dougie    88240 2006-10-25 02:42 updater
-rw-r--r--  1 dougie dougie      145 2005-08-24 15:58 updater.ini
drwxr-xr-x  3 dougie dougie     4096 2007-01-09 23:51 updates
-rwxr-xr-x  1 dougie dougie    20808 2006-10-25 02:42 xpcshell
-rwxr-xr-x  1 dougie dougie    35280 2006-10-25 02:42 xpicleanup
-rwxr-xr-x  1 dougie dougie    87000 2006-10-25 02:42 xpidl
-rwxr-xr-x  1 dougie dougie    32144 2006-10-25 02:42 xpt_dump
-rwxr-xr-x  1 dougie dougie    27020 2006-10-25 02:42 xpt_link

---

### Post by taurus on 2007-01-13
What's in the res directory anyway?

```
cd /opt/swiftfox/res
ls -la
```

Post the putput of this command from a terminal?

```
sudo find / -name swiftfox.* -print
```

---

### Post by DougieFresh4U on 2007-01-13
dougie@DougiesToyBox:~$ cd /opt/swiftfox/res
dougie@DougiesToyBox:/opt/swiftfox/res$ ls -la
total 280
drwxr-xr-x  6 dougie dougie  4096 2006-10-25 02:42 .
drwxr-xr-x 14 dougie dougie  4096 2007-01-13 07:58 ..
-rw-r--r--  1 dougie dougie    52 2004-12-08 14:39 arrowd.gif
-rw-r--r--  1 dougie dougie    49 2004-12-08 14:39 arrow.gif
-rw-r--r--  1 dougie dougie  1015 2003-02-17 19:07 bloatcycle.html                                       dougie@DougiesToyBox:~$ sudo find / -name swiftfox.* -print
/usr/share/applications/swiftfox.desktop
/usr/share/automatix2/conf/swiftfox.desktop
dougie@DougiesToyBox:~$ 


-rw-r--r--  1 dougie dougie   165 2004-12-08 14:39 broken-image.gif
-rw-r--r--  1 dougie dougie 11348 2005-01-17 12:33 charsetalias.properties
-rw-r--r--  1 dougie dougie  8507 2005-04-29 22:57 charsetData.properties
-rw-r--r--  1 dougie dougie    93 2001-05-09 09:35 cmessage.txt
drwxr-xr-x  2 dougie dougie  4096 2006-10-25 02:30 dtd
-rw-r--r--  1 dougie dougie 10566 2005-03-27 06:35 EditorOverride.css
drwxr-xr-x  2 dougie dougie  4096 2006-10-25 02:14 entityTables
drwxr-xr-x  2 dougie dougie  4096 2006-10-25 02:31 fonts
-rw-r--r--  1 dougie dougie 13385 2006-10-25 02:26 forms.css
-rw-r--r--  1 dougie dougie   858 2003-06-25 04:50 grabber.gif
-rw-r--r--  1 dougie dougie   117 2005-07-01 19:58 hiddenWindow.html
drwxr-xr-x  2 dougie dougie  4096 2006-10-25 02:28 html
-rw-r--r--  1 dougie dougie  9568 2006-08-27 17:58 html.css
-rw-r--r--  1 dougie dougie  5561 2005-04-29 22:57 langGroups.properties
-rw-r--r--  1 dougie dougie  5449 2005-04-29 22:57 language.properties
-rw-r--r--  1 dougie dougie   157 2004-12-08 14:39 loading-image.gif
-rw-r--r--  1 dougie dougie 13541 2006-08-16 16:37 mathml.css
-rw-r--r--  1 dougie dougie 11757 2005-02-18 01:13 quirk.css
-rw-r--r--  1 dougie dougie  2076 2004-07-16 15:30 sample.unixpsfonts.properties
-rw-r--r--  1 dougie dougie  2251 2005-05-19 12:07 svg.css
-rw-r--r--  1 dougie dougie   823 2003-06-25 04:50 table-add-column-after-active.gif
-rw-r--r--  1 dougie dougie   826 2003-06-25 04:50 table-add-column-after.gif
-rw-r--r--  1 dougie dougie   826 2003-06-25 04:50 table-add-column-after-hover.gif
-rw-r--r--  1 dougie dougie    50 2004-01-05 09:10 table-add-column-before-active.gif
-rw-r--r--  1 dougie dougie   825 2003-06-25 04:50 table-add-column-before.gif
-rw-r--r--  1 dougie dougie   825 2003-06-25 04:50 table-add-column-before-hover.gif
-rw-r--r--  1 dougie dougie   822 2003-06-25 04:50 table-add-row-after-active.gif
-rw-r--r--  1 dougie dougie   826 2003-06-25 04:50 table-add-row-after.gif
-rw-r--r--  1 dougie dougie   826 2003-06-25 04:50 table-add-row-after-hover.gif
-rw-r--r--  1 dougie dougie   821 2003-06-25 04:50 table-add-row-before-active.gif
-rw-r--r--  1 dougie dougie   825 2003-06-25 04:50 table-add-row-before.gif
-rw-r--r--  1 dougie dougie   825 2003-06-25 04:50 table-add-row-before-hover.gif
-rw-r--r--  1 dougie dougie   835 2003-06-25 04:50 table-remove-column-active.gif
-rw-r--r--  1 dougie dougie   841 2003-06-25 04:50 table-remove-column.gif
-rw-r--r--  1 dougie dougie   841 2003-06-25 04:50 table-remove-column-hover.gif
-rw-r--r--  1 dougie dougie   835 2003-06-25 04:50 table-remove-row-active.gif
-rw-r--r--  1 dougie dougie   841 2003-06-25 04:50 table-remove-row.gif
-rw-r--r--  1 dougie dougie   841 2003-06-25 04:50 table-remove-row-hover.gif
-rw-r--r--  1 dougie dougie  6053 2005-04-28 18:14 ua.css
-rw-r--r--  1 dougie dougie 18967 2004-08-25 19:02 unixcharset.properties
-rw-r--r--  1 dougie dougie    11 1999-02-09 14:11 viewer.properties
-rw-r--r--  1 dougie dougie  3042 2005-07-11 18:22 viewsource.css

---

### Post by taurus on 2007-01-13
How did you install swiftfox anyway?  See if /opt/swiftfox/res/arrow.gif is the right icon for it or not.  Otherwise, you need to hunt down and icon for swiftfox and save it to /usr/share/pixmaps.

---

### Post by DougieFresh4U on 2007-01-14
> **taurus said:**
> How did you install swiftfox anyway?  See if /opt/swiftfox/res/arrow.gif is the right icon for it or not.  Otherwise, you need to hunt down and icon for swiftfox and save it to /usr/share/pixmaps.

Hi taurus. Sorry for running on you yesterday. Mom's WinXP took a s*@t and I was called to rescue and I'm not even gonna get into that one now(a nightmare) but all fixed :evil: :)  Ok, so how do I track down an icon for Swiftfox and I used automatix before I upgrade to Feisty and icon was never there in the beginning. Saying that, Frostwire icon did not appear as well(Automatix as well) but it showed up after a couple of restarts-go figure that one:-?

---

### Post by DougieFresh4U on 2007-01-14
Thank you so much!! Here ya go, top left corner:

---

### Post by taurus on 2007-01-14
Nice looking swiftfox icon there...  ;)

---

