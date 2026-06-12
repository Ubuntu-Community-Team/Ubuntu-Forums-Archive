---
title: "Unofficial Ubuntu Package Site"
date: 2006-08-17
forum: General Help
---

### Post by plb on 2006-08-17
I also posted this in Ubuntu Cafe but this seems to get more traffic so I thought I'd run this idea through here. The one thing I always notice is users looking for packages when new applications are released, for instance the latest rythmbox etc. So I was thinking we should setup an unofficial site where users can upload, download ubuntu packages, we could also setup repositories.....all unoffical and use at your own risk of course. The site would contain a search, a list of the latest packages uploaded, the most popular etc. Also what version the package was tested and installed on, release notes and a comment field etc. What do you guys think about something like this.

---

### Post by secretlondon on 2006-08-18
There is something called Ubuntu backports which has up to date packages I think.

---

### Post by HAARP on 2006-08-19
Still, there are many outdated packages.

I'd like to have this, since I make simple packages myself, and I'd like to contribute them to the community.

---

### Post by The Noble on 2006-08-19
I would personally want a community maintained repo. Synaptic would probably need some slight redesign, at least show version number, who made the package (only people who are part of the forums can put up packages so we can notify of problems), and maybe some other things. I would definitely help!

---

### Post by aysiu on 2006-08-19
Aren't the Universe repositories community-maintained?

---

### Post by peabody on 2006-08-20
Yes, but to my knowledge they comprise the debian packages that Canonical is too busy to officially support.  The versions are frozen for release, to my knowledge, and only allowed to upgrade if backporting something security or bug related proves too difficult.  The community work then goes into the development release.  I'm under the impression that the original poster was talking about working on unofficial packages for dapper.

To be honest, if you want to run bleeding edge, you probably need to be running edgy.  Dapper is meant to be a stable release.  There is backports as someone else mentioned:

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports).

The hardest part about running the latest and greatest versions of packages is that it causes "upgrade creep".  For example, I want to run the cvs version of software package A.  This means running version W of library X, which requires version Y of library Z, but version Y of Library Z breaks packages B, so package B needs to be upgraded to the latest version which fixes the problem, but that breaks package C, and on, and on, and on, and on, and on, and on.  Backports has some strict policies governing what gets backported because of this, numero uno being the package must already be in edgy.

Anything unofficial anybody can do, all you need is an http or ftp server and bandwidth, so if you have a need to have a particular version of software "dapper-ized", and no one else has done it yet, you can just try to do it and if you succeed you can setup your own repository and offer it to the community.  Quinn does this with the xgl/compiz packages.  There's also the cipherfunk.org repository for the really sketchy codecs.  It's best to maintain small repos for specific things.

So to answer the question the original poster proposed, I personally wouldn't want to deal with these problems myself, which is why I think it's a better policy to just pass around and pin unofficial debs or run seperate unofficial repositories, with the understanding that using too many can mean trouble.  Making something as potentially unstable as this seem community based and official could mean a lot of confusion for new users.

---

