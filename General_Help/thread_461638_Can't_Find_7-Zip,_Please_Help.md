---
title: "Can't Find 7-Zip, Please Help"
date: 2007-06-01
forum: General Help
---

### Post by Stink Hook on 2007-06-01
Ok, so I downloaded some icons that came in a .rar package. I realized shortly there after that Archive Manager doesn't open .rar. I looked on "Add/Remove..." and found 7-Zip, and I decided to install that package. Now I can't find 7-Zip. I tried just opening the .rar again thinking that maybe it's a system type program that doesn't need a launcher. I tried the terminal (7-Zip, p7zip-full...) and the application launcher. I looked in Synaptic and though maybe I need to install p7zip as well as the p7zip-full that I installed through the Add/Remove. I followed the advice of "How to install ANYTHING in Ubuntu!" website, installing the menu-xdg package. I didn't see the Debian menu so I went to System>Preferences>Main Menu and selected Debian, but that didn't do jack because there is nothing listed under the Debian menu. I tried searching in /usr/bin and /bin thinking maybe the executable file would be there. I searched for files with "7-Zip," and "p7zip." I searched Google and the Ubuntu Forums. I'm sorry but I'm tired, can someone help me figure this out please.](*,)

---

### Post by kpel on 2007-06-01
If I remember p7zip is a command-line only port of 7zip, as the 7zip program is currently only built (and support) for Windows operating systems.

I actually stumbled on this post because I too am looking for a decent archiving program to handle those archives.  And I'm still looking....

Edit: Just found this link, maybe it'll help.

[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

---

### Post by srt4play on 2007-06-01
Archive Manager will handle pretty much any type of zipped file, but .rar and .7z cannot be handled by default. 

Install 'unrar' and 'p7zip' in Synaptic to get this funtionality.  This will not put icons in your menu it will automatically give this funtionality to Archive Manager.  Just right-click the archive file and choose extract here or open with Archive Manager.

---

### Post by true_friend on 2007-06-01
Use Atuomatix for this purpose. It installs support for rar and 7zip and the default acrchive manager becomes able to handle these formats also.

---

### Post by Stink Hook on 2007-06-01
Hallelujah! \\:D/

I would kiss your feet if they were in front of me!

Thanks guys.

(p.s. I swear I tried to figure it out myself.)

---

