---
title: "Writing a script to sync usb stick and a folder on hd"
date: 2007-09-04
forum: General Help
---

### Post by fazza on 2007-09-04
hi all
just managed to write my first simple script (I think it's called that), and it works alright. It synchronises my school work with a folder on my desktop, then displays a window telling me it's finished syncing (using Zenity). However...
Say I have two files the same, one on usb, the other on hd. One was edited at 3:00, the other was edited at 3:19. I want to get the computer to work out which is the newest and bring them both up to date. At the moment, if I do work on the hd version and then sync them, I lose everything I did to it. But if I edit the usb version and sync it, they both contain the new data. Obviously, I could write two scripts to do the job, one for usb syncing and one for hd syncing, but I'd prefer it to be in one mouse click.
Here is the current script
```
cd /
cd /home/USERNAME/Desktop
rsync -ax /media/usbdisk/School\ Work/. School\ Work
zenity --title "Coursework Sync" --window-icon "/usr/share/icons/Human/16x16/status/dialog-information.png" --info --text "Your files have been Synchronised."
```
If anyone can help, I'd be very grateful.

---

### Post by banewman on 2007-09-04
Have just been reading "man rsync" , and trying not to state the obvious, it copies from a source to a destination - the same command will only copy one way. I couldn't see an option to check the time and if necessary change the direction of the copy - which sounds like what you are after. But to offer some hope there is a forum for programming that might have people more able to offer a solution. Hope this gives some direction if not a solution.  :)

---

### Post by bashologist on 2007-09-04
```
       -u, --update
              This  forces  rsync  to  skip any files which exist on the destina
tion and have a modified time that is newer than the source file.  (If an
              existing destination file has a modify time equal to the source fi
le&#8217;s, it will be updated if the sizes are different.)

              In the current implementation of --update, a difference of file fo
rmat between the sender and receiver is always considered to be important
              enough for an update, no matter what date is on the objects.  In o
ther words, if the source has a directory or a symlink where the destina&#8208;
              tion has a file, the transfer would occur regardless of the timest
amps.  This might change in the future (feel free to comment on  this  on
              the mailing list if you have an opinion).
```

I would try the -u switch, but make sure you always backup your files when playing with scripts; Even the best scriptwriters backup their important files before executing something random on them.

```
cd ~
rsync -axu /media/usbdisk/School\ Work/. School\ Work
zenity --title "Coursework Sync" --window-icon "/usr/share/icons/Human/16x16/status/dialog-information.png" --info --text "Your files have been Synchronised."
```

---

### Post by fazza on 2007-09-04
aaahh... okay, thanks bashologist. I did experiment with -u, but didn't realise that it was put with the -ax. I put it as -ax -u, with no results. btw, what exactly does -a and -x do? I did look in the help, but didn't understand it. 

thanks banewman aswell - gave me an idea... I could put the command in both ways round, one after the other.

Also, I couldn't make the --width and --height parameters work. I tried --width=120, --width "120" and --width="120". None worked.
Thanks

---

### Post by fazza on 2007-09-06
tried this for the code now:

```
cd /
cd /home/fazz/Desktop
rsync -axu /media/usbdisk/School\ Work/. School\ Work
cd /
cd /media/usbdisk/
rsync -axu /home/fazz/Desktop/School\ Work/. School\ Work
zenity --title "Coursework Sync" --window-icon "/usr/share/icons/Human/16x16/status/dialog-information.png" --info --text "Your files have been Synchronised."
```

It appears to work though, just interested to get the window dimensions working now.

---

### Post by The_Id on 2007-09-07
> **fazza said:**
>  btw, what exactly does -a and -x do? I did look in the help, but didn't understand it. 
-a is the same as putting in -rlptgoD all at the same time, which is the normal settings for archiving something.
-x keeps it from traveling to more then one file system, for example if you were (rsync)ing the root '/' it would not sync the /media/usbdisk with its self.

Also I saw an [article]("http://www.linuxjournal.com/article/9311") that explained how to make the usb run a script automatically when you insert it.

---

### Post by huzzak on 2007-09-22
Thanks for all of the resources.  I've modified what fazza wrote so that it can be done automatically according to the methods described in the [link]("http://www.linuxjournal.com/article/9311") that The_Id posted.

This file goes in /usr/local/bin with the filename "sync-thumb.sh
```

#!/bin/bash
#
# CONFIG SECTION
# Local folder to sync with
SYNC_LOC=/home/jlutes/Desktop/TEST
# Device folder to sync with
SYNC_DEV=TEST
#
# SCRIPT SECTION
# Wait for thumbdrive to settle
sleep 10
# Synchronize thumbdrive with local
rsync -axu /media/disk/${SYNC_DEV}/ ${SYNC_LOC}/
# Synchronize local with thumbdrive
rsync -axu ${SYNC_LOC}/ /media/disk/${SYNC_DEV}/
# Inform user that synchronization is complete.
zenity --title "Thumbdrive Sync" --info --text "File synchronization complete."

```

This file goes in /etc/udev/rules.d in a file called "95.backup.rules"
```

BUS=="usb", SYSFS{serial}=="00001619C17352CE", SYMLINK=="jet_drive", RUN+="/usr/local/bin/sync-thumb.sh"

```
The serial number should be replaced as described in the [article]("http://www.linuxjournal.com/article/9311") The_Id linked to.

I have two issues with it.  For some reason the zenity dialog indicating completion isn't popping up.  I guess I have to pipe it somewhere, but I don't know.  Another problem is that the copied files are given executable status, which I don't like and wish I could prohibit.  Thanks for any comments and suggestions.

---

