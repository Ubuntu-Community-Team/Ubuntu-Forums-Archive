---
title: "cookie crowding"
date: 2024-08-04
forum: General Help
---

### Post by oneleded on 2024-08-04
i have 3 instance's of linux on my SSD. lubuntu, Q4os, and Sparky. no matter which one i am on, they stall, and act up, when it gets to 150MBs. i clear the cookies and such, and not to long of a time the problem is back, no matter which version i am using. im thinking about doing a clean install of all three, but want to know 1st. if there is a different solution. i have used the console to do basic commands, like auto-clean purge, and about 3 more, it does not seem to help in the long run. any help is much appreciated.  //ed

---

### Post by guiverc on 2024-08-04
You haven't provided any specifics as to release (eg. *you mention Lubuntu, but nothing further, so the Lubuntu reference doesn't tell me much at all as differences occur over time*).

The obvious though is given it occurs on 3 different OSes, the problem is something likely common to all three, ie. hardware?? or if you set them up the same; your setup??  

---

You mention three OSes, but give no clues as to their software stack (age or release details is somewhat critical here & the best indication), as ~all GNU/Linux distributions tend to start from the same upstream sources for our code, the difference is mostly when & from where we grab it; thus *timing* is the difference; and that is usually shown best in release details (Lubuntu being very easy given the *year.month* format of version!).  Are your three OSes the same *stack age* is something I'd contrast; if they're are - them acting the same will of course mean less, so I'd boot a *live* system with a very different stack & test that to explore OS more.

---

### Post by currentshaft on 2024-08-05
.

---

### Post by oneleded on 2024-08-08
@currentshaft; cache, is the word i am missing., unless it is in front of me, my brain will not spell it.. dyslexia thing.. Q4os on 0np4, Lubuntu 20.04 is on 0np3, Sparyt7 is on 0np2.. i intend to update Lubuntu soon enough. i Have another SSD drive, if needed. i dint think the current drive is the problem, Lubuntu, is a bit more full then i like. all three though, tend to act up, go haywire, whenever when the cache hovers at 150mbs of cache, and i have to clear it. Then they act normal again. it would seem to me, that the cache, would be different, different os's, different balance. hardware is the same, guess it could be that. maybe the way i got the wi-fi set up is another thought. IDK

---

### Post by currentshaft on 2024-08-08
.

---

### Post by oldfred on 2024-08-08
Do you have limited RAM, so default in memory cache is small?
You show a lot of unallocated drive space. Might be better then at end of drive, not next partition) to put in a partition as cache and use it.
If not hibernating, you can use one cache for all installs. And hibernating not recommended.

My old laptop only had 1.5GB of RAM, so if I loaded more than one large app with maybe a couple smaller ones, it would go to cache. The cache partition on old HDD so slow, so I would have a several second gray screen. Then tried an external SSD. Still tried to not load too many apps at once, but if I did, I could only see a flicker when using cache on much faster SSD.

---

### Post by oneleded on 2024-08-10
OK, i will try harder. i am not posting what the cut off point is, the 3 Os's, that i have. do bear with me, for i am trying, i thank you for that.

---

### Post by oneleded on 2024-08-11
i tried to do some things suggested by post #7, which is not here now, so i am post #7. h
Filesystem      Size  Used Avail Use% Mounted on
udev             16G     0   16G   0% /dev
tmpfs           3.2G  1.8M  3.2G   1% /run
/dev/nvme0n1p3   59G   21G   36G  37% /
tmpfs            16G     0   16G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs            16G     0   16G   0% /sys/fs/cgroup
/dev/nvme0n1p1  3.8G   25M  3.7G   1% /boot/efi
tmpfs           3.2G   12K  3.2G   1% /run/user/1000
i have done forgot what command this was, and will have recreate it. nvme 0n1p3 is lubuntu 20.04, that which i intend to replace with lubuntu 22.04.. i have more to add, and will be back..

---

### Post by currentshaft on 2024-08-11
.

---

### Post by oneleded on 2024-08-13
sites that i visit quit working, or seem broken. i delete cache, they start working again. i ran bleach bit though, and the commands to clean Lubuntu again, it seems to be working better. i am going to reinstall sparky7, with sparky7.4., as to get to a better version, and clean q4os, to see if that will help. somewhere, i read, the SSD didnt need a swap file more then once. anyway i added a 7GB swap file. im going to get Lubuntu 22.04 as well. i will keep informed...
1 of the sites i go to, loaded cache up really fast 3 times. there are others, not quite so fast, but do the same i think. i gotta go through Firefox, again, and redo my settings.

---

### Post by donaldslacks on 2024-08-14
A clean install might be helpful, but before that, consider extensions. Maybe an aggressive extension in one browser is causing issues across all systems. Try disabling extensions and see if it improves.

---

### Post by currentshaft on 2024-08-14
.

---

### Post by oneleded on 2024-08-24
i found the problem. two or three cookies are always there, when i have a problem. att.net, att.com, and yahoo.com, probably any other cookie connected to them. i definitely got to get better e-mail.

---

### Post by currentshaft on 2024-08-24
.

---

### Post by oneleded on 2024-08-27
i believe you are right on this.. i'm marking the problem solved..

---

