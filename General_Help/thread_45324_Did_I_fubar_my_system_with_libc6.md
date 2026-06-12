---
title: "Did I fubar my system with libc6?"
date: 2005-06-29
forum: General Help
---

### Post by Zelmo on 2005-06-29
Yesterday I was checking out different chess programs and found a deb package for glchess. When I went to dpkg -i it, the installer told me I needed libc6>=2.3.2.ds1-21. The libc6 I had installed was 2.3.2.ds1-20ubuntu, in the libc6-i686 package.

I googled for libc6 debs and found that the Debian repositories all have libc6 version 2.3.2.ds1-22, so I downloaded that package and installed it, thinking it would upgrade what I already had. Turns out the libc6-i686 and libc6-dev packages were still installed, and the new libc6 got installed alongside them.

No big deal, right? Except that when I decided I didn't like glchess and went to apt-get remove it, I got a message saying I had 3 broken packages relating to libc6, and that I should do an apt-get -f install to try to fix it. That command came up with a list of 38 packages that would be removed, and a lot of those were things I wanted to keep.

So I tried reinstalling Ubuntu's libc6-i686 package to see if it would consider that a downgrade and get rid of the offending new package. No dice.

Next I issued the apt-get -f install command again, took a screenshot of the terminal window before committing the changes (so I could refer to the list of packages it was removing and later put back the ones I wanted), then hit Enter to continue. After that the Ubuntu libc6-i686 and libc6-dev packages were gone, but the Debian libc6 is still there. And it won't let me install the Ubuntu libc6 packages while the Debian package is there.

My last thought was to remove the Debian libc6 package, intending to then install the Ubuntu packages, but issuing the apt-get remove libc6 command brought up a list of what looked like everything on my system, saying it would all be removed, and I probably shouldn't do that (seriously, it said "You are about to do something potentially harmful" and rather than the usual "Continue? [Y/n]" it said "To continue type in the phrase 'Yes, do as I say!'" Try it sometime, it's kind of amusing. Just don't really remove all that stuff!).

In the meantime, there's an awful lot of stuff that I can't install or uninstall or is otherwise broken because it depends on those Ubuntu libc6 packages that are now gone and won't come back. Does anyone have an idea how I can restore harmony to my system?

---

### Post by Xian on 2005-06-29
[QUOTE=Zelmo]After that the Ubuntu libc6-i686 and libc6-dev packages were gone, but the Debian libc6 is still there. And it won't let me install the Ubuntu libc6 packages while the Debian package is there.[/QUOTE]
You need to instruct aptitude to install a specific version of that package.
The command to do this is as below:
```
$ sudo aptitude install <pkgname>=<version>
```
So, let's assume we want the libc6 package version 2.3.2.ds1-20ubuntu13.
This would be the command:
```
$ sudo aptitude install libc6=2.3.2.ds1-20ubuntu13
```
To check what versions are available:
```
$ apt-cache show <pkgname>
```

---

### Post by Zelmo on 2005-06-29
Thanks Xian, it looks like that worked really well.

---

### Post by dmber on 2006-11-28
i downloaded the "plugin deb" from this [HOWTO]("http://ubuntuforums.org/showthread.php?t=279990") to install flash 9, just to be able to get ESPN.com to work.  i double-clicked the installer like the howto said and it says "Error: dependency is not satisfiable: libc6"

I have no idea what that means.  thanks!!

---

