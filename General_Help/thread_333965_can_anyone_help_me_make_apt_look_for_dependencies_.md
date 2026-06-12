---
title: "can anyone help me make apt look for dependencies in local folder"
date: 2007-01-08
forum: General Help
---

### Post by seshomaru samma on 2007-01-08
I fresh installed Xubuntu Dapper on this box that doesnt have an internet connection. I then copied var/cache/apt/archives from another machine to a folder on the new box and started instaling the applications there. The problem is dependencies . Even though I got all the packages and their dependencies in that folder ,apt keeps looking for the dependencies in the repositories .
Is there anyway for me to configure apt so it will look for the dependencies in that local folder. I dont want to install them manually because there many of them (i tried it).

---

### Post by xopher on 2007-01-08
> **seshomaru samma said:**
> I fresh installed Xubuntu Dapper on this box that doesnt have an internet connection. I then copied var/cache/apt/archives from another machine to a folder on the new box and started instaling the applications there. The problem is dependencies . Even though I got all the packages and their dependencies in that folder ,apt keeps looking for the dependencies in the repositories .
Is there anyway for me to configure apt so it will look for the dependencies in that local folder. I dont want to install them manually because there many of them (i tried it).

First you need to create a Packages.gz file in the directory you have the debs, this will make the directory usable as a repository. To do this:

```
dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
```

Then just add this to your sources.list:

```
deb file:///path/to/debs/ ./
```

save the file and do a:

```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by seshomaru samma on 2007-01-08
Interesting , I tried something similar that I picked from a Debian Howto but it didn't work , the idea was the same but the commands slightly different.
I will try your method tomorrow ,let you know.
Thanks

---

### Post by seshomaru samma on 2007-01-09
dpkg-scanpackages got me a 'command not found' but a Packages.gz was created
still after i added the sources list apt couldnt find anything so i guess the problem is in the first command
btw- can you explain the first command - why . /dev/null?
in [this debian]("http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html") howto the command is slightly different (with the same result though..)
( dpkg-scanpackages debs file | gzip > debs/Packages.gz)

---

### Post by seshomaru samma on 2007-01-13
another update > i try the same command on an Ubuntu (gnome) and it worked , is XFCE missing something? how come i got 'command not found' in Xubuntu?
maybe its that particular installation thats buggy

---

