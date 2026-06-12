---
title: "Boot / drive visibility / taskbar(?) inoperability problems  (ubuntu broken big time)"
date: 2007-08-09
forum: General Help
---

### Post by djrobthaman on 2007-08-09
Hi, (Before I go any further I have to apologize.  This explanation is really long.  Sorry :) )

I have a problem.  A big problem.

(Background:  I don't know if this ties in at all.  But before I had any of these problems I had a tiny one with either the grub loader or the boot sequence of ubuntu.  For some reason the oly way I could guarantee that the boot sequence for ubuntu would start was to actually wait the 10 seconds for grub to load the default os.  If i clicked on any ubuntu option that was shown 99 times out of 100 it wouldn't start booting no matter how much I waited.  windows booted fine though)

My PC dual boots xp professional and ubuntu feisty.  Within the last week I noticed that ubuntu was acting strangely.  Well, to clarify it didn't behave any differently than usual except for the fact that it froze twice.  I figured something went wrong but no biggie, it was probably fixed by whatever marvelous code lives underneath the hood.  But now I think not.

Yesterday I booted back into windows (a rare occurrence now) to rip a dvd.  Then when I rebooted and let it fall into the ubuntu boot sequence everything seemed fine until the status bar got about a third of the way across.  Then I noticed the hard drive light went out and nothing happened.  I let it stay there for what I knew was way too long and then hit the reset button.  

This happened about three times before I finally got a different response.  This time, everything I described above happened but then I got knocked into the shell with messages about files being truncated.  After all that I get an error message saying there's something wrong with my filesystem (wtF???) and it's saved to a log file (\var\log\fsck\checkfs).  And that once I fix the problem manuallly I can press control D to continue the boot sequence.

Hidden in the error message is a line saying apt cannot be found and can be installed by typing apt-get install apt (eh???)

So, I hit  vi \var\log\fsck\checkfs (I am currently logged in as root btw, which is a bit confusing because i was never prompted for a password) and get a message saying that vim is not installed and what to do to install it.  I know gedit probably won't work because I think it's a gui editor but I even try to open the file with gedit with the same response.  You do not have gedit installed.  So, I figuer what the hey, and type init 3.

I get all the bells and whistles, log in  and am greeted with what is almost my regular ubuntu install.  The only thing is I'm missing my hard drives on the desktop and the icons on the right of the top gnome panel for the start up programs (I figure they must actually be running though because I get a pop up from timevault).  Also, I can't use the panel.  I click and it does nothing.  Thankfully I have avant installed and had already put a shortcut to the terminal on it.  So I can run pretty much anything.

I look in \media and all the folders where the hard drives should be mounted are empty. And if I try typing sudo mount -a I get a blank like the terminal is working and no matter how long I wait it's still the same.  I can't even get it to stop with control C.  I have to quit the terminal.

Anyway, that's my story.  I don't know what I did.  And I don't really know what's wrong either.  But, is it possible from this explanation of what happened that someone does or, even better, knows how to fix it without losing all my ubuntu data, [references, settings and such????

Thanks a million.

By the way, here's what's written in that log file for the file system check

```

Log of fsck -C -R -A -a 
Thu Aug  9 20:37:25 2007

fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda3: 199 files, 324441/1176742 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
FATs differ but appear to be intact. Using first FAT.
Cluster 4061157 out of range (138278889 > 7320557). Setting to EOF.
Cluster 4131813 out of range (138349545 > 7320557). Setting to EOF.
Cluster 4162533 out of range (138380265 > 7320557). Setting to EOF.
Cluster 4505573 out of range (138723305 > 7320557). Setting to EOF.
Cluster 4607973 out of range (138825705 > 7320557). Setting to EOF.
Cluster 5354469 out of range (139572200 > 7320557). Setting to EOF.
Cluster 6040549 out of range (140258280 > 7320557). Setting to EOF.
Cluster 6468581 out of range (140686312 > 7320557). Setting to EOF.
Cluster 6919141 out of range (134217728 > 7320557). Setting to EOF.
/Nicholas/My Documents/My Music/iTunes/iTunes Music/Stephen Fry/Harry Potter and the Chamber of Secrets/Harry Potter and the Chamber of Secr 5.mp3
  File size is 71024640 bytes, cluster chain length is 53166080 bytes.
  Truncating file to 53166080 bytes.
/Nicholas/My Documents/My Music/iTunes/iTunes Music/The Police/Message In A Box/3-02 Driven To Tears (Live).mp3
  File size is 5277344 bytes, cluster chain length is 3211264 bytes.
  Truncating file to 3211264 bytes.
/Nicholas/My Documents/Downloads/Dragonball z movies (1-13 & special's english)/3-the tree of might.AVI
  File size is 637096888 bytes, cluster chain length is 230588416 bytes.
  Truncating file to 230588416 bytes.
/Nicholas/movies/A Nightmare On Elm Street Part 5 - The Dream Child.avi
  File size is 729421772 bytes, cluster chain length is 659046400 bytes.
  Truncating file to 659046400 bytes.
/Nicholas/movies/A Nightmare On Elm Street Part 7 - Wes Craven's New Nightmare.avi
  File size is 733741056 bytes, cluster chain length is 34701312 bytes.
  Truncating file to 34701312 bytes.
/Nicholas/movies/Clue.avi
  File size is 733843456 bytes, cluster chain length is 666222592 bytes.
  Truncating file to 666222592 bytes.
/rips/LONGE/VIDEO_TS/VTS_01_7.VOB
  File size is 391577600 bytes, cluster chain length is 341245952 bytes.
  Truncating file to 341245952 bytes.
Warning... fsck.vfat for device /dev/sdb1 exited with signal 11.
fsck died with exit status 8

Thu Aug  9 20:37:58 2007
----------------

```

---

### Post by djrobthaman on 2007-08-09
_UPDATE_

Still having the same problems but for some reason decided to try using firefox to view a web site stored locally on my PC.  I have apache running and I viewed the site perfectly.  Cleared the cache and still was able to see the site.  

The catch is that I have apache set up so that the root folder for the web site is on my windows partition, which I can't see otherwise and thought was not mounting.

What does this mean?????

Why is feisty being such a pain all of a sudden?

Edit:  When I open bluefish, it can view files on sda3 and sda1 (feisty is installed on sda2).  So those drives are getting mounted.  And now I can view them through nautilus (am I crazy?  Did I just miss that before and assume they were empty because the rest were?  I don't know)

---

