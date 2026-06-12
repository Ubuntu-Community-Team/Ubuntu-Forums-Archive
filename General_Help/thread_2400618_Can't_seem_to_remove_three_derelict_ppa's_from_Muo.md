---
title: "Can't seem to remove three derelict ppa's from Muon Package Manager."
date: 2018-09-07
forum: General Help
---

### Post by Butthead on 2018-09-07
Hi,

I did the online upgrade from Xenial 16.04 to Bionic 18.04 and still have two (well three now) leftover derelict PPA's that I can't seem to delete now still showing up in Muon's repository index.

Launchpad PPA for Graphics Drivers Team
Lauchpad PPA for Wine Team
And Lauchpad PPA for xorg crack pushers (that somehow got installed itself when I tried erasing them using a command I found on the Web somewhere). :mad:

They show up under Software Sources in Muon Authentication, but highlighting them and clicking the "remove" key in there does nothing but bring up a "The key you selected could not be removed. Please report this as a bug." error box.

I don't think they actually do anything having them listed in there, but it just looks sloppy to me. :o  

I can't find any references to these PPA's in any of the sources.list I examined, so I'm just wondering if Muon stores them in some kind of external sources.list it hides in one of it's directoriessomewhere.

I even tried purging Muon and reinstalling it, but they still come up.  Does anyone in the forum here have any idea on how to go about fixing this? :confused:

Would really appreciate any help possibly fixing this, (or I guess I just have to get used to them). :(

---

### Post by Yellow Pasque on 2018-09-07
It sounds like the keys remain rather than the PPA's themselves (unless you did not look in /etc/apt/sources.list.d/ )
[https://askubuntu.com/questions/107177/how-can-i-remove-gpg-key-that-i-added-using-apt-key-add](https://askubuntu.com/questions/107177/how-can-i-remove-gpg-key-that-i-added-using-apt-key-add)

---

### Post by Butthead on 2018-09-08
Thank you very much, Temüjin, you're a real lifesaver!   That seems to have put things in order again! :guitar:

I [COLOR="#FF0000"]REALLY [/COLOR]do appreciate it!  Thank you so much again!

---

