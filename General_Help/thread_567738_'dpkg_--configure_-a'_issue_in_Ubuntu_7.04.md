---
title: "'dpkg --configure -a' issue in Ubuntu 7.04"
date: 2007-10-04
forum: General Help
---

### Post by AdHavoc on 2007-10-04
I was downloading some packages, and the computer shut down (battery ran out), and ever since, whenever I try to launch Synaptic Package manager, I get the message:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

Yet when I run the command in terminal, I get the following error message:

"dpkg: parse error, in file `/var/lib/dpkg/status' near line 32:
 missing package name"

I know there is a "[sudo] dpkg --clear-avail" command to fix parse errors in the file 'available,' but I am at a loss at how to fix this issue.  Any help?

---

### Post by SpiritIsReality on 2007-10-04
howdy
I don't know, and I've never had to, but these guys seem to know
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22dpkg%3A+parse+error%2C+in+file+%60%2Fvar%2Flib%2Fdpkg%2Fstatus%27&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22dpkg%3A+parse+error%2C+in+file+%60%2Fvar%2Flib%2Fdpkg%2Fstatus%27&btnG=Google+Search&meta=)
[http://ubuntuforums.org/showthread.php?p=1459612](http://ubuntuforums.org/showthread.php?p=1459612)
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22dpkg+--clear%22-avai&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22dpkg+--clear%22-avai&btnG=Search&meta=)
[http://ubuntuforums.org/showthread.php?t=114504](http://ubuntuforums.org/showthread.php?t=114504)
I hope you can glean the right answer form there.

buds

---

### Post by AdHavoc on 2007-10-05
I followed the instructions in the last thread:

First:
 cd /var/lib/dpkg/
Second:
 sudo mv status status.broken
Third:
 sudo cp status-old status

It seemed to work fine and dandy but when I again ran "sudo dpkg --configure -a" I ran into a different problem.  This time it was:

dpkg: parse error, in file `/var/lib/dpkg/updates/0002' near line 1:
 field name `

I opened /var/lib/dpkg/updates/0002 in gedit, and it is just a blank file.

---

### Post by SpiritIsReality on 2007-10-05
howdy
I don't know ... but if I was me I'd mv it too?
what do you think is best?
YouAreInTheSaddle
I didn't even know there was a dpkg --clear-avail til I got here.
The answer is somewhere between aptitude and dpkg. I don't know my way around either one.
I haven't been fortunate enough to be forced to learn them in detail yet.
did some searching, but that doesn't look like it's a very good replacement for experience.
man dpkg looks like the place to look. sorry I'm not the right guy answering you.
edit : [http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html)
edit : I don't know, but it seems running 
     # apt-get -f install
     # dpkg --configure -a
meaning sudo apt-get -f install and sudo dpkg --configure -a like it says there, multiple times, might help. hope so.
what little I know about aptitude, is that it's a lot better than apt-get, but I don't know for sure about it fixing this.
[https://help.ubuntu.com/community/AptitudeSurvivalGuide](https://help.ubuntu.com/community/AptitudeSurvivalGuide)
[http://people.debian.org/~dburrows/aptitude-doc/en/]("http://people.debian.org/%7Edburrows/aptitude-doc/en/")
I've gotta go, back in 12 hrs or so.
if you don't have any success, post again , now and often.
edit: suggestion, if it seems there's going to be a lot of these, waiting to pop up one by one, it might be an idea to post the problem in the programmer forum and ask for a bash script that would cd, then mv then cp  to all the files there? maybe ask for a complete script?
YouAreInTheSaddle
I used to just reinstall right away when I got into these jams, but there's things to be learned...but reinstall is a hell of a backup plan for me. 
buds

---

### Post by SpiritIsReality on 2007-10-05
howdy
[www.ubuntuwire.com](www.ubuntuwire.com) The Ubuntu Search Engine
search
[http://www.ubuntuwire.com/index.php?cx=015625750094112125028%3A7utzntxrw5m&cof=FORID%3A11&q=dpkg+(%22power+failure%22+%7C+%22power+interrupt%22&sa=Search#928](http://www.ubuntuwire.com/index.php?cx=015625750094112125028%3A7utzntxrw5m&cof=FORID%3A11&q=dpkg+(%22power+failure%22+%7C+%22power+interrupt%22&sa=Search#928)
buds

---

### Post by SpiritIsReality on 2007-10-05
howdy
OK , I checked the /var/lib/dpkg/options directory on this rig, and there are no files in it. So, 
 I ran the  :> 
First:
 cd /var/lib/dpkg/
Second:
 sudo mv status status.broken
Third:
 sudo cp status-old statusthen ran sudo aptitude update and checked the /var/lib/dpkg/options again and there are no files there. (except for the . and .. in all directories) 
If I was me, I'd take a chance and remove all the files that show in the options directory, ...?
[http://www.google.ca/search?hl=en&q=dpkg%2Foptions&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=dpkg%2Foptions&btnG=Search&meta=)
[http://ubuntuforums.org/archive/index.php/t-457546.html](http://ubuntuforums.org/archive/index.php/t-457546.html)
buds

---

