---
title: "Apparently outdated libstdc++6 version? How to fix?"
date: 2017-11-18
forum: General Help
---

### Post by llbrand on 2017-11-18
I tried to downgrade to Firefox 56 (different story, see [here]("https://ubuntuforums.org/showthread.php?t=2377844")) and got the following error message:

```

dpkg: dependency problems prevent configuration of firefox:
 firefox depends on libstdc++6 (>= 6); however:
  Version of libstdc++6:amd64 on system is 5.4.0-6ubuntu1~16.04.5.

```
Checked the Software Center and apparently my current package was installed back in 2014 and hasn't been updated since?

That does seem a bit out of date.

sudo apt-get update doesn't seem to notice anything wrong.

Now, according to many a google result, libstdc is super important and shouldn't be messed with.

So should I upgrade it? if yes, how to do so safely?

---

### Post by vasa1 on 2017-11-18
On my system,```
$ apt policy libstdc* | grep -Ei "Installed: [0-9]"

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

  Installed: 5.4.0-6ubuntu1~16.04.5
$
```>  Now, according to many a google result, libstdc is super important and shouldn't be messed with.That's for sure. So, in my opinion, there's no need to poke the bear unless you want to learn by breaking!

---

### Post by Holger_Gehrke on 2017-11-18
Looks to me like the firefox package you have is for a newer version of ubuntu. Unless you're compulsive about cleaning your system (or have set your system to be compulsive about cleaning itself) you might find packages for firefox going back a few versions that you had installed in the apt package cache in /var/cache/apt/archives/

Holger

---

### Post by llbrand on 2017-11-18
Finally managed to install older Firefox Version 54.

Thanks anway!

---

