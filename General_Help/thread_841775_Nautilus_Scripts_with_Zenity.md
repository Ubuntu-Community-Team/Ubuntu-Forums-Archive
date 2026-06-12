---
title: "Nautilus Scripts with Zenity"
date: 2008-06-26
forum: General Help
---

### Post by TroyDowling on 2008-06-26
Hey guy,

I'm just working on a quick script that backs up my /home to a specific location. Right now I have no idea how long the process takes unless I execute the command from the terminal. I was hoping somebody knew of a quick solution to showing a progress bar of the 'tar' command. I believe this would utilize Zenity, but I have no experience with that. If anyone could help me out that would be awesome. It's a very, very basic script (below).

```

#!/bin/sh

cd /media/Storage/
tar jcfv homeBackup.tar.bz2 ~

```

---

### Post by ryanhaigh on 2008-06-26
This page has some info on how the zenity progress bar works [http://www.rolfs.no/2007/10/14/small-progress-example-script-for-gnome-zenity/](http://www.rolfs.no/2007/10/14/small-progress-example-script-for-gnome-zenity/) but it doesn't look as though it is going to be easy to do. You could throw up a notification using gnome-osd-client or or libnotify-bin at the start and the end of the script.
```

#!/bin/sh
notify-send "Backup started"
cd /media/Storage/
tar jcfv homeBackup.tar.bz2 ~
notify-send "Backup completed"

```

---

### Post by bodhi.zazen on 2008-06-26
```
cd /media/Storage/
tar jcfv homeBackup.tar.bz2 ~ 2>&1 | zenity --progress --title="Archiving..."
```

See : [http://www.linuxjournal.com/content/make-your-scripts-user-friendly-zenity](http://www.linuxjournal.com/content/make-your-scripts-user-friendly-zenity) 



In scripts, use a full path if at all possible for commands and files.

If you have a complex script, use variables to reduce errors (typos) and repetitive typing.

TAR="/bin/tar"
SOURCE="/media/Storage/"
ARCHIVE="/home/user/homeBackup.tar.bz2"

---

### Post by TroyDowling on 2008-06-27
Wow, those are both great solutions. I like the way the progress bar looks and it seems to work alright. Obviously tar'ing up my /home is taking a few minutes, but I think this is definitely what I was looking for. Thanks a lot for the help guys, I'll keep those links bookmarked for the future!

Troy.

---

### Post by NULL712 on 2008-06-27
on the topic of zenity, I would like to know how to use zenity to input variables into a script at sertin points. The point are any thang between the <> and it would be nice to have a message to tell me what to do. Here is the script

!#/bin/bash
# NOTE: Run as root
ifconfig <interface> down
dhclient -r <interface>
ifconfig <interface> up
iwconfig <interface> essid <"network-name">
iwconfig <interface> mode Managed
dhclient <interface>


Thanx
Craig.

---

### Post by geirha on 2008-06-27
[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

---

### Post by bodhi.zazen on 2008-06-27
> **geirha said:**
> [http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

In addition, once you have looked at those links, to be honest ...

man zenity

The man page is quite complete.

---

### Post by spice_vs on 2008-06-30
hi,
i am very new to gui programming. but i was wondering is there a way to notify the user about some event passively. 

i tried 
```
zenity --info --text="my script completed" 
```
but the problem is it steals the focus from my workspace.
I was wondering how can i give the cool notifications that come from the tray and does not steal focus. a good example is the "safe to remove device" pop up balloon message..

Can anyone help me how can i get that.. 


or any pointers to example code would also be great

thanks
spice

---

### Post by geirha on 2008-06-30
It's called notification. Check the links I posted earlier and the man-page for examples. The notification part isn't thoroughly documented though. This shows you how to get a bit more control over it: [http://blogs.gnome.org/jamesh/2004/09/16/notification-icons/](http://blogs.gnome.org/jamesh/2004/09/16/notification-icons/)

---

