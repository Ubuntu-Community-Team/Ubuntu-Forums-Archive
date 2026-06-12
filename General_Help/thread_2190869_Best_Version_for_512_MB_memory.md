---
title: "Best Version for 512 MB memory"
date: 2013-11-29
forum: General Help
---

### Post by mavmin on 2013-11-29
I have a Toshiba laptop with only 512MB RAM.  User just wants it for Internet and Email.  WHich is the nest version to use for such an older machine? Thanks!

---

### Post by Frogs Hair on 2013-11-29
Lubuntu

---

### Post by mavmin on 2013-11-29
That was quick!  Thanks!!

---

### Post by Iowan on 2013-11-29
> **Frogs Hair said:**
> Lubuntu
+1  
I have a tower with similar specs 
...also primarily an internet machine
...also running Lubuntu.

---

### Post by 1clue on 2013-11-29
Lubuntu 12.04

---

### Post by mörgæs on 2013-11-29
> **1clue said:**
> Lubuntu 12.04

should never be recommended, as it is out of support and hence a security breach. 13.10 is supported and might even perform better.

You could try a [core install]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") if you want something even lighter.

---

### Post by 1clue on 2013-11-29
> **mörgæs said:**
> should never be recommended, as it is out of support and hence a security breach. 13.10 is supported and might even perform better.

You could try a [core install]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") if you want something even lighter.

How so?  It's LTS right?

---

### Post by mörgæs on 2013-11-29
No, as I wrote it's unsupported. There's no LTS for Lubuntu. 

Ubuntu has five years and Xubuntu three.

---

### Post by monkeybrain20122 on 2013-11-29
> **mörgæs said:**
> No, as I wrote it's unsupported. There's no LTS for Lubuntu. 

Ubuntu has five years and Xubuntu three.

But it uses the same repos as Ubuntu 12.04 so almost everything will be supported, the only things not supported would be LXDE specific things. Not sure how risky it is to run those.

---

### Post by mörgæs on 2013-11-29
It has been discussed many times. No matter if the risk is big or small it's not worth the experiment. 

If long time support is important [Bodhi Linux]("http://www.bodhilinux.com") is a better choice.

---

### Post by 1clue on 2013-11-29
> **mörgæs said:**
> No, as I wrote it's unsupported. There's no LTS for Lubuntu. 

Ubuntu has five years and Xubuntu three.

In that case I can't say I'd recommend anything Ubuntu-based.  Ubuntu Server 12.04?  Maybe use the 12.04 minimal install and maybe blackbox?

---

### Post by grier-devon on 2013-11-29
Wouldn't Xubuntu 32 bit Work fine? I am sure it would run on 512 MB. If no one agrees to that I know Linux Mint Debian Edition XFCE 32 Bit uses only like 196 MB of RAM so that would run just fine on your system.

---

### Post by craig10x on 2013-11-29
He should download an iso of xubuntu 13.10 and see how it runs on the live session ...probably will use even less ram then 12.04 did...

---

### Post by grier-devon on 2013-11-30
> **craig10x said:**
> He should download an iso of xubuntu 13.10 and see how it runs on the live session ...probably will use even less ram then 12.04 did...

Really? Well that would be nice. I know for me Ubuntu 12.04 used some where around 500 MB where as 13.10 is using 700 MB roughly. Though my Fan speeds don't seem to spin up as much so for me I am guessing 13.10 to be less cpu intense.

---

### Post by DuckHook on 2013-11-30
> **mörgæs said:**
> ...If long time support is important [Bodhi Linux]("http://www.bodhilinux.com") is a better choice.+1

@OP

By now, I'm sure you're screaming, "Too Much Information!"

In my opinion, mörgæs is spot on&#8213;within the Ubuntu family, *Lubuntu*. If willing to go outside, *Bodhi*. His recommendations are not based only on personal preference but on memory footprint. Here in KB are the memory footprints of the various installs--each a fresh default install running in a VM:

```
Ubuntu:  433148
Xubuntu: 262400
Lubuntu: 175932
Bodhi:   152164
```

If you are willing to go outside of the Ubuntu family altogether, then distros like Tiny, Damn Small, Slitaz, Vector, are lighter still. Some of them are only 40,000 KB. But there is a point where you start paying with functionality and crippled/obsolete apps.

In cases like yours, I used to recommend *Lubuntu*, but I am more and more gravitating to *Bodhi* these days, precisely for the same reasons that mörgæs raises: it is both lighter *and* LTS. That's a hard-to-beat combo.

**EDIT**

I always forget *CrunchBang*, another light distro that can still actually *do* things. It's not based on *Ubuntu*, but *Debian*, which is pretty close. Memory footprint of fresh default install is 186020 KB which puts it slightly higher than *Lubuntu*, but not enough to matter. It doesn't have an LTS, but *Debian* is so conservative that you get lengthy support cycles anyway.

---

### Post by craig10x on 2013-11-30
@grier-devon: well, i haven't run it but just making that assumption...i have seen ram usage go down on main ubuntu going from 12.04 through 13.10 and unity generally uses more ram then xubuntu would (since it doesn't have it) and it has much newer kernels so the possibility exists...of course, only one way for him to find out...run the live iso (of course a hard installed one should be less but he should get SOME idea from that)...

---

### Post by sudodus on 2013-11-30
Have a look at these threads

[Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")
and[URL="http://ubuntuforums.org/showthread.php?t=1582027"]
Light Linux Distributions - Hardware Testing (RAM)[/URL]

---

