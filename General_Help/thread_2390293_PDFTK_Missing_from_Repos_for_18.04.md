---
title: "PDFTK Missing from Repos for 18.04?"
date: 2018-04-27
forum: General Help
---

### Post by linux4me on 2018-04-27
I've been using PDFTK to work with PDFs in Ubuntu for years, including in 17.10, but it is currently [missing from the repos for 18.04]("https://packages.ubuntu.com/search?keywords=pdftk&searchon=names&suite=bionic&section=all"). I've searched, but haven't been able to find out if it's been dropped, going to be included but just hasn't been yet, or what the story about it is. 

Does anyone know, or know where I should be looking?

```

inxi -r
Repos:     Active apt sources in file: /etc/apt/sources.list
           deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
           deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
           deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
           deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
           deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
           deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
           deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
           deb http://security.ubuntu.com/ubuntu bionic-security main restricted
           deb http://security.ubuntu.com/ubuntu bionic-security universe
           deb http://security.ubuntu.com/ubuntu bionic-security multiverse

```

---

### Post by kostkon on 2018-04-27
Looks like [it's been dropped]("https://bugs.launchpad.net/ubuntu/+source/pdftk/+bug/1757314").

---

### Post by linux4me on 2018-04-27
I can't tell from that if it has been dropped, or just temporarily removed while a fix was released, but it's certainly not in the repo now.

---

### Post by deadflowr on 2018-04-27
> **linux4me said:**
> I can't tell from that if it has been dropped, or just temporarily removed while a fix was released, but it's certainly not in the repo now.

The Fix Released tag means it's gone and won't reappear.
at least it will never reappear in 18.04.
Maybe they'll fix it in later releases.

---

### Post by linux4me on 2018-04-27
Oh! Okay, got it. Thanks.

---

### Post by SeijiSensei on 2018-04-27
I got the version built for Yakkety (16.10) to install on my 18.04 machine a few weeks ago.  I don't recall if I had to do any extra massaging to make this work.  I think I just downloaded the .deb ([amd64 version](https://launchpad.net/ubuntu/+source/pdftk/2.02-4build1/+build/10581759/+files/pdftk_2.02-4build1_amd64.deb)) and installed it with dpkg.

[https://launchpad.net/ubuntu/+source/pdftk/2.02-4build1/+build/10581759](https://launchpad.net/ubuntu/+source/pdftk/2.02-4build1/+build/10581759)

---

### Post by linux4me on 2018-04-27
> **SeijiSensei said:**
> I got the version built for Yakkety (16.10) to install on my 18.04 machine a few weeks ago.  I don't recall if I had to do any extra massaging to make this work.  I think I just downloaded the .deb ([amd64 version](https://launchpad.net/ubuntu/+source/pdftk/2.02-4build1/+build/10581759/+files/pdftk_2.02-4build1_amd64.deb)) and installed it with dpkg.

[https://launchpad.net/ubuntu/+source/pdftk/2.02-4build1/+build/10581759](https://launchpad.net/ubuntu/+source/pdftk/2.02-4build1/+build/10581759)

That's interesting. The bug report made me think there was a missing dependency in Bionic.

---

### Post by SeijiSensei on 2018-04-27
I might have needed to track down a package or two.  I'm sorry I can't remember more details.

I know it's installed on this machine and working.  I used it just this morning.

```

$ dpkg -s pdftk
Package: pdftk
Status: install ok installed
Priority: optional
Section: text
Installed-Size: 4030
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
**Version: 2.02-4build1**
Depends: libc6 (>= 2.14), libgcc1 (>= 1:3.0), libgcj17 (>= 5), libstdc++6 (>= 5.2)

```

I think the issue is libgcj17.  I have the version 6.4.0-8ubuntu1 from Artful installed.  I must have gotten it here: [https://packages.ubuntu.com/search?keywords=libgcj17](https://packages.ubuntu.com/search?keywords=libgcj17)

---

### Post by linux4me on 2018-04-27
Not a problem! You've let me know it's possible. I'm going to give it a try if I can't get pdfshuffler or pdfmod, which are still in the Bionic repos, to meet my needs.

---

### Post by #&amp;thj^% on 2018-04-27
> **SeijiSensei said:**
> I might have needed to track down a package or two.  I'm sorry I can't remember more details.

I know it's installed on this machine and working.  I used it just this morning.

```

$ dpkg -s pdftk
Package: pdftk
Status: install ok installed
Priority: optional
Section: text
Installed-Size: 4030
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
**Version: 2.02-4build1**
Depends: libc6 (>= 2.14), libgcc1 (>= 1:3.0), libgcj17 (>= 5), libstdc++6 (>= 5.2)

```

I think the issue is libgcj17.  I have the version 6.4.0-8ubuntu1 from Artful installed.  I must have gotten it here: [https://packages.ubuntu.com/search?keywords=libgcj17](https://packages.ubuntu.com/search?keywords=libgcj17)

+1 I needed these for deps.
**libgcj17-dev And gcc-libs** Found here: [https://packages.ubuntu.com/artful/libgcj17-dev](https://packages.ubuntu.com/artful/libgcj17-dev)

---

### Post by linux4me on 2018-04-28
> **1fallen said:**
> +1 I needed these for deps.
**libgcj17-dev And gcc-libs** Found here: [https://packages.ubuntu.com/artful/libgcj17-dev](https://packages.ubuntu.com/artful/libgcj17-dev)

Thanks!

---

### Post by monkeybrain20122 on 2018-04-28
Maybe pdfshuffler can do the same things?

---

### Post by Claus7 on 2018-05-07
Hello,

1)
> **monkeybrain20122 said:**
> Maybe pdfshuffler can do the same things?

From my experience I was able to see that it cannot be used from terminal, yet from graphical interface. 

2) qpdf can be an alternative if merging files using the command:
```
qpdf --empty --pages input1.pdf 1-z input2.pdf 1-z -- output.pdf
```

yet pdftk I think is more elegant:
```
pdftk input1.pdf input2.pdf cat output output.pdf
```

3) recapitulation of the intallation process of pdftk to 18.04 (in that order):
```
sudo dpkg -i gcc-6-base_6.4.0-8ubuntu1_amd64.deb
sudo dpkg -i libgcj-common_6.4-3ubuntu1_all.deb
sudo dpkg -i libgcj17_6.4.0-8ubuntu1_amd64.deb
sudo dpkg -i pdftk_2.02-4build1_amd64.deb
```

where the first downloaded from:
[https://packages.ubuntu.com/artful/libgcj17-dev](https://packages.ubuntu.com/artful/libgcj17-dev)
the second one from:
[https://packages.ubuntu.com/artful/libgcj-common](https://packages.ubuntu.com/artful/libgcj-common)
the third one from:[EDIT]
[https://packages.ubuntu.com/artful/libgcj17](https://packages.ubuntu.com/artful/libgcj17)
and the last one from:
[https://launchpad.net/ubuntu/+source/pdftk/2.02-4build1/+build/10581759](https://launchpad.net/ubuntu/+source/pdftk/2.02-4build1/+build/10581759)

Thank you,
Regards!

---

### Post by agopaul on 2018-06-05
> **Claus7 said:**
> 
where the first and the third one downloaded from:
[https://packages.ubuntu.com/artful/libgcj17-dev](https://packages.ubuntu.com/artful/libgcj17-dev)
the second one from:
[https://packages.ubuntu.com/artful/libgcj-common](https://packages.ubuntu.com/artful/libgcj-common)
and the last one from:
[https://launchpad.net/ubuntu/+source/pdftk/2.02-4build1/+build/10581759](https://launchpad.net/ubuntu/+source/pdftk/2.02-4build1/+build/10581759)


Thanks, this works like a charm.

One small correction though: the correct link for the third package (libgcj17) is: [https://packages.ubuntu.com/artful/libgcj17](https://packages.ubuntu.com/artful/libgcj17)

---

### Post by Claus7 on 2018-06-08
Hello,
> **agopaul said:**
> Thanks, this works like a charm.

One small correction though: the correct link for the third package (libgcj17) is: [https://packages.ubuntu.com/artful/libgcj17](https://packages.ubuntu.com/artful/libgcj17)

thank you *agopaul*, you are correct! I edited my post to include the correct information.

Regards!

---

### Post by Claus7 on 2018-09-09
Hello,

just to add that recently I came across this ppa, which avoids all these kind of installations mentioned thus far:
[http://ppa.launchpad.net/malteworld/ppa/ubuntu](http://ppa.launchpad.net/malteworld/ppa/ubuntu)

Regards!

---

### Post by driehuis on 2019-08-29
Actually, that PPA has not been updated for a year. The current version of that package for Disco (19.04) works out of the box on Bionic (18.04LTS). You can download the package from [https://packages.ubuntu.com/disco/all/pdftk-java/download](https://packages.ubuntu.com/disco/all/pdftk-java/download), and install it with:

```
sudo dpkg -i /tmp/pdftk-java_3.0.2-2_all.deb
sudo apt-get install -f
```

You would still not get updates, but at least it's more recent than 3.0.0.

I hold out some hope that pdftk-java will be released for bionic. It's a painless backport, the version from disco just works, so it should just drop in.

There is also a version out there that can be installed as a snap, but it cannot read or write files to /tmp, so it does not meet my requirements. That said, if you want that one, just use
```
snap install pdftk
```

---

