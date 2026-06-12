---
title: "/var/cache deleted"
date: 2007-07-27
forum: General Help
---

### Post by sonic256 on 2007-07-27
I was working on clearing my cache for different apps (firefox, thunderbird etc.) and I accidentalyl deleted /var/cache, so now my system is kinda fubar.  Could anyone please give me some help on what to do?  I am on xubuntu 6.06 LTS.

Thanks,
Tim

---

### Post by FleetAdmiral74 on 2007-07-27
I would think you could simply create the folder again, so something like

```
sudo mkdir /var/cache
```

But you might wait for a second opinion.

---

### Post by sonic256 on 2007-07-27
The dir is there just missing alot

When I start up synaptic manager, 
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

That is what I get.

This is the contents on my /var/cache
tim@laptop:~$ ls -R /var/cache
/var/cache:
cups  man  samba

/var/cache/cups:
job.cache  remote.cache

/var/cache/man:
cat1  cat3  cat5  cat7  cat9    index.db  oldlocal  X11R6
cat2  cat4  cat6  cat8  fsstnd  local     opt

/var/cache/man/cat1:

/var/cache/man/cat2:

/var/cache/man/cat3:

/var/cache/man/cat4:

/var/cache/man/cat5:

/var/cache/man/cat6:

/var/cache/man/cat7:

/var/cache/man/cat8:

/var/cache/man/cat9:

/var/cache/man/fsstnd:
ly&t=511110
/var/cache/man/local:
cat1  index.db

/var/cache/man/local/cat1:

/var/cache/man/oldlocal:
cat1  index.db

/var/cache/man/oldlocal/cat1:

/var/cache/man/opt:

/var/cache/man/X11R6:

/var/cache/samba:
browse.dat  printing

/var/cache/samba/printing:
officejet.tdb  printers.tdb


Is there some way I can redownload or reset the structure of that dir?

---

### Post by rillip on 2007-07-27
Is it still in your trash folder for you to simply restore?

---

### Post by sonic256 on 2007-07-27
xubuntu 6.06 dosent have trash.

---

### Post by rillip on 2007-07-28
> **sonic256 said:**
> xubuntu 6.06 dosent have trash.

The fact that xfce doesn't implement a trash icon doesn't mean there's not trash.  There should be a .trash folder in each folder that contains items deleted out of it.

---

### Post by catphive on 2007-08-11
I also deleted my /var/cache when trying to solve a space crunch, and now synaptic package manager gives me the same errors that were mentioned above.

I know for a fact that it isn't in the Trash folder because I checked and because I deleted it with rm.

Is there anyway to get apt-get, synaptic package manager, and whatever else uses /var/cache to regenerate their caches? I'm particularly interested in getting package management working again.

Thanks

---

### Post by kevinlyfellow on 2007-08-11
You can always pop in a live cd and copy the directory from that

---

### Post by catphive on 2007-08-11
OK. I have the solution:

sudo mkdir /var/cache/apt
sudo mkdir /var/cache/apt/archives/partial

and apt-get or synaptic package manager will download whatever files it needs automatically.

If you get any more complaints about missing directories, just sudo mkdir them also. Everything in /var/cache can be regenerated, but some things aren't smart enough to recreate their directories so you need to do it for them.

---

