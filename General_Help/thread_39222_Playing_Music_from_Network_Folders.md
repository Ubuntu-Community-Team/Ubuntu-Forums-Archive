---
title: "Playing Music from Network Folders"
date: 2005-06-03
forum: General Help
---

### Post by mjsoccer1 on 2005-06-03
Hello....
I'm running Kubuntu on a Dell Latitude C610 with both KDE and GNOME desktops.  I am using AmaroK for my music, which I like, but I'm trying to play music that is in a networked folder and it will not play.  AmaroK recognizes the folder and loads the songs into the playlist, but when I try to play any of the networked songs, t;hey dont play.  The problem is specific to networked folders because AmaroK handles Mp3s in the home folder fine... Any ideas? AmaroK doesn't even give me an error when trying to play the networked songs, it looks like it is playing, but nothing comes out... Any thoughts are appreciated. Thanks!

---

### Post by _Pete_ on 2005-06-04
[QUOTE=mjsoccer1]Hello....
I'm running Kubuntu on a Dell Latitude C610 with both KDE and GNOME desktops.  I am using AmaroK for my music, which I like, but I'm trying to play music that is in a networked folder and it will not play.  AmaroK recognizes the folder and loads the songs into the playlist, but when I try to play any of the networked songs, t;hey dont play.  The problem is specific to networked folders because AmaroK handles Mp3s in the home folder fine... Any ideas? AmaroK doesn't even give me an error when trying to play the networked songs, it looks like it is playing, but nothing comes out... Any thoughts are appreciated. Thanks![/QUOTE]

Have you checked that you have proper access right to the network folder e.g. you really can read the files there ?

---

### Post by apswartz on 2005-06-04
[QUOTE=mjsoccer1]Hello....
I'm running Kubuntu on a Dell Latitude C610 with both KDE and GNOME desktops.  I am using AmaroK for my music, which I like, but I'm trying to play music that is in a networked folder and it will not play.  AmaroK recognizes the folder and loads the songs into the playlist, but when I try to play any of the networked songs, t;hey dont play.  The problem is specific to networked folders because AmaroK handles Mp3s in the home folder fine... Any ideas? AmaroK doesn't even give me an error when trying to play the networked songs, it looks like it is playing, but nothing comes out... Any thoughts are appreciated. Thanks![/QUOTE]
 How are the drives networked? nfs, samba, ??

---

### Post by still on 2005-06-04
try to mount those network folders locally (ie. /mnt/music) then try playing them..
ihad an alike issue with kaffeine..

---

### Post by mjsoccer1 on 2005-06-05
Hey,
I'm using Samba to network the folders... I can access all of the files from my Windows machine with no problem, and when I browse the folders in Konqueror, I have no problems... It used to pop up login windows, but I changed some settings in samba on the Mandrake machine using Webmin to allow guests to access files... Right now on the Mandrake machine, the music folder is owned by my user name (the Mandrake user name) Should I change it to Samba or something? Thanks!

---

### Post by mjsoccer1 on 2005-06-05
Okay... I still cannot play music from my network folder, however I can "preview" all of the songs using Kaffeine.  When I try to start Kaffeine indepedently, I cannot open the networked songs (if I select one, I receive an error, stating "*You can only select local files.* "... I will continue to play around, and see what I come up with... SO far I have had no luck trying to mount the remote folder... I will keep on trying....

---

### Post by still on 2005-06-05
try to mount using the following command:

mount -t cifs -o username="xxxx", password="xxxx" //server/share /mnt/music

so any change?

---

### Post by mjsoccer1 on 2005-06-05
Hmm.. I tried mounting using cifs, however it is not returning anything other than the different parameters that I can use for the command mount... I tried mounting the remote fs using mount smbfs, however I do not have smbfs installed, so I tried apt-get install smbfs, and it appears that [http://archive.ubuntu.com](http://archive.ubuntu.com).... is down (I can't ping it, and I get a 111 Connection refused). I will keep on trying, thanks for the suggestions, any more are greatly appreciated. Thanks!

---

### Post by still on 2005-06-05
can u write down the exact command u use for mounting?

---

### Post by mjsoccer1 on 2005-06-05
Okay, I installed smbfs, and I can mount the other linux machine... **mount -t smbfs //linuxmac/homes/username/My_Media/Music /mnt/Music  ** And I can play songs now on this machine, which is good... The only thing is that when I mount the //linuxmac, it only mounts the root share (//linuxmac)... even if I specify the specific folder (//linuxmac/homes/username/My_Media/Music)  While this isn't a huge problem, it still requires some click throughs to get to my music... is there anyway to mount the specific Music folder from the other machine?  Thanks for all of your help!  :grin:

---

### Post by still on 2005-06-06
just make that specific windows folder shared and mount it on ur ubuntu box..
glad that its working now inthere although ididnt realize yet where was the prob.?

---

### Post by mjsoccer1 on 2005-06-07
Well it seems as though I needed to mount the remote fs, and to do so, I need smbfs installed... cifs wouldn't work.  After mounting the samba folder as smbfs, it worked well... not exactly sure why that was necessary, but its working now. Thanks for all of your help!

---

