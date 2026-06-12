---
title: "Troubles with Samba on Ubuntu with Wubi."
date: 2008-05-21
forum: General Help
---

### Post by Wubifan on 2008-05-21
Hello I'm pretty new to Wubi and am in a little trouble.


See i put ubuntu with wubi on my main PC and i love it, i'm thow forced to go to WinXp because i can't share to the Windows Xp Pc that is use to play video files in my LCD TV.


So i searched and found out that Samba was the best for my so i got it and tried to set it up. But there comes the problem i don't now where to find the computers name ore where in Xp to trie to find the Ubuntu shareing.


I would love to get some good instrucsions on how i can share so i don't have to go to Xp.

Alsow how do i see the files on the Windows Xp OS when i'm in Ubuntu?

---

### Post by ago on 2008-05-21
XP files are available under /host

You can look into Samba documention on how to set it up. But it should be quite trivially to do so via system > admin. 

You can use the ip of your machine. See the network applet.

Note that the samba SERVER is used to "send" files from Ubuntu to other Windows machines on the network. And of course the Ubuntu machine has to be on. To "get" the files that are shared by other Windows machines into Ubuntu you need to use the samba CLIENT which is already available via nautilus.

---

