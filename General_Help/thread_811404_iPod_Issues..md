---
title: "iPod Issues."
date: 2008-05-29
forum: General Help
---

### Post by lszanto on 2008-05-29
Ever since I have upgraded to Hardy Heron, for some reason it seems that programs on my computer do not see my iPod(5g 60gb). I can browser and edit the files on the ipod using nautilus but when trying to use banshee and other media programs they do not detect any ipod. The one program that will sync and detect the ipod is Songbird.

Has anybody else had this problem or have any ideas on how to fix this?  I would really like to get my ipod working.

---

### Post by psyopper on 2008-05-31
+1 for this problem.

Ipod functionality was flawless under Fiesty and Gutsy. My Ipod icon appears on the desktop and Rythmbox opens, but I use Banshee and it does not see the Ipod.

I upgraded to Hardy and I noticed a few things drive wise. Primarily, all of my HDx drives changed to SDx which totally screwed up my fstab (and thus mounting my music volume). Could this be related?

---

### Post by sparkguitar05 on 2008-05-31
iPod support sucks in linux.  I keep Windows around just so I can use iTunes to sync with my iPod.

---

### Post by shifty_powers on 2008-05-31
have ya checked out rockbox?

[http://www.rockbox.org/](http://www.rockbox.org/)

i use it on my 5th gen 30gig ipod video, and it rocks, especially the drag and rop support :D

---

### Post by Bigtime_Scrub on 2008-05-31
I just got my 80G Classic working with Amarok after a long frustrating fight. Im willing to help you out, I know what a pain in the behind it can be. 

Does it mount correctly?

---

### Post by psyopper on 2008-05-31
Yeah, it mounts correctly. Worked beautifully and pain free in Banshee/Feisty and Banshee/Gutsy. Just doesn't work in Banshee/Hardy. Apparently there's a known issue that's being resolved that effected lots of distros (Red Hat, Suse, Gentoo, Ubuntu).

[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/139226]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/139226")

Interestingly enough, I am having this problem and never even had podsleuth installed!

---

### Post by psyopper on 2008-06-05
The Banshee update this morning seems to have fixed this problem. Banshee now loads my ipod and all is well. Interestingly it gave me a message along the lines of "Banshee doesn't recognize this ipod, please go to our web site and update the version so we can have future versions of Banshee recognize it correctly."

Works like always though. I wonder if it was related to me replacing the drive in my 4GB Mini to a 16GB CF card and it was a drive size reporting thing.

---

### Post by Keith Hedger on 2008-06-05
I use rockbox exclusivly and have done for about a year its themeable free and constantly evolving and makes the apple software look rather dull and bland and absolutly no problems with linux (its all drag and drop none of that awful itunes db to muck about with)
dump apple and rockit!

---

### Post by Desterie on 2008-06-05
OK, I am willing to try this rockbox thing.  I clicked on the releases and it said there were no new releases, to get a current build instead.  So what does that mean in newbie terms?

Currently downloading the ipod video build.  Do I have to do anything special to install it?

Thanx

---

### Post by Keith Hedger on 2008-06-05
i think this is the link u need:
[http://download.rockbox.org/manual/rockbox-ipodvideo/rockbox-build.html](http://download.rockbox.org/manual/rockbox-ipodvideo/rockbox-build.html)
anyway just download or view online the relevent manual for your ipod and follow the instructions, I would suggest a manual install
PS you must have a windows formated ipod (FAT32)
PPS !!!! BACK UP YOUR DATA FIRST !!!!

its a bit fiddly to install but when u have the bootloader installed u just download a fresh build (i build from svn) and unzip it to the root folder of your ipod its easy after that.

---

### Post by shifty_powers on 2008-06-05
what you need is the rockbox utility...

[http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility](http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility)

it will be able to install rockbox for you and do everything automatically.

much easier.

and rockbox, well, rocks ;)

---

### Post by Desterie on 2008-06-05
AH, the joys of noobieness.  I got the file for my ipod.  Gotta extract it to the ipod root.   How do I find out where that root directory is for the ipod is?

---

### Post by Keith Hedger on 2008-06-06
the root directory of any drive is the topmost level of the drive ie for your linux system it is / for your ipod it will be the mount point (probably something like /media/ipod)

dont worry we were all noobs once!

i prefer manual install because if something does go wrong you are more likely to know what u did and what bit to fix (just a personal preference), and i dont like programs that install stuff without me knowing what and where has been installed (is that good english?)

---

