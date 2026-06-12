---
title: "Why does apt-get say packages are no longer required when they are?"
date: 2014-02-15
forum: General Help
---

### Post by desconocido on 2014-02-15
I have a new computer which has the amd64 version of Ubuntu 12.04.3 installed. (Also has unity and unity2d removed and gnome-shell installed - I use Gnome Classic.)

I Installed apt-show-versions using apt-get install.
Amongst other things, apt-get said
"The following packages were automatically installed and are no longer required:
libkrb5-3:i386 libk5crypto3:i386 .... [65 libraries in total]
Use 'apt-get autoremove' to remove them."
So I did apt-get autoremove

However, this broke my installation of Skype. Trying to re-install Skype failed. Trying to re-install the libraries it needed failed. Things got worse ending up with a message "You requested to remove a package which is an essential part of your system." You can see all the details at [http://ubuntuforums.org/showthread.php?t=2203319](http://ubuntuforums.org/showthread.php?t=2203319)

I notice that other people have had difficulty with apt-get autoremove removing needed packages:
[http://ubuntuforums.org/archive/inde...t-1203065.html](http://ubuntuforums.org/archive/inde...t-1203065.html)
[http://ubuntuforums.org/archive/inde...t-1132579.html](http://ubuntuforums.org/archive/inde...t-1132579.html)

I would like to understand what went wrong so that I can avoid having to re-install Ubuntu in future.

1) My first thought was that something was wrong with apt-show-versions, but I think this is unlikely.
2) I had to add```
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free
```to /etc/apt/sources.list (instruction from Opera). Could altering repositories be a problem?
3) Maybe this version of Ubuntu doesn't handle the transition to 64 bit versions of libraries well enough? (All the libraries removed (initially) were :1386 types.)
4) Maybe I didn't run apt-get update enough?
5) Maybe dpkg, gdebi, apt-get and ubuntu software center don't work well together and don't keep the same lists of dependencies?
6) Could there be a bug in apt-get?

My current workaround is to never run apt-get autoremove but I would prefer a more robust solution.

Thanks for any suggestions you may have.

---

### Post by CaptainMark on 2014-02-15
I think the problem lies more in the packaging of Skype, possibly the package depends on another package that is not earmarked as an actual dependency, hence auto-remove has removed it, and sorry to say, once you're into dependency hell (even a milder form modern form of it) it's very difficult to get out. I wouldn't be so quick to assume you've done something wrong,

---

