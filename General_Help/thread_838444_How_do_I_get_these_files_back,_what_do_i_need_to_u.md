---
title: "How do I get these files back, what do i need to uninstall/re-install"
date: 2008-06-23
forum: General Help
---

### Post by boyd98 on 2008-06-23
Followed instruction for my tuner card, one of the steps i followed was

 sudo rm -rf /lib/modules/`uname -r`/ubuntu/media/cx88

sudo rm -rf /lib/modules/`uname -r`/ubuntu/media/saa7134

sudo depmod -a
-------------

I have no sound, and i think the above is the reason.

I checked after that and /proc/asound/cards doesnt have my tuner card listed anymore


Any help is appreciated- this tuner card is my only issue

---

### Post by VMC on 2008-06-23
I don't know what a tuner card is, but regarding the sound, have you checked
System > Preferences > Sound
Then do the "test" and see if it recognizes your sound card.

---

### Post by jpryor68 on 2008-06-23
> **boyd98 said:**
> Followed instruction for my tuner card, one of the steps i followed was

 sudo rm -rf /lib/modules/`uname -r`/ubuntu/media/cx88

sudo rm -rf /lib/modules/`uname -r`/ubuntu/media/saa7134


to get those files back, do this:

```

sudo apt-get install linux-ubuntu-modules-$(uname -r)

```

---

### Post by chrisccoulson on 2008-06-23
Out of interest, where did you get these instructions from?

---

### Post by jpryor68 on 2008-06-23
> **chrisccoulson said:**
> Out of interest, where did you get these instructions from?

```
dpkg -S /dir/file
```

will report what package installed a given file. So on my own machine, I typed:

```
dpkg -S /lib/modules/*/ubuntu/media/saa7134/*
dpkg -S /lib/modules/*/ubuntu/media/cx88/*

```
which reported that the files in question came from packages like linux-ubuntu-modules-2.6.24-19-generic. I don't know what kernel version the original poster is using, but

```
uname -r

```
will report the "2.6.24-19-generic" part. Hence my instructions:

```
sudo apt-get install linux-ubuntu-modules-$(uname -r)

```

Hope that helps.

---

### Post by jpryor68 on 2008-06-23
> **jpryor68 said:**
> 

Hence my instructions:

```
sudo apt-get install linux-ubuntu-modules-$(uname-r)

```

Hope that helps.

Whoops...somehow lost a space between uname and -r. That should be:

```
sudo apt-get install linux-ubuntu-modules-$(uname -r)

```

Earlier posts have been corrected.

---

### Post by chrisccoulson on 2008-06-24
Thanks jpryor68, but my question was directed at the original poster. I was wondering what instructions he followed which told him to go and delete files out of /lib/modules

---

