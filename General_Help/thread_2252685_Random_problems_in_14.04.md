---
title: "Random problems in 14.04"
date: 2014-11-13
forum: General Help
---

### Post by MibunoOokami on 2014-11-13
Hi everyone,

Recently I have been experiencing some random problems in Ubuntu 14.04 and figure it better to list them all in one thread than create a bunch of different threads. The first one is the most important and I would love a solution to ASAP please, other threads I've come across seem to have similar but not the exact same error message. The next two are reasonably important and the last one is less important I guess, but it would be interesting to hear thoughts on what is causing this.

The first one is all of a sudden rsync has started throwing out this error message.
```
rsync: mkdir "/media/BUFFALO/hpbackup" failed: no such file or directory (2)
rsync error: error in file IO (code11) at main.c(674) [Receiver=3.1.0]
```
I don't know why, BUFFALO is the name of the external drive I backup on, hpbackup is the name of the folder where backups have been going and it still exists.

Next problem is software updates. Updates usually appear automatically but the day before yesterday I had an exclamation mark inside a red triangle telling me I haven't updated in X amount of days. 

Another one is compiz closes every now and then with this message ```
sorry the program "compiz" closed unexpectedly. Your computer does not have enough free memory to automatically analyse the problem and send a report to the developers
``` I have 2GB ram and I can't see myself consuming it all.

Two more problems are with a firefox program called ghostery. Since one of its updates ghostery keeps unblocking all the trackers and whatnot that it's supposed to be blocking and it also keeps throwing up a tutorial window and it's starting to drive me up the wall. I don't want to get rid of this program. 


Thanks

---

### Post by ajgreeny on 2014-11-13
For the first let's see the output of ```
ls -laR /media
```which will show if that folder exists or not; if you used 12.04 before and it worked there, it may be that the folder is now /media/**username**/BUFFALO/hpbackup, as automounted partitions are now put in /media/username not just /media.

Is it just rsync that can not see the folder or is it impossible to navigate to it in a file-manager?

I can't help with compiz (I don't use it any more) nor with ghostery, I'm afraid

---

### Post by MibunoOokami on 2014-11-13
> **ajgreeny said:**
> For the first let's see the output of ```
ls -laR /media
```which will show if that folder exists or not; if you used 12.04 before and it worked there, it may be that the folder is now /media/**username**/BUFFALO/hpbackup, as automounted partitions are now put in /media/username not just /media.

Is it just rsync that can not see the folder or is it impossible to navigate to it in a file-manager?

I can't help with compiz (I don't use it any more) nor with ghostery, I'm afraid

I just tried the code, the output appears to be a giant list of the contents of the drive which did include the hpbackup folder. I'm not comfortable posting the output. 

It just seems to be an rsync problem,  because I can navigate to the folder and view its contents in a file manager. I'll see if adding my username helps.

EDIT: Adding my username did nothing, I got the exact same error.

Correction: I forgot 14.04 wouldn't let me use uppercase letters for my username. After changing to lowercase it is now syncing. Thanks for your advice.

---

### Post by MibunoOokami on 2014-11-13
> **MibunoOokami said:**
> After changing to lowercase it is now syncing.

OK it was syncing but seems to have stalled, its been stuck on the same cache file for the last ten minutes which seems excessive.

---

### Post by MibunoOokami on 2014-11-13
There's one more problem I forgot to add. Occasionally my machine decides to act funny and not detect my webcam. Both cheese and skype say no device found and rebooting doesn't help at the time. It just seems to come right by itself. This has happened in 12.04 as well so I don't think it's to do with the version of Ubuntu. 

If anyone has experienced this problem, I would like to hear how you overcame it. Thanks

---

### Post by Impavidus on 2014-11-14
As for the update problem, try to run```
sudo apt-get update
sudo apt-get upgrade
```and post the output, which should contain a useful error message. But this issue seems unrelated, so I think you should start a separate thread for that.

---

