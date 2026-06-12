---
title: "Free Java plugin for Firefox?"
date: 2007-10-22
forum: General Help
---

### Post by jordon on 2007-10-22
Since I've upgraded from Feisty to Gutsy, my Java plugin seems to have gone missing (maybe because I disabled the multiverse repository before upgrading?). Is there a *free* implementation of Java available as a plugin for Firefox on Gutsy?

Possibly relevant information -- I have the following java-related packages installed: java-common, libhsqldb-java, libjaxp1.3-java, libjline-java, libservlet2.3-java, libservlet2.4-java, libxalan2-java, libxerces2-java, openoffice.org-java-common, sun-java6-bin, sun-java6-jre.

---

### Post by ayoli on 2007-10-22
I guess you need this one:
```
sudo apt-get install sun-java6-plugin
```

---

### Post by jordon on 2007-10-22
> **ayoli said:**
> I guess you need this one:
```
sudo apt-get install sun-java6-plugin
```

sun-java6-plugin is apparently in the multiverse repository. I would prefer to use free software. Is there an equivalent package in the main or universe repository?

---

### Post by ayoli on 2007-10-22
> **jordon said:**
> sun-java6-plugin is apparently in the multiverse repository. I would prefer to use free software. Is there an equivalent package in the main or universe repository?

multiverse repositoey doesn't mean not free, this is a only a commmunity repository not officialy supported.

---

### Post by jordon on 2007-10-22
> **ayoli said:**
> multiverse repositoey doesn't mean not free, this is a only a commmunity repository not officialy supported.

I believe that's what the universe repository is for. I'm under the impression that the repositories are like this:

Free and supported: main
Free and not supported: universe
Non-free and supported: restricted
Non-free and not supported: multiverse

---

### Post by ayoli on 2007-10-23
Pasted from original sources.list:
> ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
universe and multiverse are not entirely supported, but universe can have updates from the security team.
non free software are in restricted, non-free and partner repositories only.

---

### Post by FredB on 2007-10-23
You can try Java 7, alias Iced Tea for now. It is alpha quality but a very good one alpha quality.

There is an old version available in universe repository, but you can find a newer one packaged by an ubuntu coder, Doko.

If you want to test it, add this to your  /etc/apt/sources.list/

# iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/)  gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/

Hope I helped ;)

---

