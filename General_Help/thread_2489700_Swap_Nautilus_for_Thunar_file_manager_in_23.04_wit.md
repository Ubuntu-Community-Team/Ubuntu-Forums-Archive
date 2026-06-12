---
title: "Swap Nautilus for Thunar file manager in 23.04 with XFCE"
date: 2023-08-07
forum: General Help
---

### Post by makem2 on 2023-08-07
I am using Ubuntu 23.04 with an XFCE desktop and Thunar file manager. I would like the ability to expand folders which Nautilus gives. Perhaps use Nemo too to have split screen windows?

Is it possible/advisable? I see both can be installed in 22.04.

---

### Post by dragonfly41 on 2023-08-07
I'm still on standard desktop but looking at others for virtual desktops for remote learning.

But on the matter of file manager I might suggest Krusader.

I looked up the refeence but as I write I do not use XFCE .. just watching.

[https://docs.kde.org/trunk5/en/krusader/krusader/faq.html](https://docs.kde.org/trunk5/en/krusader/krusader/faq.html)

---

### Post by #&amp;thj^% on 2023-08-07
> **dragonfly41 said:**
> I'm still on standard desktop but looking at others for virtual desktops for remote learning.

But on the matter of file manager I might suggest Krusader.

I looked up the refeence but as I write I do not use XFCE .. just watching.

[https://docs.kde.org/trunk5/en/krusader/krusader/faq.html](https://docs.kde.org/trunk5/en/krusader/krusader/faq.html)

+1 Krusader is another excellent suggestion:
```
 apt depends krusader
krusader
  Depends: kinit
  Depends: kio
  Depends: libacl1 (>= 2.2.23)
  Depends: libc6 (>= 2.35)
  Depends: libkf5archive5 (>= 5.85.0)
  Depends: libkf5bookmarks5 (>= 5.68.0~)
  Depends: libkf5codecs5 (>= 5.68.0~)
  Depends: libkf5completion5 (>= 5.81.0)
  Depends: libkf5configcore5 (>= 5.68.0~)
  Depends: libkf5configgui5 (>= 5.68.0~)
  Depends: libkf5configwidgets5 (>= 4.98.0)
  Depends: libkf5coreaddons5 (>= 5.68.0~)
  Depends: libkf5guiaddons-bin
  Depends: libkf5guiaddons5 (>= 5.68.0~)
  Depends: libkf5i18n5 (>= 5.68.0~)
  Depends: libkf5iconthemes5 (>= 5.68.0~)
  Depends: libkf5itemviews5 (>= 5.68.0~)
  Depends: libkf5jobwidgets5 (>= 5.70.0)
  Depends: libkf5kiocore5 (>= 5.96.0)
  Depends: libkf5kiofilewidgets5 (>= 5.68.0~)
  Depends: libkf5kiogui5 (>= 5.83.0)
  Depends: libkf5kiowidgets5 (>= 5.92.0)
  Depends: libkf5notifications5 (>= 5.68.0~)
  Depends: libkf5parts5 (>= 5.81.0)
  Depends: libkf5service-bin
  Depends: libkf5service5 (>= 5.69.0)
  Depends: libkf5solid5 (>= 5.68.0~)
  Depends: libkf5textwidgets5 (>= 5.68.0~)
  Depends: libkf5wallet-bin
  Depends: libkf5wallet5 (>= 5.68.0~)
  Depends: libkf5widgetsaddons5 (>= 5.77.0)
  Depends: libkf5windowsystem5 (>= 5.68.0~)
  Depends: libkf5xmlgui5 (>= 5.84.0)
  Depends: libqt5core5a (>= 5.15.1)
  Depends: libqt5dbus5 (>= 5.14.1)
 |Depends: libqt5gui5 (>= 5.12~)
  Depends: libqt5gui5-gles (>= 5.12~)
  Depends: libqt5printsupport5 (>= 5.12~)
  Depends: libqt5widgets5 (>= 5.15.1)
  Depends: libqt5xml5 (>= 5.12~)
  Depends: libstdc++6 (>= 4.1.1)
  Depends: zlib1g (>= 1:1.1.4)
  Recommends: kde-cli-tools
  Recommends: keditbookmarks
  Recommends: kio-extras
  Suggests: arj
  Suggests: ark
  Suggests: bzip2
  Suggests: cpio
  Suggests: kate
 |Suggests: kdiff3
 |Suggests: kompare
  Suggests: xxdiff
  Suggests: kmail
  Suggests: konsole
  Suggests: krename
  Suggests: <lha>
    jlha-utils
    lhasa
 |Suggests: <md5deep>
    hashdeep
  Suggests: <cfv>
  Suggests: okteta
  Suggests: p7zip
  Suggests: rpm
  Suggests: unace
 |Suggests: unrar
 |Suggests: unrar-free
  Suggests: rar
  Suggests: unzip
  Suggests: zip

```

---

### Post by Holger_Gehrke on 2023-08-07
Should certainly be possible; back in 12.04 I ran standard Ubuntu (Unity at the time IIRC, with nautilus as the file manager) and installed XFCE in addition (mainly because I liked having a 'real' menu instead of a full screen application starter ...) which brought thunar along. Since I didn't try to remove either desktop it ran quite stable and I could choose my desktop when logging in.

But I don't quite understand what you mean by "expanding folders". Do you mean showing sub-directory hierarchies in the left hand panel ? Thunar can do that, but you have to switch that panel from "Bookmark view" to "Tree view". You can do that either from the "View" menu or with the keyboard short cuts ctrl-b (bookmarks) and "ctrl-e"  (tree).

One thing that makes me think it might not be a good thing to do it is Tracker, a desktop search system nautilus depends on. This is known to burn quite a few cycles indexing your files and most people chose XFCE either because they want/need a lighter system because their machine is not the most powerful or because they like the more traditional design of it.

Holger

---

### Post by #&amp;thj^% on 2023-08-07
> **Holger_Gehrke said:**
> 
**_One thing that makes me think it might not be a good thing to do it is Tracker,_** a desktop search system nautilus depends on. This is known to burn quite a few cycles indexing your files and most people chose XFCE either because they want/need a lighter system because their machine is not the most powerful or because they like the more traditional design of it.

Holger
+1 for that heads up, but still the OP makeum2 could stop and mask that service, if wanted.

---

### Post by makem2 on 2023-08-07
> **Holger_Gehrke said:**
> Should certainly be possible; back in 12.04 I ran standard Ubuntu (Unity at the time IIRC, with nautilus as the file manager) and installed XFCE in addition (mainly because I liked having a 'real' menu instead of a full screen application starter ...) which brought thunar along. Since I didn't try to remove either desktop it ran quite stable and I could choose my desktop when logging in.

But I don't quite understand what you mean by "expanding folders". Do you mean showing sub-directory hierarchies in the left hand panel ? Thunar can do that, but you have to switch that panel from "Bookmark view" to "Tree view". You can do that either from the "View" menu or with the keyboard short cuts ctrl-b (bookmarks) and "ctrl-e"  (tree).

One thing that makes me think it might not be a good thing to do it is Tracker, a desktop search system nautilus depends on. This is known to burn quite a few cycles indexing your files and most people chose XFCE either because they want/need a lighter system because their machine is not the most powerful or because they like the more traditional design of it.

Holger

I mean:

[https://averagelinuxuser.com/ubuntu-23-04-after-install/#2-enable-expanded-folder-view](https://averagelinuxuser.com/ubuntu-23-04-after-install/#2-enable-expanded-folder-view)

I would also like to know how to do the swap, or, does the fact that I install Nautilus make it the default file manager?

---

### Post by makem2 on 2023-08-07
> **1fallen said:**
> +1 for that heads up, but still the OP makeum2 could stop and mask that service, if wanted.

Would explain how to do that please?

---

### Post by #&amp;thj^% on 2023-08-07
For Example:
```
systemctl stop libtracker-sparql
```
then Mask it:
```
systemctl mask libtracker-sparql
```
But to be sure if you go with nautilus use this one for real
```
systemctl mask tracker-miner-fs
Unit tracker-miner-fs.service does not exist, proceeding anyway.
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-unit-files ===
Authentication is required to manage system service or unit files.
Authenticating as: Me,,, (me)
Password: 
==== AUTHENTICATION COMPLETE ===
Created symlink /etc/systemd/system/tracker-miner-fs.service &#8594; /dev/null.

```
Good Luck
EDIT: I do have it installed (Nautilus)
result:
```
&#9492;&#9472;> systemctl status tracker-miner-fs
&#9675; tracker-miner-fs.service
     Loaded: masked (Reason: Unit tracker-miner-fs.service is masked.)
     Active: inactive (dead)

```

---

### Post by Holger_Gehrke on 2023-08-07
> **makem2 said:**
> I mean:

[https://averagelinuxuser.com/ubuntu-23-04-after-install/#2-enable-expanded-folder-view](https://averagelinuxuser.com/ubuntu-23-04-after-install/#2-enable-expanded-folder-view)

I would also like to know how to do the swap, or, does the fact that I install Nautilus make it the default file manager?

Hm, not a behaviour I'd want. What happens if I change the sort order ... Also, with multiple folders with lots of files in them expanded like that, I'd always be just one interruption away from having to scroll up to see in what folder I'm actually working ...

Installing a different file manager shouldn't make it the default. There's an app(let) in settings called "Default Applications" (German "Standardanwendungen", English taken from the .desktop-file). The actual name of the program is xfce4-mime-settings. There on the "Tools" ("Werkzeuge") tab is a setting where you can set your file manager.

Holger

---

### Post by makem2 on 2023-08-08
Thank you both.

Edit: There is an app in 'Applications Menu' called 'Application Finder' which will allow change of the active file manager under 'Utilities'.

---

### Post by makem2 on 2023-08-08
> **1fallen said:**
> For Example:
```
systemctl stop libtracker-sparql
```
then Mask it:
```
systemctl mask libtracker-sparql
```
But to be sure if you go with nautilus use this one for real
```
systemctl mask tracker-miner-fs
Unit tracker-miner-fs.service does not exist, proceeding anyway.
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-unit-files ===
Authentication is required to manage system service or unit files.
Authenticating as: Me,,, (me)
Password: 
==== AUTHENTICATION COMPLETE ===
Created symlink /etc/systemd/system/tracker-miner-fs.service &#8594; /dev/null.

```
Good Luck
EDIT: I do have it installed (Nautilus)
result:
```
&#9492;&#9472;> systemctl status tracker-miner-fs
&#9675; tracker-miner-fs.service
     Loaded: masked (Reason: Unit tracker-miner-fs.service is masked.)
     Active: inactive (dead)

```

Nautilus is operating correctly but I get this error when trying to stop [COLOR=#000000][FONT=&amp]libtracker-sparql:

[/FONT][/COLOR]```
makem@makem-22:~$ sudo systemctl stop libtracker-sparql[sudo] password for makem: 
Failed to stop libtracker-sparql.service: Unit libtracker-sparql.service not loaded.

makem@makem-22:~$

```

[COLOR=#000000][FONT=&amp]There is a warning when choosing expand folders etc that it will cause more work, especially if remote folders/files.

Edit: Bug report: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=908800](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=908800)

I also find this report: [https://www.linuxuprising.com/2019/07/how-to-completely-disable-tracker.html](https://www.linuxuprising.com/2019/07/how-to-completely-disable-tracker.html)

Checking tracker version I get:

[/FONT][/COLOR]```

makem@makem-22:~$ tracker3 status
Currently indexed: 30604 files, 1634 folders
Remaining space on database partition: 44.7 GB (50.77%)
All data miners are idle, indexing complete
43 recorded failures


Path                                          Message                                     
&#8230;ments/All_WebSites/travel/img/common/1x1.gif Could not get any metadata for uri:'file://&#8230;
&#8230;/laptop/netgear/NETGEAR_files/h_blue_bar.gif Could not get any metadata for uri:'file://&#8230;
/home/makem/Documents/20220130_162413.jpg     Could not get any metadata for uri:'file://&#8230;
&#8230;lan.action_files/activityi_data/activity.gif Could not get any metadata for uri:'file://&#8230;
&#8230;lan.action_files/activityi_data/ADVID408.gif Could not get any metadata for uri:'file://&#8230;
/home/makem/Documents/20220130_162436.jpg     Could not get any metadata for uri:'file://&#8230;
&#8230;aint files/chp complaint/20220219_142734.jpg Could not get any metadata for uri:'file://&#8230;
&#8230;aint files/chp complaint/20220219_142748.jpg Could not get any metadata for uri:'file://&#8230;
&#8230;aint files/chp complaint/20220219_142848.jpg Could not get any metadata for uri:'file://&#8230;
&#8230;ome/makem/Documents/Flat/20220524_161254.jpg Could not get any metadata for uri:'file://&#8230;
&#8230;ome/makem/Documents/Flat/20220524_161312.jpg Could not get any metadata for uri:'file://&#8230;
&#8230;ome/makem/Documents/Flat/20220524_161345.jpg Could not get any metadata for uri:'file://&#8230;
&#8230;ome/makem/Documents/Flat/20220524_161413.jpg Could not get any metadata for uri:'file://&#8230;
&#8230;ome/makem/Documents/Flat/20220524_161441.jpg Could not get any metadata for uri:'file://&#8230;
&#8230;fireworks example/Complete/images/arrows.gif Could not get any metadata for uri:'file://&#8230;
&#8230;an to uk/BookTripPlan.action_files/blank.gif Could not get any metadata for uri:'file://&#8230;
&#8230;otes/laptop/netgear/NETGEAR_files/bullet.gif Could not get any metadata for uri:'file://&#8230;
&#8230;ebSites/travel/uk/jersey/images/DSC04518.JPG Could not get any metadata for uri:'file://&#8230;
&#8230;vel/EU/portugal/alcoutim/images/P5151230.JPG Could not get any metadata for uri:'file://&#8230;
&#8230;rt/han to uk/BookTripPlan.action_files/e.gif Could not get any metadata for uri:'file://&#8230;
&#8230;el/EU/portugal/albufeira/images/P5181388.JPG Could not get any metadata for uri:'file://&#8230;
&#8230;e/xubuntu/applications/debian-uxterm.desktop Unknown desktop entry type 'Application'    
&#8230;iba - Product Specifications_files/pixel.gif Could not get any metadata for uri:'file://&#8230;
&#8230;p/toshiba/satellite 5100-501_files/pixel.gif Could not get any metadata for uri:'file://&#8230;
&#8230;re/xubuntu/applications/debian-xterm.desktop Unknown desktop entry type 'Application'    
&#8230; Prices & Special Promotions_files/pixel.gif Could not get any metadata for uri:'file://&#8230;
&#8230;otes/laptop/netgear/NETGEAR_files/spacer.gif Could not get any metadata for uri:'file://&#8230;
&#8230;fireworks example/Complete/images/spacer.gif Could not get any metadata for uri:'file://&#8230;
&#8230;es/laptop/netgear/NETGEAR_files/spffffff.gif Could not get any metadata for uri:'file://&#8230;
&#8230;/letters sent to CHP/28_04_16 fire alarm.doc Could not get any metadata for uri:'file://&#8230;
&#8230;k/letters sent to CHP/29_4_16 no stage 2.doc Could not get any metadata for uri:'file://&#8230;
&#8230;usr/share/applications/org.kde.kded5.desktop Unknown desktop entry type 'Service'        
&#8230;untu/applications/Thunar-bulk-rename.desktop Unknown desktop entry type 'Application'    
lines 1-39

```[COLOR=#000000][FONT=&amp]

[/FONT][/COLOR]```
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]makem@makem-22:~$ sudo systemctl --user mask tracker-extract-3.service tracker-miner-fs-3.service tracker-miner-rss-3.service tracker-writeback-3.service tracker-xdg-portal-3.service tracker-miner-fs-control-3.service
[sudo] password for makem: 
Failed to connect to bus: No medium found
makem@makem-22:~$ 

```
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR] I am wondering if the ability to expand folders which on my system I find works well, is it really worth it given the above problems I do not have enough knowledge to deal with?
?

Maybe 23.04 differs from previous versions in this respect.

Edit: this is dated [COLOR=#555555][FONT=&quot]2023/05/16 09:59 but refers to 22.04: [https://itp.uni-frankfurt.de/xwiki/bin/view/Disable%20Gnome%20Tracker/](https://itp.uni-frankfurt.de/xwiki/bin/view/Disable%20Gnome%20Tracker/)




[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2023-08-08
All I know is "tracker-miner-fs-3.service " was the only tracker service HTop could find.
This would all be a different look with Gnome DE  installed.
Now on Debian and XFCE4 with Nautilus:
```
tracker3 status
Currently indexed: 0 files, 0 folders
Remaining space on database partition: 176.5*GB (69.10%)
Data is still being indexed: Estimated less than one second left

```
That is the extend of what the tracker services do.
makem2 I'm not sure what is going on with yours on this:

```
makem@makem-22:~$ tracker3 status
Currently indexed: 30604 files, 1634 folders
Remaining space on database partition: 44.7 GB (50.77%)
All data miners are idle, indexing complete
43 recorded failures


Path                                          Message                                     
&#8230;ments/All_WebSites/travel/img/common/1x1.gif Could not get any metadata for uri:'file://&#8230;
&#8230;/laptop/netgear/NETGEAR_files/h_blue_bar.gif Could not get any metadata for uri:'file://&#8230;
/home/makem/Documents/20220130_162413.jpg     Could not get any metadata for uri:'file://&#8230;
&#8230;lan.action_files/activityi_data/activity.gif Could not get any metadata for uri:'file://&#8230;
&#8230;lan.action_files/activityi_data/ADVID408.gif Could not get any metadata for uri:'file://&#8230;
/home/makem/Documents/20220130_162436.jpg     Could not get any metadata for uri:'file://&#8230;
&#8230;aint files/chp complaint/20220219_142734.jpg Could not get any metadata for uri:'file://&#8230;
&#8230;aint files/chp complaint/20220219_142748.jpg Could not get any metadata for uri:'file://&#8230;
&#8230;aint files/chp complaint/20220219_142848.jpg Could not get any metadata for uri:'file://&#8230;
&#8230;ome/makem/Documents/Flat/20220524_161254.jpg Could not get any metadata for uri:'file://&#8230;
&#8230;ome/makem/Documents/Flat/20220524_161312.jpg Could not get any metadata for uri:'file://&#8230;
&#8230;ome/makem/Documents/Flat/20220524_161345.jpg Could not get any metadata for uri:'file://&#8230;
&#8230;ome/makem/Documents/Flat/20220524_161413.jpg Could not get any metadata for uri:'file://&#8230;
&#8230;ome/makem/Documents/Flat/20220524_161441.jpg Could not get any metadata for uri:'file://&#8230;
&#8230;fireworks example/Complete/images/arrows.gif Could not get any metadata for uri:'file://&#8230;
&#8230;an to uk/BookTripPlan.action_files/blank.gif Could not get any metadata for uri:'file://&#8230;
&#8230;otes/laptop/netgear/NETGEAR_files/bullet.gif Could not get any metadata for uri:'file://&#8230;
&#8230;ebSites/travel/uk/jersey/images/DSC04518.JPG Could not get any metadata for uri:'file://&#8230;
&#8230;vel/EU/portugal/alcoutim/images/P5151230.JPG Could not get any metadata for uri:'file://&#8230;
&#8230;rt/han to uk/BookTripPlan.action_files/e.gif Could not get any metadata for uri:'file://&#8230;
&#8230;el/EU/portugal/albufeira/images/P5181388.JPG Could not get any metadata for uri:'file://&#8230;
&#8230;e/xubuntu/applications/debian-uxterm.desktop Unknown desktop entry type 'Application'    
&#8230;iba - Product Specifications_files/pixel.gif Could not get any metadata for uri:'file://&#8230;
&#8230;p/toshiba/satellite 5100-501_files/pixel.gif Could not get any metadata for uri:'file://&#8230;
&#8230;re/xubuntu/applications/debian-xterm.desktop Unknown desktop entry type 'Application'    
&#8230; Prices & Special Promotions_files/pixel.gif Could not get any metadata for uri:'file://&#8230;
&#8230;otes/laptop/netgear/NETGEAR_files/spacer.gif Could not get any metadata for uri:'file://&#8230;
&#8230;fireworks example/Complete/images/spacer.gif Could not get any metadata for uri:'file://&#8230;
&#8230;es/laptop/netgear/NETGEAR_files/spffffff.gif Could not get any metadata for uri:'file://&#8230;
&#8230;/letters sent to CHP/28_04_16 fire alarm.doc Could not get any metadata for uri:'file://&#8230;
&#8230;k/letters sent to CHP/29_4_16 no stage 2.doc Could not get any metadata for uri:'file://&#8230;
&#8230;usr/share/applications/org.kde.kded5.desktop Unknown desktop entry type 'Service'        
&#8230;untu/applications/Thunar-bulk-rename.desktop Unknown desktop entry type 'Application'    
lines 1-39



```
But on my end nautilus preforms and acts like it should here.
See Screenshot
FTR I'm not going to keep Nautilus Installed and Thunar works very well for me.
EDIT I forgot this:
```
&#9492;&#9472;> systemctl --user status tracker-extract-3.service tracker-miner-fs-3.service tracker-miner-rss-3.service tracker-writeback-3.service tracker-xdg-portal-3.service tracker-miner-fs-control-3.service
&#9675; tracker-extract-3.service
     Loaded: masked (Reason: Unit tracker-extract-3.service is masked.)
     Active: inactive (dead)

&#9675; tracker-miner-fs-3.service
     Loaded: masked (Reason: Unit tracker-miner-fs-3.service is masked.)
     Active: inactive (dead)

&#9675; tracker-miner-rss-3.service
     Loaded: masked (Reason: Unit tracker-miner-rss-3.service is masked.)
     Active: inactive (dead)

&#9675; tracker-writeback-3.service
     Loaded: masked (Reason: Unit tracker-writeback-3.service is masked.)
     Active: inactive (dead)

&#9675; tracker-xdg-portal-3.service
     Loaded: masked (Reason: Unit tracker-xdg-portal-3.service is masked.)
     Active: inactive (dead)

&#9675; tracker-miner-fs-control-3.service
     Loaded: masked (Reason: Unit tracker-miner-fs-control-3.service is masked.)
     Active: inactive (dead)

```

---

### Post by makem2 on 2023-08-08
> **1fallen said:**
> All I know is "tracker-miner-fs-3.service " was the only tracker service HTop could find.
This would all be a different look with Gnome DE  installed.
Now on Debian and XFCE4 with Nautilus:
```
tracker3 status
Currently indexed: 0 files, 0 folders
Remaining space on database partition: 176.5*GB (69.10%)
Data is still being indexed: Estimated less than one second left

```
That is the extend of what the tracker services do.
makem2 I'm not sure what is going on with yours on this:

```
makem@makem-22:~$ tracker3 status
Currently indexed: 30604 files, 1634 folders
Remaining space on database partition: 44.7 GB (50.77%)
All data miners are idle, indexing complete
43 recorded failures


Path                                          Message                                     
…ments/All_WebSites/travel/img/common/1x1.gif Could not get any metadata for uri:'file://…
…/laptop/netgear/NETGEAR_files/h_blue_bar.gif Could not get any metadata for uri:'file://…
/home/makem/Documents/20220130_162413.jpg     Could not get any metadata for uri:'file://…
…lan.action_files/activityi_data/activity.gif Could not get any metadata for uri:'file://…
…lan.action_files/activityi_data/ADVID408.gif Could not get any metadata for uri:'file://…
/home/makem/Documents/20220130_162436.jpg     Could not get any metadata for uri:'file://…
…aint files/chp complaint/20220219_142734.jpg Could not get any metadata for uri:'file://…
…aint files/chp complaint/20220219_142748.jpg Could not get any metadata for uri:'file://…
…aint files/chp complaint/20220219_142848.jpg Could not get any metadata for uri:'file://…
…ome/makem/Documents/Flat/20220524_161254.jpg Could not get any metadata for uri:'file://…
…ome/makem/Documents/Flat/20220524_161312.jpg Could not get any metadata for uri:'file://…
…ome/makem/Documents/Flat/20220524_161345.jpg Could not get any metadata for uri:'file://…
…ome/makem/Documents/Flat/20220524_161413.jpg Could not get any metadata for uri:'file://…
…ome/makem/Documents/Flat/20220524_161441.jpg Could not get any metadata for uri:'file://…
…fireworks example/Complete/images/arrows.gif Could not get any metadata for uri:'file://…
…an to uk/BookTripPlan.action_files/blank.gif Could not get any metadata for uri:'file://…
…otes/laptop/netgear/NETGEAR_files/bullet.gif Could not get any metadata for uri:'file://…
…ebSites/travel/uk/jersey/images/DSC04518.JPG Could not get any metadata for uri:'file://…
…vel/EU/portugal/alcoutim/images/P5151230.JPG Could not get any metadata for uri:'file://…
…rt/han to uk/BookTripPlan.action_files/e.gif Could not get any metadata for uri:'file://…
…el/EU/portugal/albufeira/images/P5181388.JPG Could not get any metadata for uri:'file://…
…e/xubuntu/applications/debian-uxterm.desktop Unknown desktop entry type 'Application'    
…iba - Product Specifications_files/pixel.gif Could not get any metadata for uri:'file://…
…p/toshiba/satellite 5100-501_files/pixel.gif Could not get any metadata for uri:'file://…
…re/xubuntu/applications/debian-xterm.desktop Unknown desktop entry type 'Application'    
… Prices & Special Promotions_files/pixel.gif Could not get any metadata for uri:'file://…
…otes/laptop/netgear/NETGEAR_files/spacer.gif Could not get any metadata for uri:'file://…
…fireworks example/Complete/images/spacer.gif Could not get any metadata for uri:'file://…
…es/laptop/netgear/NETGEAR_files/spffffff.gif Could not get any metadata for uri:'file://…
…/letters sent to CHP/28_04_16 fire alarm.doc Could not get any metadata for uri:'file://…
…k/letters sent to CHP/29_4_16 no stage 2.doc Could not get any metadata for uri:'file://…
…usr/share/applications/org.kde.kded5.desktop Unknown desktop entry type 'Service'        
…untu/applications/Thunar-bulk-rename.desktop Unknown desktop entry type 'Application'    
lines 1-39



```
But on my end nautilus preforms and acts like it should here.
See Screenshot
FTR I'm not going to keep Nautilus Installed and Thunar works very well for me.
EDIT I forgot this:
```
&#9492;&#9472;> systemctl --user status tracker-extract-3.service tracker-miner-fs-3.service tracker-miner-rss-3.service tracker-writeback-3.service tracker-xdg-portal-3.service tracker-miner-fs-control-3.service
&#9675; tracker-extract-3.service
     Loaded: masked (Reason: Unit tracker-extract-3.service is masked.)
     Active: inactive (dead)

&#9675; tracker-miner-fs-3.service
     Loaded: masked (Reason: Unit tracker-miner-fs-3.service is masked.)
     Active: inactive (dead)

&#9675; tracker-miner-rss-3.service
     Loaded: masked (Reason: Unit tracker-miner-rss-3.service is masked.)
     Active: inactive (dead)

&#9675; tracker-writeback-3.service
     Loaded: masked (Reason: Unit tracker-writeback-3.service is masked.)
     Active: inactive (dead)

&#9675; tracker-xdg-portal-3.service
     Loaded: masked (Reason: Unit tracker-xdg-portal-3.service is masked.)
     Active: inactive (dead)

&#9675; tracker-miner-fs-control-3.service
     Loaded: masked (Reason: Unit tracker-miner-fs-control-3.service is masked.)
     Active: inactive (dead)

```

Yes Thunar is fine, just a pity it does not have more options. I have reverted to Thunar. Thanks for the interesting info.

---

### Post by #&amp;thj^% on 2023-08-08
> **makem2 said:**
> Yes Thunar is fine, just a pity it does not have more options. I have reverted to Thunar. Thanks for the interesting info.

Agreed, they pride themself on keeping it light-weight, so some bells and whistles are left out..

---

