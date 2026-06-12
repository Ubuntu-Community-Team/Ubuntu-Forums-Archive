---
title: "Run Protions of Ubuntu from RAM?"
date: 2008-04-20
forum: General Help
---

### Post by BadServo on 2008-04-20
I've been running Ubuntu for some time now on systems with 4GB of RAM.

However, I notice that I seldom hit even 1GB of RAM usage even with no swap partition.  It seems as though it should be possible to put that extra memory to good use.  As it stands I've eliminated my swap partition and install the preload package.

Any other advice to keeping things cached or otherwise improving performance with extra RAM would be appreciated.

Also, would it be possible to setup a RAMdrive that I could install portions of Ubuntu (var, lib, etc) to.  I realize that this is dangerous, but I have fairly good backup power.

---

### Post by jpkotta on 2008-04-20
There is already a tmpfs filesystem at /dev/shm.  You could copy what you need there and symlink it.  It would probably be a good idea to make it read only then (there is a reason why /bin and /usr/bin, etc. are read only for users).

OTOH, the easy way to do this is to simply let the kernel do its job (managing hardware).  If there is free RAM, Linux will cache whatever it reads from the disk there.  It's treated as unallocated memory in the sense that it's just overwritten when more RAM is requested.  If you enable a swapfile, then you get more cache, and it will probably make your system more responsive on average (but still with those noticable lags when something needs to get swapped back into RAM). You can tune how soon things get swapped to disk by writing to /proc/sys/vm/swappiness.

You can see how RAM is being used with the "free" command.

---

### Post by sdennie on 2008-04-20
I would not recommend trying to manually fill what appears to be empty RAM.  Your apps may only be using 1G of RAM but linux is using the rest of your RAM for cache.  It's effectively creating a RAM disk for you over time except that it's only filling it with stuff you've already used.  Over time, I would imagine that's a better algorithm than brute forcing a RAM disk with something like /usr/lib or /var (which is going to have hundreds of megs of stuff you'll never need).

---

### Post by bingoUV on 2008-04-20
vor, I don't think it is always a better algorithm. Given that kernel developers do not know the user's installed RAM amount, and their requirements, this is the best they could do. But once we know these, we can do better. Preload is a step in the right direction.

The problem is  : I start firefox. It will load binary executables and libraries worth a few MBs. Kernel will now cache it so that when I start firefox next time I can do it faster. But I never close my firefox once started. So the only time I start it, it is always slow and the cache is not useful. 

If on the other hand, the executables and libraries were in RAM **before** I start it for the first time, RAM would be put to better use.

---

### Post by sdennie on 2008-04-20
Well, I wouldn't claim that it's an optimal algorithm but, it's less wasteful of RAM than creating a RAM disk of, for instance, /usr/lib or /usr/bin.  Also, it can be manipulated in a more fine grained way to essentially pre-cache an application so it and all of the files that it touches on startup are already sitting in cache when you go to start the app.  See [this]("http://ubuntuforums.org/showthread.php?t=565651") thread for more information on how to use readahead.

---

### Post by bingoUV on 2008-04-21
Thanks, I did not know about readahead. Do you know what is the difference between 
```

cat /path/to/library.ld.so.2 > /dev/null

```

and 
```

readahead-list /path/to/library.ld.so.2

```

Catting a big file to null increases my ram usage (in the buffers department) so I thought it is good enough.

---

### Post by sdennie on 2008-04-21
There is a companion tool to readahead-list called readahead-watch that watches disk activity for a period of time (until you kill it) and generates a list for readahead-list.  I believe that readahead-watch has some sort of understanding of how files are physically laid out on the disk and so the list it generates is supposed to minimize seeks when it's fed to readahead-list.  My guess is that readahead-list is probably just a big for loop that does indeed just cat a bunch of files to /dev/null.

---

