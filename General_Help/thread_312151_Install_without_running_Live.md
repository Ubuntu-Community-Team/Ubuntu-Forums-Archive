---
title: "Install without running Live"
date: 2006-12-03
forum: General Help
---

### Post by dickohead on 2006-12-03
Hey Guys,

I have been trying to find an answer to this problem for a while, but continually come up empty handed.

How do I install Ubuntu from the boot CD, without having to run the Live-CD first?

I want to just install the system without waiting for over 30 minutes for the system to boot before I can then choose to install.

It seems a very counter-productive method of installing Ubuntu to me, given that not every-one is new to Ubuntu nor Linux I thought the old method of installation was perfect - one Disc to try it, another to install it.

And since I'm whinging, why is it so hard to do a succesful update, especially given that Ubuntu releases MAJOR system updates every 6 months, whereas others who Release updates yearly, have upgrading down-pat?

/end rant.

---

### Post by bmathis on 2006-12-03
download the alternate cd... it installs in text mode

---

### Post by atoponce on 2006-12-03
> **dickohead said:**
> Hey Guys,

I have been trying to find an answer to this problem for a while, but continually come up empty handed.

How do I install Ubuntu from the boot CD, without having to run the Live-CD first?

I want to just install the system without waiting for over 30 minutes for the system to boot before I can then choose to install.

It seems a very counter-productive method of installing Ubuntu to me, given that not every-one is new to Ubuntu nor Linux I thought the old method of installation was perfect - one Disc to try it, another to install it.

And since I'm whinging, why is it so hard to do a succesful update, especially given that Ubuntu releases MAJOR system updates every 6 months, whereas others who Release updates yearly, have upgrading down-pat?

/end rant.

Well..

1) The method of installation that you are looking for is the Alternate Install CD.  It's not live, and is text-based like the previous versions.  Or, you could download and install the Server CD, then:

```
sudo aptitude install ubuntu-desktop
```

2) Maybe you could be more specific here.  I find the update system in Ubuntu flawless.

---

### Post by scrooge_74 on 2006-12-03
try booting in safe mode it worked for me last night,  (a friend needed to use ubuntu but things took to long on normal boot from live cd), things then were very fast as with my every day laptop

---

