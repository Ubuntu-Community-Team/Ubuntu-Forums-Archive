---
title: "A Change in Synaptic?"
date: 2016-09-19
forum: General Help
---

### Post by BlueAZ on 2016-09-19
Hello,
I love Ubuntu and successfully did a clean install of 16.04 -- yay!  Now I receive package updates for Linux version 4.4.0-xxx.  Great!  I install them and go forward.

Except...  I've always used Synaptic to cull out older versions, as I had start-up problems when I didn't.  I was hoping 16.04 would do this housekeeping by itself, or at least give me some option to only keep the two most recent.  But no, the versions continue to pile up.  Today's update was to 4.4.0-38, so I went in Synaptic to see what other versions exist in my system.  Usually, I would click on 'Status', then 'Installed', and then search for 'linux-'...   But today, Synaptic doesn't work as it always did.

First, there is no open Search field at the top.  One has to click on 'Search'.  So I was in 'Status'/'Installed' when I clicked on 'Search'.  I filled in 'linux-' and clicked search.  What I got was not the limited list from 'Installed', but an endless list from 'ALL'.  I tried twice with the same result, so this is definitely a change in Synaptic.  By using some creative highlighting, I was able to find the previous installed versions, ...36 and ...34, and removed the ...34's.  So I got it done.  Just more time and effort.

Was this a considered, intentional change to Synaptic Package Manager?  If so, I found it more useful BEFORE!  If anyone has a quick easy way to clean out old linux versions, or reset Synaptic to its old self, please let me know!

Many Thanks!

---

### Post by westie457 on 2016-09-19
The other way still works.

While in Status/Installed highlight any package in the list and start typing the name of a package. All those with the same letters in are found.

This works in all sections of Synaptic.

---

### Post by #&amp;thj^% on 2016-09-19
They felt it was buggy...but others here use this:
```
sudo apt-get install apt-xapian-index
```
then force a rebuild of the index
```
sudo update-apt-xapian-index -vf
```
That should get synaptic the way you were used to.
Ninje'd by  westie457 :)

---

### Post by jeremy31 on 2016-09-19
Strange as Synaptic Package Manager on the laptop I updated to 16.04 from 15.10 still has the search box but my clean installs don't and it shows Synaptic being the latest version

---

### Post by #&amp;thj^% on 2016-09-19
> **jeremy31 said:**
> Strange as Synaptic Package Manager on the laptop I updated to 16.04 from 15.10 still has the search box but my clean installs don't and it shows Synaptic being the latest version

Yup same here upgrading leaves it in place...while a fresh install omits it...
This was very early in Development that we discovered old bugs coming back to haunt us: [https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/655831](https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/655831)
[http://osdir.com/ml/ubuntu-bugs/2016-09/msg07313.html](http://osdir.com/ml/ubuntu-bugs/2016-09/msg07313.html)
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=793681](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=793681)
I could list more but I won't..:)

---

### Post by BlueAZ on 2016-09-20
> **1fallen said:**
> They felt it was buggy...but others here use this:
```
sudo apt-get install apt-xapian-index
```
then force a rebuild of the index
```
sudo update-apt-xapian-index -vf
```
That should get synaptic the way you were used to.
Ninje'd by  westie457 :)

Thanks so much westie457!  I used this method and it worked perfectly!
I'll marked this solved.
Thanks again,  Blue

---

