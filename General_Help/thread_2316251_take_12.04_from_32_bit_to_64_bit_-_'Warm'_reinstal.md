---
title: "take 12.04 from 32 bit to 64 bit - 'Warm' reinstall posible?"
date: 2016-03-06
forum: General Help
---

### Post by candtalan on 2016-03-06
Currently running Ubuntu 12.04 32 bit and am going to take it from 32bit to 64bit - it would be most onvenient to do a warm reinstall from 32 to 64...
That is, choose 'something else' and direct to the existing partition, leaving the partition 'not format'.
Anyone know if this will/should work?
It seems to me that the ext4 format will not change with 64bit, nor the data files (Home), only the installed (executables) is this correct I wonder?
tia

---

### Post by grahammechanical on 2016-03-06
You might be the first person to try this. Let us know how it goes. For myself, when I converted from Ubuntu 32 bit to Ubuntu 64 bit I did not leave the root ( / ) partition unformatted.

It is my guess that some 32 bit libraries will be over-written by 64 bit libraries but others will not be over-written. Who knows what effect that will have.

The safe way to do this would be to back up important data and re-install 64 bit over 32 bit using the Something Else option and formatting the partition. If you do not have a separate /home partition then this would be the time to create one. Either that or create a partition just for your data/documents.

I once listened in on a discussion by Ubuntu developers on the subject of offering users an option to safely upgrade from 32 bit to 64 bit. The answer was: "It is technically possible but it is a non trivial thing to do." Non trivial is a developer's way of saying, it is too much work. 

Regards.

---

### Post by oldfred on 2016-03-06
It actually should work, but all the old logs, 32 bit files and other junk will still be taking up space and difficult to houseclean.
And any file that has configurations, will be reset. So if you have customized anything that is lost unless you back that up. All your data will still be there, but better to reorganize and create separate /home or /mnt/data partition as grahammechanical suggests.

 Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872) 


When I converted, I also was not sure, but had data in data partitions, so was able to just install the 64 bit version into another 25GB / (root) partition. Then anything I forgot was still there to go back and get. But that lead me to my backups.
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by howefield on 2016-03-06
What should happen is that all system folders should be deleted with only /home left intact.

Not the way I'd recommend doing it, but you should be fine :)

As always, good backups of your important data are a must before carrying out risky manoeuvres on your disk.

---

### Post by candtalan on 2016-03-06
Thanks for the great comments! I am techy but not so much... and so I think I will play safe and go for a clean install. My substantial data is on a separate HD anyway, but it does not sound like a good idea to leave a few problems to be discovered later when I am in a sweat!
Thanks again, much appreciated!

---

