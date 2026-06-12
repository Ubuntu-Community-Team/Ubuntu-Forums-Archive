---
title: "Konqueror and Kate in GNOME: problem with remote files"
date: 2008-05-06
forum: General Help
---

### Post by cannibal_bill on 2008-05-06
Hi everyone!
This is my first post, I've been more than happy reading other people problems to solve mines for almost a year now, since when I switched from windows to ubuntu.

No I have a problem I can't solve browsing here or there : 
I run Ubuntu 7.10 (with GNOME), and I keep it updated when updates go out (I did not get 8.04 since I had problems updating from 7.04 to 7.10 and I'm quite happy with it now - and 8.10 does not seem satisfactory).

I use konqueror and kate to browse/edit files via ssh on my dreamhost account. Double-click in konqueror opens php/js and more in kate ; while ctrl-s in kate saves live on dreamhost servers. All this via ssh, nice!

But last week-end (sunday), ssh connexions failed. I could not even connect via terminal and I contacted the dreamhost support team who fixed it. Now my computer can talk via ssh with dreamhost servers... Well, not fully : connexions via the terminal work fine, ssh in nautilus & gedit work fine, but konqueror and kate still wont find the server.

Konqueror doesn't do anything : just, well, nothing. The status bar says "connecting", then nothing (to be more precise, at some point it says "no files" or something like that).
Kate opens a "loading progress..." window with a progress bar and a text saying "connecting..." that should says "initiating procolo", then "downloading"... But, then again, nothing : this window stays "freezed" (although I can close it)...
I've tried ssh, sftp and ftp. All work with nautilus+gedit, none with konqueror+kate

Does anybody have a clue about this?
I'm no linux guru, I update almost blindly. This morning, I was asked to update some "kdecore" or "kdelibs" or something like that, which I did, but it changed nothing.

Again, nautilus and gedit can connect perfectly, but konqueror and kate wont do nothing. I know I could use gedit (which I dont like, kate is way more powerful), or switch to KDE (well, I prefer the GNOME style)... Besides, this SHOULD (and HAS) worked, and fine, until 2 days ago.

Any advice? Thanks for your time, AWESOME ubuntu community !!

edit: Unbelievable! After 3 days, the problem solved alone! Possibly because of rebooting : last week-end, when the problem arose, I had rebooted the system. I don't know for how long it was up, and had the buggy update waiting... Then, after this morning's update, I also didnt reboot (well I thought linux needed seldom reboots after updates/installs/uninstalls, and when it does, the udpate manager informs you with an icon near the clock, which I have not seen for a while now). Now the system hanged, and I checked konqueror : successful connexion. Double-click opens file in kate . . . awww, relief !!!
Lesson learned : when previously ok system fails with no tweaking, buggy update is to blame... What do do? Just wait a couple of days for a new update, then reboot... Linux is magic !! Sorry for bugging this forum . . . !

---

