---
title: "[SOLVED] USB drive shortcuts to Desktop from Drive will not launch"
date: 2007-07-31
forum: General Help
---

### Post by nowshining on 2007-07-31
when I right click and click create launcher then input a name, then on the command, browse to the intended program (an exe file (I have wine) and I've also tried with a zip file and still no go) then click okay, it throws up the following:

There was an error launching the application

Details: Failed to execute child process "/media/CENTON" (No such file or directory)



my centon usb drive is named Centon 970M and yes I've tried going directly thru filesystem media folders, but sill no go, is this a bug or simply something that is not yet implemented... that's what I'd like to know or a fix if possible if anyone knows before I may file a bug report... I want to make sure whether it is a bug or not..so i'm asking here first...

edit: a USB Stick flash Drive is what it is..

---

### Post by audax321 on 2007-07-31
It might be because the path includes a space:

1. Right click the launcher.
2. Go to Properties.
3. Go to the Launcher Tab.
4. Look at the command and wherever there is a space, put a \ so it looks like this:

BEFORE: /path/to a/file
AFTER: /path/to\ a/file

If you need further help, post the command you are trying to launch from that box. I bet its just formatted wrong or something. (you could also try just putting the entire command in quotes so it looks like this: "/path/to a/file"

---

### Post by nowshining on 2007-07-31
thanks :) for your help..

edit: here's what it had to look like for me

/media/CENTON 970M/PStart.exe    --- before
/media/CENTON\ 970M/PStart.exe   ---after


i input that example to also help others...having shortcut issues also

---

### Post by audax321 on 2007-07-31
They've had that problem for awhile, but it looks like it might finally be getting fixed in time for Gutsy:

[https://bugs.launchpad.net/gnome-panel/+bug/15050](https://bugs.launchpad.net/gnome-panel/+bug/15050) :)

---

### Post by nowshining on 2007-07-31
Thanks for that info.

---

