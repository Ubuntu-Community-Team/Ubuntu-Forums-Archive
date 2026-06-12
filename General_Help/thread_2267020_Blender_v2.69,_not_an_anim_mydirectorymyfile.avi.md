---
title: "Blender v2.69, not an anim /mydirectory/myfile.avi"
date: 2015-02-26
forum: General Help
---

### Post by chrzk on 2015-02-26
Hi
Every now and again, I log into Ubuntu 14.04 LTS on my dual boot HP Pavilion i5, and so I can be considered fairly new to the OS.
My thought process is that Linux is much more light weight than Windows, and so it should be better suited to video editing.

I have installed Blender v2.69 straight from the Software Centre.
It runs absolultely fine, but I have found that[COLOR=#ff0000] **I cannot open .avi files**[/COLOR], although it can successfully open .mov files.
NB I am opening both file types from the same directory created under Windows 8.1 (NTFS partition).
The avi files have been rendered by kdenlive, also running from this dual booted Ubuntu.
I have also edited my .mov file and rendered a .avi from Blender, but Blender will not open the .avi that it has created.
I have made a copy of the file and attempted to access it from my Ubuntu partition.

If I run Blender from command line, and attempt to open the file, I get;
[SIZE=1][FONT=courier new]root@MyMachine:/usr/share# blender
Color management: using fallback mode for management
connect failed: No such file or directory
[COLOR=#ff0000]**not an anim: /mydirectory/myfile.avi**[/COLOR][/FONT][/SIZE]
(I have executed as root and my user)

A Google search indicates very few people have this type of issue, and I have therefore been unable to find any way to resolve the issue.
Can anybody help?

Example properties using 'Files';
**Video**
Dimensions : 1920 x 1080
Codec : MPEG-4 Video
Framerate : 30 frames per second
Bitrate : N/A
**Audio**
Codec : MPEG-1 Layer 3 (MP3)
Channels : Stereo
Sample rate : 44100 Hz
Bitrate : 128 kbps

thank you

---

