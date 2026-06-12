---
title: "Sbackup fills up boot drive with temp files"
date: 2007-06-09
forum: General Help
---

### Post by thatcooldude on 2007-06-09
I decided to give Sbackup a try after googling for a good "automated" backup solution.  After installing it and setting up my first backup (daily at around 5am, full backup of my media server), I decided to test it out by doing a backup 'now'.  It said it would launch as a background process, so I monitored it via top, and found that the process was using only around .6% of the CPU,  vs. Gzip which was utilizing around 96%.  I figured this was normal, as it was probably compressing the contents of the media drive in order to back up.

The way I setup the backup was to take a 1:1 backup of /dev/sdc1 and copy it over to sdd1.  Essentially, I have two hard drives, wanted one to copy over to the other ALL of its contents.

Well, after letting it run for a few hours, my boot disk is full (presumably from the gzipped file.)  I checked my sbackup.conf file, and it's pointing the target to the correct disk (sdd1) so I don't know why it was storing the gzip on my boot drive (which is a LOT smaller than the media being copied).  Looking through bug reports, it seems that there's an issue with Sbackup not allocating enough space, and it will write up the last little block available before crapping out.

My question is this:  Where the hell is that temp gzip file stored?  I can't boot into Ubuntu anymore because it doesn't have enough space, although I'm comfortable enough in the terminal to erase it manually....just can't figure out where it's stored.  Installing any new apps is out of the question (no space!) so I can't even get a disk inventory program to see what's taking up space!

Are there any terminal commands to show the biggest files on the drive?  Anyone know where Sbackup keeps those temp files while in the process of backing up a drive?

Any help would be greatly appreciated.  Thanks!

-Stephen

---

### Post by thatcooldude on 2007-06-09
Finally got it.  I ended up finding the file in the root's trash can after rebooting.

I can't remember if I actually deleted it, or if it just ended up there.  In any case:

To fix this problem, I:

Killed the running X session by pressing control+alt+1 when the login screen came up.
Typed startx (to attempt to start a new xsession) - It'll already be in use.  Use sudo rm to remove to xlock that the output shows. (Should be /tmp/X something or another)

Then start x by typing 'sudo startx'

Once in, you can go into your trash can and remove the offending files.

I believe you can also log in as root and go to the .Trash folder, but I just now realized it.  Oh well.

Hopefully this helps someone else, or ME the next time I try this :D

-Stephen

---

