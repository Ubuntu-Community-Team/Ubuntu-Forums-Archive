---
title: "Download package from apt-get with ALL required libraries"
date: 2007-05-19
forum: General Help
---

### Post by loathsome on 2007-05-19
Hi there,

How can I download for example the supertux deb-package from apt-get PLUS all the libraries *even though I already have them?*

If I for example run ```
sudo apt-get install -d supertux
```, the package manager will download all required files into /var/cache/apt/archives **but** it will not download the libraries I need for supertux if I already have them.

I need this because a friend of mine wants some software, and he doesn't have an internet connection - it's way too much work for me to manually get [each and every library](http://packages.debian.org/stable/games/supertux) required myself.

Thanks a lot for help!

---

### Post by kaamos on 2007-05-19
You could find this useful -> [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by loathsome on 2007-05-19
Thanks, that looks **great!**

Though, I'd prefer if there was any simpler way, like ```
sudo apt-get install -all supertux
``` for example.

---

### Post by cborga1985 on 2007-05-19
you would be better off to create a [LocalAptGetRepository]("https://help.ubuntu.com/community/LocalAptGetRepository") with all the software he wants in it.

more links: [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=Repository&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=Repository&titlesearch=Titles)

---

### Post by aysiu on 2007-05-19
What I do in situations like those is use a live CD to see what packages need to be downloaded.

You can get the packages here:
[http://packages.ubuntu.com/feisty/games/supertux](http://packages.ubuntu.com/feisty/games/supertux)

The ones you actually need to install are these: ```
libopenal0a libphysfs-1.0-0 libvorbisfile3 supertux supertux-data
```

---

### Post by cborga1985 on 2007-05-19
> **aysiu said:**
> What I do in situations like those is use a live CD to see what packages need to be downloaded.

You can get the packages here:
[http://packages.ubuntu.com/feisty/games/supertux](http://packages.ubuntu.com/feisty/games/supertux)

The ones you actually need to install are these: ```
libopenal0a libphysfs-1.0-0 libvorbisfile3 supertux supertux-data
```

that would work also but if you have multiple things i would make a Local Apt Repository

---

### Post by loathsome on 2007-05-19
> **aysiu said:**
> What I do in situations like those is use a live CD to see what packages need to be downloaded.

You can get the packages here:
[http://packages.ubuntu.com/feisty/games/supertux](http://packages.ubuntu.com/feisty/games/supertux)

The ones you actually need to install are these: ```
libopenal0a libphysfs-1.0-0 libvorbisfile3 supertux supertux-data
```

Yes, a LiveCD would work, but that's also .. too much work for me :KS

About the aptoncd; That didn't do anything good, actually. It would just burn all the cache files from /var/cache/apt/archives, which I regularly run through apt-get clean anyway.

---

### Post by aysiu on 2007-05-19
> **loathsome said:**
> Yes, a LiveCD would work, but that's also .. too much work for me :KS Then just pay attention to the second part of my post.

---

### Post by loathsome on 2007-05-19
But there's listed a lot more packages [here](http://packages.ubuntu.com/feisty/games/supertux) than you're saying that I need.

---

### Post by aysiu on 2007-05-19
> **loathsome said:**
> But there's listed a lot more packages [here](http://packages.ubuntu.com/feisty/games/supertux) than you're saying that I need.
Yes, because some packages will already be installed.

---

### Post by loathsome on 2007-05-19
Aha, okay.

So .. how will one know what packages that already are installed?

---

### Post by aysiu on 2007-05-19
In general? Or in this specific case?

In general, as I said before, you can use the live CD to see what additional packages need to be downloaded.

In this specific case, I didn't have Supertux installed (in fact, I have very little at all installed--I don't even have *ubuntu-desktop* installed), so I just did ```
sudo apt-get install supertux
``` to see what new packages would be installed.

---

### Post by loathsome on 2007-05-19
Great, then - thanks a lot for your help. I guess I'll just use the LiveCD (I might even boot it up in vmware or something :-P) for future packages.

---

