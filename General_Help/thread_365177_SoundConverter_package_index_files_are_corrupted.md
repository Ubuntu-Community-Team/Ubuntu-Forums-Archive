---
title: "SoundConverter package index files are corrupted"
date: 2007-02-19
forum: General Help
---

### Post by webjames on 2007-02-19
Hi, tried installing SoundConverter to convert some audio:

```

sudo apt-get install soundconverter

```

however i get this error:

> The following NEW packages will be installed:
  soundconverter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
E: The package index files are corrupted. No Filename: field for package soundconverter.


anyone else getting this message? i'm sure i've had this installed before!

Thanks

James

---

### Post by brendand on 2008-07-14
James,

I got a similar message...

> Writing extended state information... Error!
E: The package index files are corrupted. No Filename: field for package openssh-blacklist.
E: Couldn't lock list directory..are you root?

I fixed it.  I think it was the following which did it;

sudo rm /var/lib/apt/lists/*
sudo aptitude update
sudo aptitude install openssh-server

Obviously you want to replace the "openssh-server" with "soundconverter"...

HTH.

Brendan

---

