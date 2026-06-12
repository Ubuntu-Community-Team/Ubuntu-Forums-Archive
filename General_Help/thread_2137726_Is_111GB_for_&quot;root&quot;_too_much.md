---
title: "Is 111GB for &quot;/root&quot; too much?"
date: 2013-04-21
forum: General Help
---

### Post by Juniorr on 2013-04-21
I bought a 1TB drive, I'm planning on doing the following partitioning:

320GB for Windows, I use Windows ONLY for games.

111.51GB for root
500GB for /home

I plan to install all my programs on Linux, also using VBox and Wine for those that need Windows to run. On the /home side, I download lots of music (about 100GB downloaded and 50GB copied from CD's, most of them from the 90's), movies, series, Documentaries and such, and I'll also install Steam, which stores all game's data on /home.

---

### Post by deadflowr on 2013-04-21
Personally, I don't think you can ever have too big a root partition.:P

But, in all fairness, you could go with half that, and still have plenty of space to work with.

Ideally, I'd say 30GB should be more than enough, even pushing it down to 20GB should be suffice.

---

### Post by wildmanne39 on 2013-04-21
If you are going to install a lot applications then I recommend 20 to 30 is good most people recommend much smaller but I always need at least 20 but I am not changing version of ubuntu every six month anymore.

---

### Post by pqwoerituytrueiwoq on 2013-04-21
my root partition tends to be under 6gb at any given time under 5gb if i use a separate on for /tmp and /var
the only time you may need over 10gb is when you upgrade the system

---

### Post by Juniorr on 2013-04-21
I was planning to use 40GB but I'm affraid that it's not gonna be enough at some point from now on. I always used 20GB but I kept all my work focused on Windows at the time, not much programs on Ubuntu were installed.

I'm going to use Audio/Video editors, Blender, Vbox, Steam, Wine, Gimp, Inkscape, install some games from the Software Center for my daughter and who knows what elsI might install. Should 40GB do it?

---

### Post by pqwoerituytrueiwoq on 2013-04-21
40gb for root sounds fine to me given /home is separate

---

### Post by Juniorr on 2013-04-21
OK, I guess it's fine then =)

Thank you all.

Have a nice week.

---

### Post by matt_symes on 2013-04-21
Hi

Wow you guys use a lot for root.

```
matthew-S206:/home/matthew % df -h | grep "/$" 
/dev/sda8        15G   12G  2.4G  83% /
matthew-S206:/home/matthew % 
```

My home partition is on the root directory. 

```
matthew-S206:/home/matthew % du -cshPx ~
3.6G    /home/matthew
3.6G    total
matthew-S206:/home/matthew % 
```

However all of my main folders are actually symlinks on a storage partition and that is where most of my data is stored.

```
matthew-S206:/home/matthew % ls -l | grep "^l" 
lrwxrwxrwx  1 matthew matthew        35 Dec 28 15:03 Documents -> /home/matthew/storage/my_documents//
lrwxrwxrwx  1 matthew matthew        35 Dec 28 15:06 Downloads -> /home/matthew/storage/my_downloads//
lrwxrwxrwx  1 matthew matthew        31 Dec 28 15:01 Music -> /home/matthew/storage/my_music//
lrwxrwxrwx  1 matthew matthew        34 Dec 28 15:04 Pictures -> /home/matthew/storage/my_pictures//
lrwxrwxrwx  1 matthew matthew        32 Dec 28 22:04 Public -> /home/matthew/storage/my_public//
lrwxrwxrwx  1 matthew matthew        31 Dec 28 14:59 Videos -> /home/matthew/storage/my_video//
matthew-S206:/home/matthew % 
```

My home directory is really a dumping ground for things until they are sorted out.

So my root directory is 15G with ~ 8.5G used for installed apps etc.

20-40G should last you a lifetime :) Then again, i'm not a gamer and they take up space.

Indecently 15G for root is big for me but that is because i decided to keep /home on root.

Kind regards

---

### Post by oldos2er on 2013-04-21
My root partition is 26GB, of which I'm currently using almost 9GB. I usually install a lot of software. I do have, by comparison, large /home and /opt partitions.

---

### Post by oldfred on 2013-04-22
As long as we are comparing:
fred@fred-Precise:~$ df -h | grep ".*/$" 
/dev/sdd3        28G  9.7G   17G  38% /
fred@fred-Precise:~$ du -cshPx ~
2.2G    /home/fred
2.2G    total


My /home is larger as I run Windows version of Picasa in .wine and have not attempted to move it. Everything else including some larger folders normally hidden like Firefox and Thunderbird profiles are in data partitions.

---

### Post by CatKiller on 2013-04-22
Just so you're aware, the /root that you refer to in the title is root's Home folder. The mount-point for the partition you're talking about is /.

Yes, 111 GB is too much for /root :)

---

### Post by Juniorr on 2013-04-22
I used 40GB, I'm not gonna miss this space or anything, I have plenty of space right now. I dumped the /swap partition (10GB because I'll install another 4GB mem stick), I've never used it AND it gives me headaches trying to understand and solve the "cryptswap1 is not ready", caused by /home encryption.

So it's:

Windows = 320GB
/           = 40GB
/home    = 571.51GB

---

### Post by 3Miro on 2013-04-22
20GB of root is enough in most cases. 50GB is perhaps an overkill. 

BTW wine applications and VirtualBox both install the bulk of their data in /home/, you may add that to your calculations.

Why don't you have a single partition for both root and home?

---

### Post by Juniorr on 2013-04-22
> **3Miro said:**
> Why don't you have a single partition for both root and home?
In case I need to format I can keep all my data on /home. I guess there is an option to re-install but if I recall that option says "This will erase all your data" so I kind of feel more confortable with sepparate partitions.

---

### Post by roly33 on 2013-04-23
I just let the Ubuntu Installer sort out my Partitions, so I've just got a 320GB / Partition.

I hate trying to Partition as I never end up with the Partitions the size I want them and always find that 1 is slightly bigger than the other when I try to Partition equally.

Roland

---

### Post by 3Miro on 2013-04-23
> **Juniorr said:**
> In case I need to format I can keep all my data on /home. I guess there is an option to re-install but if I recall that option says "This will erase all your data" so I kind of feel more confortable with sepparate partitions.

I think newer versions of Ubuntu can sort this out automatically, however, you should double-check.

If you go with root, 20-30 should be enough.

---

