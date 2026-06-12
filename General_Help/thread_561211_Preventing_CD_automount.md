---
title: "Preventing CD automount"
date: 2007-09-27
forum: General Help
---

### Post by lofftjm on 2007-09-27
Is there a way I can prevent CD's from automounting?  I already tried going to "System / Preferences /  Removable Drives and Media" and unchecking the "Mount removable media when inserted" box.  CD's still automount however.

My problem is whith Audio CD's.  I want to insert one and mount it manually so I can make an ISO via command line utils.

When I put an audio cd in the drive it creates an "Audio Disc" icon on the desktop.  If I right click the icon and click "Browse Folder" it opens the sound juicer application.  Due to a bug in Sound Juicer it will not make ISO images tha can be used for anything.

If I open Nautilus and click on the "Audio Disc" I get an error:

"cdda:///dev/scd0" is not a valid location.

In Nautilus nothing shows up in any of these locations:

/media/cdrom 
/media/cdrom0
/media/cdrom1

Doing a df from the command prompt doesn't show it mounted anywhere either.

This doesn't seem like this should be this difficult...

---

### Post by eggdeng on 2007-09-27
```
I already tried going to "System / Preferences / Removable Drives and Media" and unchecking the "Mount removable media when inserted" box.
```

Audio cds aren't actually mounted. I suspect you've been looking at the storage tab which is for data cds. You want to go to the multimedia tab and uncheck Play Audio cds when inserted. Check out [http://ubuntuforums.org/showthread.php?t=272009&highlight=cd+eject&page=3]("http://ubuntuforums.org/showthread.php?t=272009&highlight=cd+eject&page=3") post #22

---

### Post by lofftjm on 2007-09-28
Thanks for the response...I unchecked the optios on the Multimedia Tab (play audio cd's when inserted) but it still does the same thing.

I also tried gnome baker.  Couldn't create an ISO with it and extracting the tracks to WAV files produced garbage files...mostly silence...

I can't understand why this is even an issue in Ubuntu...I really do not want to have to boot into Windows anymore and this is one of the few problems I have left to fix.

Any other suggestions?

---

