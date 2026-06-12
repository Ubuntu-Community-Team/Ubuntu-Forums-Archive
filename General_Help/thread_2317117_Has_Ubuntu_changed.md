---
title: "Has Ubuntu changed?"
date: 2016-03-13
forum: General Help
---

### Post by gari3 on 2016-03-13
I recently installed Ubuntu 14 LTS on an old PC for running a projector for movie watching etc
The plan was to play DVDs via vlc, and stuff like Netflix, iPlayer and Amazon Prime on Firefox.
I had more or less this set up on another old PC several years ago and it all worked well.
This time not.so much. VLC wouldn't even read the DVDs, when I tried Prime it said it couldn't stream, I assume because of the lack.of Silverlight. Netflix also wouldn't stream as it needed to go through Chrome?
You've probably guessed I am not really a software guy! But I had no issues the last time I did this. I am not entirely useless though, just clueless with the command line, sorry.
So has something changed? Or am I just doing it wrong? It's been a while and I can't remember most of how I got the set up sorted TBH.
I find it hard to believe that any modern OS would be incapable of any form of playing/streaming media content for an entertainment set up. Help.....

---

### Post by montag dp on 2016-03-13
I don't know about the VLC issue, but as far as I know you need Chrome to play Netflix and Amazon Prime.

---

### Post by oldos2er on 2016-03-13
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Installing_libdvdcss](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Installing_libdvdcss)

This hasn't changed, btw. It is illegal for Canonical to distribute libdvdcss2 with the Ubuntu ISO in some countries. See (USA-centric) [http://www.howtogeek.com/138969/why-watching-dvds-on-linux-is-illegal-in-the-usa/](http://www.howtogeek.com/138969/why-watching-dvds-on-linux-is-illegal-in-the-usa/) for more info.

---

### Post by deadflowr on 2016-03-13
You've never been able to do any of that out of the box on Ubuntu.
But...
Here are several things you'll need:
First I'd install the restricted-extras package to install the extra (and non-free) codecs such as flash.
```
sudo apt-get install ubuntu-restricted-extras
```
[Beware that you will need to accept a EULA, to do so press the tab key and the arrow keys on your keyboard to accept the EULA]

You might also look into setting up your dvd plavyback by following the advice from here:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Next, you can try using a specialize plugin system designed to run windows plugins in linux firefox.
It's called pipelight, and you can read about how to install and configure it here:
[http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html)

And as an aside, Ubuntu used to be able to play protected flash (Firefox only; chrome's flash version does not support this on Linux), if you install a package called hal.
But, alas, hal has been deprecated and removed from the Ubuntu repositories.
Luckily, a brave user has created a ppa for this, which can be easily installed by running
```
sudo add-apt-repository ppa:mjblenner/ppa-hal 
```
then run an update
```
sudo apt-get update
```
then install hal
```
sudo apt-get install hal
```

But if you have pipelight properly installed, hal probably isn't needed.

Hope it helps,
or makes sense

Edit: ninja'd, not ninja'd...

---

