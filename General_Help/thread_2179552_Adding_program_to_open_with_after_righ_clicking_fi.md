---
title: "Adding program to open with after righ clicking file"
date: 2013-10-08
forum: General Help
---

### Post by adec2 on 2013-10-08
Hi, I have an unusual problem.

I have installed a program called mediainfo-gui that i would like to add to the right click>open with pop up after i click on a media file. When i select other program and find the mediainfo-gui it opens in mediainfo-gui fine but doesnt automatically add itself to the open with for further use in the future. Also when i select it as default it doesnt stick and keeps the old association which is vlc player. I have opened the shortcut with gedit and it's exec is "mediainfo-gui %U" which is waht i expect to be.

Has anyone any clue as to why it wont add itself to the right click>open with column please?

If it helps this a copy of my .desktop file for mediainfo-gui

[Desktop Entry]
Type=Application
Version=1.0
Name=MediaInfo
Comment=Supplies technical and tag information about a video or audio file
Comment[fr]=fournit des informations techniques et les tags à propos de vos fichiers video et audio
Icon=mediainfo
Exec=mediainfo-gui %U 
Terminal=false
MimeType=
Categories=AudioVideo;AudioVideoEditing;

Also the set as default works fine for associating any other programs but i want to just have it in the open with program list and not set it to open as default

---

### Post by adec2 on 2013-11-03
I'll mark this as solved because for no reason at all it re-appeared back into my open with option :)

---

