---
title: "Beagle Problems"
date: 2005-06-17
forum: General Help
---

### Post by mike998 on 2005-06-17
After seeing many posts on Beagle, I decided to install it.  I have followed the instructions to install it at the following page : [http://beaglewiki.org/index.php/UbuntuInstall](http://http://beaglewiki.org/index.php/UbuntuInstall) 
The only difference is that my hard drive is partitioned to just a root, swap and that's it.  Here's my /etc/fstab:
```
mike@wolfspider:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro,user_xattr 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
``` 
This is due to the partitioning that is default with the system install...
I have run the daemon using the following command : beagled --fg --debug
However, when beagle gets to the first directory in my home directory it seems to stick, and won't index any files beyond that.  Here is the output:
```
DEBUG: Starting task File System Crawler
DEBUG: Crawl Task Scheduling /home/mike/Shorts (state=PossiblyClean)
DEBUG: Finished task File System Crawler in .00s
DEBUG: Starting task Crawling /home/mike/Shorts
DEBUG: *** What should we do with /home/mike/Shorts/batman_dead_end_full_screen.mpg?
DEBUG: *** Doing nothing to /home/mike/Shorts/batman_dead_end_full_screen.mpg
DEBUG: *** What should we do with /home/mike/Shorts/Grayson_web_large.mov?
DEBUG: *** Doing nothing to /home/mike/Shorts/Grayson_web_large.mov
DEBUG: *** What should we do with /home/mike/Shorts/Worlds_Finest_Hi.mov?
DEBUG: *** Doing nothing to /home/mike/Shorts/Worlds_Finest_Hi.mov
DEBUG: *** What should we do with /home/mike/Shorts/weapon_of_choice_-_fatboy_slim.asf?
DEBUG: *** Doing nothing to /home/mike/Shorts/weapon_of_choice_-_fatboy_slim.asfDEBUG: *** What should we do with /home/mike/Shorts/artofthesaber.mov?
DEBUG: *** Doing nothing to /home/mike/Shorts/artofthesaber.mov
DEBUG: *** What should we do with /home/mike/Shorts/artofthesaber_concept.mov?
DEBUG: *** Doing nothing to /home/mike/Shorts/artofthesaber_concept.mov
DEBUG: *** What should we do with /home/mike/Shorts/BattleStar Galactica - 2004 Pilot movie [Full] (Exxon's VP6).avi?
DEBUG: *** Doing nothing to /home/mike/Shorts/BattleStar Galactica - 2004 Pilot movie [Full] (Exxon's VP6).avi
DEBUG: *** What should we do with /home/mike/Shorts?
DEBUG: *** Doing nothing to /home/mike/Shorts
DEBUG: worker added: name=HandleConnection (899) refcount=1
DEBUG: worker removed: name=HandleConnection (899)
DEBUG: Done sending request
DEBUG: Finished task Crawling /home/mike/Shorts in .02s
``` 
Which repeats over and over...  Does anyone have any idea why this is?  I really like the look of beagle and it would make it easier to find stuff, but it's just plain not working.

---

### Post by mike998 on 2005-06-17
Guess I should have searched the threads a little better: [http://ubuntuforums.org/showthread.php?t=41999](http://ubuntuforums.org/showthread.php?t=41999) 

If the mods want to lock this thread, please feel free.

---

