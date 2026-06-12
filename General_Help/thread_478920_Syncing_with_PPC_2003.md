---
title: "Syncing with PPC 2003"
date: 2007-06-19
forum: General Help
---

### Post by smilliken on 2007-06-19
I finally was able to get my Axim X5 to be recognized using synce-kde, Raki and the rest of the packages required. My problem now is, how do I get my contacts and calender info in kontact to the Pocket PC and visa versa? I can use kcemirror and all of the other functions in Raki and they work, except for the transferring any info. Also, multisunc does not eem to do anything. I've surfed the net with no luck so far.

Any help is much appreciated.

---

### Post by ffoletti on 2007-06-22
here [http://ubuntuforums.org/showthread.php?t=331168&highlight=synce+feisty&page=5](http://ubuntuforums.org/showthread.php?t=331168&highlight=synce+feisty&page=5)
I wrote how I could sync my axim x30...maybe it can be useful..
worked perfectly in edgy, but in feisty I had to sync through multisync and evolution (you can read about this in the same forum page). Anyway, here's how it worked:

1 Connect Pocket Pc to USB
2 apt-get install synce-dccm synce-kde synce-kde-dev synce-serial librra0 libsynce0 libsynce0-dev
3 apt-get install syncekonnector syncekonnector-dev
4 apt-get install kdepim kdepim-dev kdepim-dbg libqt3-headers libqt3-mt-dev kdelibs4-dev kdepim-dev
5 type dmesg :  you should see something like pocket pc connected to ttyUSB0
6 sudo synce-serial-config ttyUSB0 -> the output should tell you that now you can start connection via synce-serial-start
7 now I started raki; raki opens and **you have to select vdccm;**
8 now start syncing: sudo synce-serial-start
9 left click on raki icon, pocket pc, configure and select, e.g., appointments, configure them with select exisiting calendar, choosing korganizer ics file (for me it was the default choice in select existing calendar)
10 syncronize

hope this can help
bye

---

### Post by smilliken on 2007-06-23
One can follow all of these instructions, but they will not work if one does not have ksync installed. 

Installed ksync and away things went.

---

