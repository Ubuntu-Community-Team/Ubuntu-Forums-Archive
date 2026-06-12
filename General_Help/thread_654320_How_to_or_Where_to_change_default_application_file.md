---
title: "How to or Where to change default application file-type wide?"
date: 2007-12-30
forum: General Help
---

### Post by Laibcoms on 2007-12-30
Hi,

   I'm familiar with the "Open With" tab, but that method is time consuming as I will have to either (1) find each file extension I want to change; (2) download a file of a certain file extension that I want to change.

   Is there a way, GUI or command-line, that will allow me to change the default application to open system-wide per extension on either or both gnome and kde (since both are installed together)?

   I'm referring about something like the "File Types" in XP where one can simply scroll and do changes, instead of locating each file in the hard disk drives.

   Example, I want to change the default application of .torrent files to Deluge instead of KTorrent but I don't have .torrent files atm, I just want to set it up ;)

   And with that, I noticed that after I installed kubuntu-desktop (on-top of ubuntu), it changed a lot of default applications system-wide to its own, so I ended up checking each application and see if its using gnome or kde apps, which is again, extra steps, and I tend to miss a lot that way.

   Command-line is fine, no problem with it...  I was already alive during the DOS days :p 8086 PCs of the 80s ;)

   Thanks a bunch, and Happy New Year!  (It's 12:45pm here, 11 hours and 15minutes to 2008!!)


-- laters... going to watch and take photos of the last sunset of 2007 :D

---

### Post by dlegend on 2007-12-31
I think the file you want to modify is located here: **~/.local/share/applications/defaults.list** -- this will change your user's default application file-types. To modify, just navigate to that folder and open the defaults.list file or type this in your terminal:

> 
gedit ~/.local/share/applications/defaults.list


Note: The above file I mentioned will probably be empty (as mine is) and you'd need to grab the information from the below mentioned file to get the default entries so you can modify them.

The other file you can modify is **/usr/share/applications/defaults.list** file -- I believe this is for global changes across different users though. To modify just type:

> 
sudo gedit /usr/share/applications/defaults.list


I'm guaranteed that modifying the second file I mentioned will solve your problem but you can try the first suggested method if your up to it.

---

### Post by Whiffle on 2007-12-31
Under KDE...

Open Konqueror, Settings Menu, Configure Konqueror, go to File Associations.

---

### Post by afeasfaerw23231233 on 2008-01-06
how can i make smplayer to be the default player of certain type of video file [mkv, rvmb, mp4] and totem to play avi, wmv.
here's what i get by
sudo gedit /usr/share/applications/defaults.list 
> 
[Default Applications]
application/csv=ooo-calc.desktop
application/excel=ooo-calc.desktop
application/msexcel=ooo-calc.desktop
application/msword=ooo-writer.desktop
application/ogg=totem.desktop
application/pdf=evince.desktop
application/postscript=evince.desktop
application/rtf=ooo-writer.desktop
application/tab-separated-values=ooo-calc.desktop
application/vnd.lotus-1-2-3=ooo-calc.desktop
application/vnd.ms-excel=ooo-calc.desktop
application/vnd.ms-word=ooo-writer.desktop
application/vnd.rn-realmedia=totem.desktop
application/vnd.sun.xml.calc=ooo-calc.desktop
application/vnd.sun.xml.calc.template=ooo-calc.desktop
application/vnd.sun.xml.draw=ooo-impress.desktop
application/vnd.sun.xml.draw.template=ooo-impress.desktop
application/vnd.sun.xml.math=ooo-math.desktop
application/vnd.sun.xml.writer=ooo-writer.desktop
application/vnd.sun.xml.writer.template=ooo-writer.desktop
application/vnd.sun.xml.writer.global=ooo-writer.desktop
application/vnd.oasis.opendocument.formula=ooo-math.desktop
application/vnd.oasis.opendocument.graphics=ooo-draw.desktop
application/vnd.oasis.opendocument.graphics-template=ooo-draw.desktop
application/vnd.oasis.opendocument.presentation=ooo-impress.desktop
application/vnd.oasis.opendocument.presentation-template=ooo-impress.desktop
application/vnd.oasis.opendocument.spreadsheet=ooo-calc.desktop
application/vnd.oasis.opendocument.spreadsheet-template=ooo-calc.desktop
application/vnd.oasis.opendocument.text=ooo-writer.desktop
application/vnd.oasis.opendocument.text-template=ooo-writer.desktop
application/vnd.oasis.opendocument.text-web=ooo-writer.desktop
application/vnd.oasis.opendocument.text-master=ooo-writer.desktop
application/vnd.sun.xml.impress=ooo-impress.desktop
application/vnd.sun.xml.impress.template=ooo-impress.desktop
application/vnd.stardivision.calc=ooo-calc.desktop
application/vnd.stardivision.draw=ooo-draw.desktop
application/vnd.stardivision.impress=ooo-impress.desktop
application/vnd.stardivision.math=ooo-math.desktop
application/vnd.stardivision.writer=ooo-writer.desktop
application/mspowerpoint=ooo-impress.desktop
application/vnd.ms-powerpoint=ooo-impress.desktop
application/vnd.wordperfect=ooo-writer.desktop
application/wordperfect=ooo-writer.desktop
application/x-123=ooo-calc.desktop
application/x-abiword=abiword.desktop
application/x-applix-spreadsheet=ooo-calc.desktop
application/x-ar=file-roller.desktop
application/x-arj=file-roller.desktop
application/x-bzip-compressed-tar=file-roller.desktop
application/x-bzip=file-roller.desktop
application/x-cd-image=nautilus-cd-burner-open-iso.desktop
application/x-compressed-tar=file-roller.desktop
application/x-compress=file-roller.desktop
application/x-deb=gdebi.desktop
application/x-debian-package=gdebi.desktop
application/x-dos_ms_excel=ooo-calc.desktop
application/x-ear=file-roller.desktop
application/x-excel=ooo-calc.desktop
application/x-extension-m4a=totem.desktop
application/x-extension-mp4=totem.desktop
application/x-flac=totem.desktop
application/x-glade=glade-2.desktop
application/x-gnumeric=gnumeric.desktop
application/x-gtar=file-roller.desktop
application/x-gzip=file-roller.desktop
application/x-gzpostscript=evince.desktop
application/xhtml+xml=firefox.desktop
application/x-jar=file-roller.desktop
application/x-java-archive=file-roller.desktop
application/x-lha=file-roller.desktop
application/x-lhz=file-roller.desktop
application/xls=ooo-calc.desktop
application/x-lzop=file-roller.desktop
application/x-matroska=totem.desktop
application/x-mps=ooo-calc.desktop
application/x-ms-excel=ooo-calc.desktop
application/x-msexcel=ooo-calc.desktop
application/x-ogg=totem.desktop
application/x-oleo=ooo-calc.desktop
application/x-perl=gedit.desktop
application/x-planperfect=ooo-calc.desktop
application/x-quattropro=ooo-calc.desktop
application/x-rar-compressed=file-roller.desktop
application/x-rar=file-roller.desktop
application/x-rpm=file-roller.desktop
application/x-sc=ooo-calc.desktop
application/x-shockwave-flash=totem.desktop
application/x-sylk=ooo-calc.desktop
application/x-tar=file-roller.desktop
application/x-war=file-roller.desktop
application/x-xbase=ooo-calc.desktop
application/x-xls=ooo-calc.desktop
application/x-zip-compressed=file-roller.desktop
application/x-zip=file-roller.desktop
application/x-zoo=file-roller.desktop
application/zip=file-roller.desktop
audio/mpeg=totem.desktop
audio/mpegurl=totem.desktop
audio/vnd.rn-realaudio=totem.desktop
audio/x-flac=totem.desktop
audio/x-m4a=totem.desktop
audio/x-mp3=totem.desktop
audio/x-mpeg=totem.desktop
audio/x-mpegurl=totem.desktop
audio/x-ms-asf=totem.desktop
audio/x-ms-asx=totem.desktop
audio/x-ms-wax=totem.desktop
audio/x-pn-aiff=totem.desktop
audio/x-pn-au=totem.desktop
audio/x-pn-realaudio-plugin=totem.desktop
audio/x-pn-realaudio=totem.desktop
audio/x-pn-wav=totem.desktop
audio/x-pn-windows-acm=totem.desktop
audio/x-real-audio=totem.desktop
audio/x-scpls=rhythmbox.desktop
audio/x-wav=totem.desktop
image/bmp=eog.desktop
image/gif=eog.desktop
image/jpeg=eog.desktop
image/jpg=eog.desktop
image/pjpeg=eog.desktop
image/png=eog.desktop
image/svg+xml=eog.desktop
image/tiff=eog.desktop
image/vnd.rn-realpix=totem.desktop
image/x-bmp=eog.desktop
image/x-gray=eog.desktop
image/x-icb=eog.desktop
image/x-ico=eog.desktop
image/x-png=eog.desktop
image/x-portable-anymap=eog.desktop
image/x-portable-bitmap=eog.desktop
image/x-portable-graymap=eog.desktop
image/x-portable-pixmap=eog.desktop
image/x-psd=gimp-2.2.desktop
image/x-xbitmap=eog.desktop
image/x-xpixmap=eog.desktop
inode/directory=nautilus-folder-handler.desktop
misc/ultravox=totem.desktop
multipart/x-zip=file-roller.desktop
text/abiword=abiword.desktop
text/comma-separated-values=ooo-calc.desktop
text/csv=ooo-calc.desktop
text/html=firefox.desktop
text/plain=gedit.desktop
text/richtext=abiword.desktop
text/rtf=ooo-writer.desktop
text/spreadsheet=ooo-calc.desktop
text/tab-separated-values=ooo-calc.desktop
text/x-comma-separated-values=ooo-calc.desktop
text/x-chdr=gedit.desktop
text/x-csrc=gedit.desktop
text/x-dtd=gedit.desktop
text/x-java=gedit.desktop
text/mathml=gedit.desktop
text/x-python=gedit.desktop
text/x-sql=gedit.desktop
text/xml=firefox.desktop
video/dv=totem.desktop
video/mp4=totem.desktop
video/mpeg=totem.desktop
video/msvideo=totem.desktop
video/quicktime=totem.desktop
video/vnd.rn-realvideo=totem.desktop
video/x-anim=totem.desktop
video/x-avi=totem.desktop
video/x-flc=totem.desktop
video/x-fli=totem.desktop
video/x-mpeg=totem.desktop
video/x-ms-asf=totem.desktop
video/x-msvideo=totem.desktop
video/x-ms-wmv=totem.desktop
video/x-nsv=totem.desktop
x-directory/normal=nautilus-folder-handler.desktop
zz-application/zz-winassoc-xls=ooo-calc.desktop

---

### Post by Alex_Fingers on 2008-02-06
I found a simpler way of changing what application a certain file type opens with (I'm using Ubuntu 7.10) :

Take, for example, a .wav - right click on it, click on the 'opens with' tab and choose the application you want it to open with there...

Hope this helps!

---

### Post by zabaksmers17 on 2008-07-03
solution can be found here: [http://linux.about.com/od/ubuntu_doc/a/ubudg10t10.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg10t10.htm) : right click on the file icon, select properties and choose the appropriate application in "open with" tab.

---

### Post by iura_boss on 2008-07-16
The easiest way is to Right Click on that specific file, choose Properties -> Open With. There you can select an application to open that type of files! :D

---

