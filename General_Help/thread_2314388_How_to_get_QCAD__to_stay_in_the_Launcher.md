---
title: "How to get QCAD  to stay in the Launcher"
date: 2016-02-20
forum: General Help
---

### Post by RayArdia on 2016-02-20
I use QCAD a lot. For those not familiar it's a CAD program, the 'standard' version is open-source, free to download and use. There is also a Pro version for sale (which I use) which is slightly superior to the free version, and IMHO much better than Libre CAD which is of course available from Software Centre.

I recently needed to upgrade QCAD so downloaded and installed version 3.12.6 pro. All is well, the new version runs fine but with a little snag - I have to load from Terminal each time ; then the QCAD symbol appears in Launcher, but despite locking it to Launcher the symbol disappears as the program is closed.

As I need to use QCAD just about every time I open my laptop, I would very much like to find a way to make it 'stick' to Launcher anyone have any idea how I can do this please?

---

### Post by gordintoronto on 2016-02-21
How did you "lock to launcher"? Right-click on the item in the launcher? I've never had that fail.

---

### Post by RayArdia on 2016-02-21
Yes, locked on by right click in the usual way, however QCAD only stays locked to Launcher whilst it is running, unlocks when closed.

---

### Post by kostkon on 2016-02-22
You can create a custom launcher for your application, then search for it in the dash and drag it to the launcher, e.g.:

in the terminal:
```
gedit ~/.local/share/applications/QCAD.desktop
```
then paste the following into it:
```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=QCAD
Comment=The ultimative CAD program
Keywords=3d;cad;model;
Exec=path/to/qcad/executable
Icon=path/to/icon/file
Categories=Graphics;
Terminal=false
StartupNotify=true
StartupWMClass=wmclass_of_qcad
```

the StartupWMClass option is an additional measure to make sure that the icon in the launcher corresponds to its actual window(s). To find the WM_CLASS of your application, if it's got one, start the application, then in the terminal:
```
xprop | grep WM_CLASS
```
and when the crosshair cursor appears, click on its window.

Hope that helps.

---

### Post by RayArdia on 2016-03-05
> **kostkon said:**
> You can create a custom launcher for your application, then search for it in the dash and drag it to the launcher, e.g.:

in the terminal:
```
gedit ~/.local/share/applications/QCAD.desktop
```
then paste the following into it:
```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=QCAD
Comment=The ultimative CAD program
Keywords=3d;cad;model;
Exec=path/to/qcad/executable
Icon=path/to/icon/file
Categories=Graphics;
Terminal=false
StartupNotify=true
StartupWMClass=wmclass_of_qcad
```

the StartupWMClass option is an additional measure to make sure that the icon in the launcher corresponds to its actual window(s). To find the WM_CLASS of your application, if it's got one, start the application, then in the terminal:
```
xprop | grep WM_CLASS
```
and when the crosshair cursor appears, click on its window.

Hope that helps.

Thank you, tried to do what you suggest but it didn't work for me. After I had pasted your code into ```
gedit ~/.local/share/applications/QCAD.desktop
``` nothing happened, 
what should have happened?

---

### Post by RayArdia on 2016-03-05
PS. Afternote:- Terminal output:-
ray@ray-Aspire-5735:~$ ls
Allinson-Clutterbuck_2014-11-27.gpkg.media
Allinson-Clutterbuck.ged
Audio Disc.toc.bin
brasero-session.log
BSA M20 Military Version.html
Calibre Library
cups-1.7.3
deja-dup
Desktop
Diagrams Sketches etc
Documents
Downloads
examples.desktop
Family Tree Backups
ffmpeg-2.4.3
firefox
Firefox_wallpaper.png
Five Stars Music.xspf
Genealogy  for Sorting
guayadeque
HMA VPN
Hobbies
 Hobbies
hp-check.log
hplip-3.10.9
hs_err_pid4070.log
hs_err_pid9455.log
iTunes
Jigsaw etc.dxf
Keepass Database.kdb
libflashplayer.so
Link to Calibre Library
Link to Music
Link to Photos
Link to Pictures
Link to Videos
lshw.txt
Mail
Marks Events.odt
Marriage Marks-Wadham Oct-Dec 1867.odt
MobiMetaEditor
Mounting and Permissions.odt
NIS Vocabulary - Beginners 1-8.odt
NIS Vocabulary.odt
output
photorec.ses
Pictures
Pillar Drill mods.dxf
Playlist 1.xspf
Public
qbittorrent-3.1.11
QBT Downloads
qcad-3.12.6-pro-linux-x86_32
qcad-3.12.6-pro-linux-x86_32.tar.gz
readme.txt
recovered_jpegs
Santander 11 Dec 14.odt
Santander 17 Jan14.odt
Santander 23 Jan 2014.odt
Seagate
Seagate Expansion Drive
shotwell-0.8.1
Silverside.odt
Soluciones NIS Int.odt
soundKonverter
Templates
testdisk-7.0-WIP
testdisk.log
Test Page.odt
troubleshoot.txt
Two M10 nuts .skb
Two M10 nuts .skp
Ubuntu One
usr
Videos
WD&RA letter to Santander 28 Jul 2014.odt
ray@ray-Aspire-5735:~$ cd qcad-3.12.6-pro-linux-x86_32
ray@ray-Aspire-5735:~/qcad-3.12.6-pro-linux-x86_32$ 
ray@ray-Aspire-5735:~/qcad-3.12.6-pro-linux-x86_32$ gedit ~/.local/share/applications/QCAD.desktop

Gedit entry is:-
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=QCAD
Comment=The ultimative CAD program
Keywords=3d;cad;model;
Exec=path/to/qcad/executable
Icon=path/to/icon/file
Categories=Graphics;
Terminal=false
StartupNotify=true
StartupWMClass=wmclass_of_qcad

Does this help?

---

