---
title: "CNR is here...yet not"
date: 2007-11-08
forum: General Help
---

### Post by teddybairs1 on 2007-11-08
Ok, I saw on CNR.com that the package for Ubuntu was available. So, having had a good experience with  cnr under Lindows 4.5 I tried to download it and install it. It said it was for fiesty,while I am currently running gutsy, but I figured that I still had a good chance of running it anyway. I tried installing it with gdebi, and was immediately informed that it couldn't resolve a package dependency. CNR requires libapt-pkg-libc6.4-... OK, fair enough, I go hunting in the repos and find out that this is a virtual package already supplied by APT. I went into fiesty's repo to see if it was there, and got the same result. I then found that it might be supplied by the Debian repos, and still no luck. Seeing as the appropriate libs were already supplied by apt I attempted to do the install with dpkg and telling it to ignore that package. It then installed, but then couldn't locate the libapt-pkg-libc6....so library sitting in /usr/lib. I finally had to remove the package and let the .deb sit dormant for the moment in my home folder.

Just wondering if anyone else came up against this, and if they had a fix for it. Whatever anyone else might think about CNR, it does make things easier to get a hold of software, even commercial software, that isn't in the repos.

As a postscript, does anyone else get the feeling that Lindows/Linspire has gone downhill over the last few years? When I first started using Linux, it was the only distro which would actually run all the hardware, even the modem, that I threw at it, and cnr was a blessing even at dialup speeds. Ubuntu has pretty much filled that void and then some, but Linspire still holds a special place and does a better job with the commercial and restricted software than Canonical does for the moment. But their software seems to be getting crappier and crappier. I tried installing freespire 2, because it was based on Ubuntu, on a desktop and got really horrible results, especially with the apt-get/cnr. I wiped it and put ubuntu fiesty on the dirve instead (now gutsy).

---

### Post by S3Indiana on 2007-11-10
The ubuntu repository for 7.10 (Gutsy) is different than 7.04 (Feisty), so the CNR mirror must be different, and the CNR client needs to identify the difference between versions of distributions. The CNR Client to support both ubuntu 7.04 and 7.10 is in final development...

---

### Post by Frak on 2007-11-10
They are working on adding Gutsy Repositories.

As for Linspire/Freespire, just ask Kevin Carmony, former CEO of Linspire. He's bragged about Ubuntu over Linspire for some time.

---

### Post by teddybairs1 on 2007-11-10
I know the repos for fiesty and gutsy are different. I checked both for the package in question, and neither one had it as anything else but a virtual package. The .so is already sitting in the /usr/lib and doesn't need an additional package to install it. Further, from further checking on this forum, it's a necessary library to have if you want anything apt based to work in software retrieval. The problem is just that cnr isn't recognizing it without the non-existant package that it wants. Anyone know how to unpack a .deb and change the package dependencies?

---

### Post by Frak on 2007-11-10
> **teddybairs1 said:**
> I know the repos for fiesty and gutsy are different. I checked both for the package in question, and neither one had it as anything else but a virtual package. The .so is already sitting in the /usr/lib and doesn't need an additional package to install it. Further, from further checking on this forum, it's a necessary library to have if you want anything apt based to work in software retrieval. The problem is just that cnr isn't recognizing it without the non-existant package that it wants. Anyone know how to unpack a .deb and change the package dependencies?
Just install it with app with the --force-yes flag.

---

### Post by por100pre1 on 2007-11-10
> **Frak said:**
> Just install it with app with the --force-yes flag.

Sorry to differ but, force installing that package can cause serious issues. Besides, CNR doesn't support Gutsy repositories yet, so it's better to wait.

---

### Post by Frak on 2007-11-10
> **por100pre1 said:**
> Sorry to differ but, force installing that package can cause serious issues. Besides, CNR doesn't support Gutsy repositories yet, so it's better to wait.
I thought he was talking about some random package.

---

### Post by por100pre1 on 2007-11-10
> **Frak said:**
> I thought he was talking about some random package.

Actually... yes, sorry! However, force installing a package is risky anyways.

---

### Post by Frak on 2007-11-10
> **por100pre1 said:**
> Actually... yes, sorry! However, force installing a package is risky anyways.
[Getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") can solve dependency problems once the application is installed.

---

### Post by S3Indiana on 2007-11-11
> **por100pre1 said:**
> Besides, CNR doesn't support Gutsy repositories yet, so it's better to wait.Correct, that's what I referred to in the [previous]("http://ubuntuforums.org/showthread.php?p=3744473&highlight=cnr#post3744473") post. [CNR.com]("http://www.cnr.com") must mirror the repository, then the client must have the new version of the supported distribution in the database to connect to the mirrored repository. Hope this clarifies...

---

### Post by S3Indiana on 2007-12-01
The latest CNR Client has been [released]("http://www.cnr.com/supportPages/aboutDownloadPlugin.seam") supporting 7.04 & 7.10...

---

### Post by bluenova on 2007-12-05
Just installed the Gutsy version, tried to install a few things:

First try: Install failed, no reason.
Second try: File not found on server
Third try: Successful, but no shortcut in the applications menu.

CNR uninstalled.

---

### Post by teddybairs1 on 2007-12-05
So far, I downloaded the cnr for 7.10 and it's been working pretty well, except that it doesn't add anything to the apps menu. This isn't a big problem, it's just annoying. A launcher is easy to create and the desktop menu is easily modified. I haven't tried it under kde though.

So far though, I haven't seen anything in the CNR warehouse that would really be a must have app that you can't get from the standard add/remove software manager. But, the promise is there... so we'll wait and see.

---

### Post by S3Indiana on 2007-12-05
> **teddybairs1 said:**
> So far, I downloaded the cnr for 7.10 and it's been working pretty well, except that it doesn't add anything to the apps menu. This isn't a big problem, it's just annoying. A launcher is easy to create and the desktop menu is easily modified. I haven't tried it under kde though.

So far though, I haven't seen anything in the CNR warehouse that would really be a must have app that you can't get from the standard add/remove software manager. But, the promise is there... so we'll wait and see.Filter [CNR.com]("http://www.cnr.com") by Commercial Software for applications you might not find in one location (updates to open source packages in-work)...

---

