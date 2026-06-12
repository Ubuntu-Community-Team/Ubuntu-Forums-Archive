---
title: "how do i speed things up on older machine?"
date: 2012-11-02
forum: General Help
---

### Post by zander1013 on 2012-11-02
hi,

i am using 12.04 lts on an older netbook.  it's beginning to become sluggish under the load of the newer releases.

is there anyway i can configure things for a speed up?

thank you.

---

### Post by JRV on 2012-11-02
I would try Lubuntu.  I found it to be much faster, even when compared to Unity2d.

---

### Post by snowpine on 2012-11-02
There are many "older netbooks" and we aren't mind readers; which one do you have? :)

CPU, RAM, video card, hard drive/SSD.... all of these factors affect performance but I don't know what you have.

---

### Post by kanikilu on 2012-11-02
Phoronix found 12.04 to be slow/sluggish on older hardware as well:

[http://www.phoronix.com/scan.php?page=news_item&px=MTA3ODQ](http://www.phoronix.com/scan.php?page=news_item&px=MTA3ODQ)

If you have really old hardware, it may be time to try a distro designed specifically to be lightweight:

[http://www.expertreviews.co.uk/general/1289197/top-5-lightweight-linux-distros-for-older-pcs](http://www.expertreviews.co.uk/general/1289197/top-5-lightweight-linux-distros-for-older-pcs)

I'd personally try Lubuntu to stay in the "Ubuntu family", and then if necessary, move on to CrunchBang, which I've tried in the past on an ASUS EeePC701, and was impressed with...

---

### Post by ajgreeny on 2012-11-02
If you're prepared to look at, and more importantly, learn to use a completely different style of DE (Enlightenment) have a look at, and play with Bodhi for a while.

It is screamingly fast and once you get used to it, it's extremely good.  It also uses the Ubuntu repos, and the same system of package management (sudo, apt-get, synaptic, etc).

Otherwise I also loke Lubuntu very much and use it on my netbook, an MSI U100, rebadged with another makers name. Atom 1.6GH cpu, atheros wireless, 1GB ram, intel graphics.

It runs unity, just, but is too slow to be worth using with that DE.

---

### Post by Rezliw on 2012-11-02
Tried a bunch of liteweight versions on my Asus 2Gb surf and the winner was Puppeee (Puppy) installed entirely on the 2Gb SSD and also booting Easey Peasey from a 4Gb class 10 SD card works well too.

---

### Post by BBQdave on 2012-11-02
> **zander1013 said:**
> ...is there anyway i can configure things for a speed up?

Max out your ram and give Xubuntu a try :)

---

### Post by Lyfang on 2012-11-03
**@JRV:** Great advise! I use Lubuntu 12.10. **@zander1013:** If you try Lubuntu I would advise to upgrade to Lubuntu 12.10 since Lubuntu 12.04 is not LTS anyway and instead of Abiword and Gnumeric I use LibreOffice. But you can in fact try to install the Lubuntu Desktop environment with a minimal installation, search for the *lubuntu-core* package in Synaptic.

---

### Post by black veils on 2012-11-04
install lubuntu desktop.

[adjust swappiness]("http://ubuntuforums.org/showpost.php?p=12261874&postcount=2")  read from the line "then do this tweak"


use lighter application alternatives, like those included in the lubuntu desktop.

---

### Post by mardybear on 2012-11-04
I run old systems too...

I would recommend utilizing the Openbox window manager before all the hassle of installing another distribution. It doesn't require a windows manager and runs very lean. Should be avaiable in your existing repositories...

Many of these tweaks will still apply:
[http://kmandla.wordpress.com/projects/set-up-ubuntu-for-speed/](http://kmandla.wordpress.com/projects/set-up-ubuntu-for-speed/)

mardybear

---

### Post by Manhi40 on 2012-11-05
Not sure if this would help much, but try using bleach bit
```
sudo apt-get install bleachbit
```

---

### Post by |{urse on 2012-11-05
Install LXDE, (that's where lubuntu gets it's L) I'm running it on a very very slow laptop (celeron m with 768mb ram) and it's 'faster' (more responsive) than my nice laptop (with 7, an i5 and 4gb ram and an ssd). ;)

Now that, was a punctuation nightmare, but give LXDE a whirl.

---

