---
title: "apt-get for this n00b"
date: 2004-12-09
forum: General Help
---

### Post by CacheMonet on 2004-12-09
how do I use apt-get to install the latest versions of gaim and firefox?.. I've tried:

1- apt-get update
2- apt-get upgrade
3- apt-get install gaim [I get message saying latest version is installed.. but it is not]

what am I missing here?

---

### Post by ubuntu_demon on 2004-12-09
probably you are using warty and the latest-version is installed but that means the latest version of gaim available in the warty repositories.

If you want to have newer versions you can get them from hoary. But since you're a n00b I don't recommend it. Wait for hoary to become stable.

see :
Mozilla Firefox 1.0 ?
[http://www.ubuntuforums.org/showthread.php?t=6976](http://www.ubuntuforums.org/showthread.php?t=6976)

---

### Post by Hikaru79 on 2004-12-09
To reiterate what demon666 said, in simpler terms, is that the Ubuntu team has stopped upgrading packages for the "stable" release of Ubuntu (the one that you have), and are putting all new packages into the repositories of Ubuntu's beta release, "Hoary Hedgehog". It's NOT reccomended you switch to Hoary just to get a newer version of gaim from it, because it's very unstable and buggy. Instead, it's much better simply to download the source from the gaim site and compile it yourself. Try that, and ask in here if you're not sure how.

Good luck :)

---

### Post by nigelng on 2004-12-09
Just some idea to show u how to compile gaim from source:

download the gaim<something>.tar.gz  > home directory 

tar -xzvf gaim-1.1.tar.gz
cd gaim 
./configure --prefix=/opt/
make
make install 

this should install gaim into /opt/
and u can run it by command: /opt/gaim/usr/bin/gaim 

However, expect to have some errors during configure step as u might needs couple of library. Report errors here. people might help u.

- For firefox the story is easier
Download firefox-1.0.tar.gz (from [www.mozilla.org](www.mozilla.org)). I assume u get it to ur home directory. the open the gnome-terminal (console)

tar -xzvf firefox-1.0.tar.gz
ls firefox/ (make sure the directory is there)
sudo mv firefox/ /opt
sudo mv /usr/bin/firefox  /usr/bin/firefox-0.9-old
sudo ln -sf /usr/bin/firefox /opt/firefox/firefox (by making this sym link u dont need to change all ur icons).

If your plugins & extension is install locally (in ur home then it's should be there). If you cannot run any extension => update it :)

Report back here if u get any error. Ppl here are really nice to help u. 

Nigel

---

### Post by ubuntu_demon on 2004-12-09
[QUOTE=Hikaru79]To reiterate what demon666 said, in simpler terms, is that the Ubuntu team has stopped upgrading packages for the "stable" release of Ubuntu (the one that you have), and are putting all new packages into the repositories of Ubuntu's beta release, "Hoary Hedgehog". It's NOT reccomended you switch to Hoary just to get a newer version of gaim from it, because it's very unstable and buggy. Instead, it's much better simply to download the source from the gaim site and compile it yourself. Try that, and ask in here if you're not sure how.

Good luck :)[/QUOTE]
 I'll recommend waiting for hoary. But if you really need something you can indeed compile the sources yourself.

off topic :
Nice pics hikaru79. I've watched Hikaru no Go too.Now that I think of it I don't remember if I've seen "Hikaru no Go New Year's Special 2004". Downloading it now :D

---

### Post by p!=f on 2004-12-09
I think the easiest way is to add Hoary sources in /etc/apt/sources.list along the Warty's one. Then create/edit /etc/apt/preferences file and put the following inside:
```

Package: *
Pin: release a=warty
Pin-Priority: 700

Package: *
Pin: release a=hoary
Pin-Priority: 650

```
This is called apt pinning. Now Warty sources has bigger priority so you can choose individual packages to upgrade by running:
```

sudo apt-get install gaim/hoary

```
or
```

sudo apt-get -t hoary install gaim

```

---

### Post by ubuntu_demon on 2004-12-09
I wouldn't recommend apt-pinning to a n00b

---

### Post by p!=f on 2004-12-09
[QUOTE=demon666_nl]I wouldn't recommend apt-pinning to a n00b[/QUOTE]
You really don't need expert skills for apt pinning. If he just wants to upgrade a few packages I can see no reason why he would not use apt pinning.
I may be wrong but I'm sure he does not want to wait a few months to get newer Gaim, Firefox, ... or compile it from sources.
If something goes wrong, Warty is preferred so downgrading should not be a problem.

---

### Post by ubuntu_demon on 2004-12-09
[QUOTE=p!=f]You really don't need expert skills for apt pinning. If he just wants to upgrade a few packages I can see no reason why he would not use apt pinning.
I may be wrong but I'm sure he does not want to wait a few months to get newer Gaim, Firefox, ... or compile it from sources.
If something goes wrong, Warty is preferred so downgrading should not be a problem.[/QUOTE]
 If he makes a mistake he could be ending up with a hoary installation.

I would like to reassure CacheMonet that all security updates that are made to gaim flow back to the warty version.  All packages in the main ubuntu repositorie are maintained with security updates they just don't introduce new features.

So if he isn't dependend on some new gaim feature I don't think it would be a disaster to wait a couple of months.

---

### Post by Hikaru79 on 2004-12-09
[QUOTE=demon666_nl]off topic :
Nice pics hikaru79. I've watched Hikaru no Go too.Now that I think of it I don't remember if I've seen "Hikaru no Go New Year's Special 2004". Downloading it now :D[/QUOTE] :D Yay! Another Hikaru no Go fan, didn't think there were too many around anymore =/ Do you also play Go for real? PM me if you do! ^__^

---

### Post by ubuntu_demon on 2004-12-09
I do play it occasionally. But since I don't play it very often I'm not very good.

---

### Post by regeya on 2004-12-10
[QUOTE=demon666_nl]If he makes a mistake he could be ending up with a hoary installation.

I would like to reassure CacheMonet that all security updates that are made to gaim flow back to the warty version.  All packages in the main ubuntu repositorie are maintained with security updates they just don't introduce new features.

So if he isn't dependend on some new gaim feature I don't think it would be a disaster to wait a couple of months.[/QUOTE]

That would have to be one BIG mistake, though I have to agree.

I've done a combination of backporting and apt-pinning.  I wouldn't recommend it for anyone, and I wouldn't have bothered had it not been for the fact that Warty was a first release.  What I've seen so far makes me think that Hoary will be > *.  :D

---

### Post by ubuntu_demon on 2004-12-10
[QUOTE=regeya]That would have to be one BIG mistake, though I have to agree.

I've done a combination of backporting and apt-pinning.  I wouldn't recommend it for anyone, and I wouldn't have bothered had it not been for the fact that Warty was a first release.  What I've seen so far makes me think that Hoary will be > *.  :D[/QUOTE]
 I also think hoary will rock. Let's make Ubuntu kick ass for the average-desktop-user and kick-ass for nerds at the same time.

---

