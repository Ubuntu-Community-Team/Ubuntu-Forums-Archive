---
title: "How to install backup( which was copied from /var/cache/apt/archives )?"
date: 2013-05-04
forum: General Help
---

### Post by Ashfaqur Rahman on 2013-05-04
I have re-installed Ubuntu before that I created a backup copy of /var/cache/apt/archives derectory.
Now I have copied all files to /var/cache/apt/archives from my backup folder to get all my necessary softs in my newly installed ubuntu.
But I cant understand how to install them.

---

### Post by mcduck on 2013-05-05
Open a terminal, move to the directory where you put all the .deb packages, and use dpkg to install them:
```

sudo dpkg -i *.deb
```

---

### Post by Ashfaqur Rahman on 2013-05-05
I haven't tried
```

sudo dpkg -i *.deb

```

But I tried in another way.I downloaded synaptic pakage manager.And add my backup files or pakages there.It installed them automatically.
Though It installed all files I didn't find all programs!! Its clearly seen that I have got back all(maybe) my system updates as when I installed Ubuntu 2nd time it showed 300+ updates but after this operation now its showing only 18 updates. Also found only one program till now (I installed chess in previous Ubuntu and after this I found that).But could not find most of my programs like shutter, smplayer, chrome etc.

Ok now I will try dpkg from /var/cache/apt/archives .But the question is will it cause any problem? as I have already installed programs with synaptic.

---

### Post by mcduck on 2013-05-05
doesn't make any difference, dpkg, Synaptic Package Manager, apt-get, and so on are all just different interfaces for the very same package management system. Doesn't matter which one you use, they all share the same package information

Anyway, assuming you have never ran "apt-get clean" or emptied the package manager cache by some other means, and that you had installed all your application using the package manager in the first place, reinstalling everything from /var/cache/apt/archives should have restored all your programs. HAve you tried logging out and back again after you reinstalled them? Which desktop environment you are using?

---

### Post by Ashfaqur Rahman on 2013-05-08
> **mcduck said:**
> Have you tried logging out and back again after you reinstalled them?

Cant understand what you meant.Please explain.

No I haven't ever run apt-get update.My desktop environment is Unity (Ubuntu 12.10)

---

