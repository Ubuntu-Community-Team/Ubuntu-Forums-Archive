---
title: "apt-get error: but it is not going to be installed"
date: 2005-10-16
forum: General Help
---

### Post by dtfinch on 2005-10-16
This has to be one of the most useless error messages I've ever encountered. It's as helpful as saying "there was an error".

I started with the preview release of Ubuntu Breezy. There was a lot of neat stuff i there. Everything worked. I installed Eclipse from the repository, and got to see Eclipse running well on gcj. On the day that Ubuntu Final was released, this was all broken. Apt-get wanted to remove Eclipse for its own satisfaction. Eventually I noticed that a bunch of alternate Eclipse packages were added in its place, so I figured they just did a rename and I'd just have to uninstall and reinstall.

When I went to reinstall Eclipse, I got this error:
The following packages have unmet dependencies:
  eclipse-sdk: Depends: eclipse-jdt (= 3.1.1-1ubuntu3) but it is not going to be installed
               Depends: eclipse-pde (= 3.1.1-1ubuntu3) but it is not going to be installed

Trying to install any of the Eclipse packages gives the same useless error. I've gotten this error message in the past, and it has always been completely uninformative as to what's wrong. There's no documentation anywhere as to what the error message means. Even the source code is extremely unhelpful. There are no comments relating to the error message, and the code that prints the error is nowhere near where the error originates. It appears that it just sees that it has failed and tries to guess at what went wrong long after the fact, hence the extreme vagueness. Add to that the fact that apt-get has no real debugging/verbosity command line options and we have a real problem.

---

### Post by wylfing on 2005-10-16
I agree that those messages are frustrating.

I can't tell from your message whether you're just venting or if you want help trying to solve what went wrong :)  I'll assume the latter -- if it's not true then at least if anyone searches on this in the future they might get some help. I'll also preface this by saying I don't know anything about how Eclipse is installed.

Probably what is happening is that when you uninstalled Eclipse it left some of its dependencies behind, namely eclipse-jdt and eclipse-pde. The version of those packages that are still on your system was correct for the old Eclipse package but is incorrect for the new Eclipse package. So when apt-get looks at the dependencies of the new Eclipse, and finds there's a conflict with what is already on your system, it simply stops.

Why? Because apt-get has no way of knowing whether uninstalling these pacakges (to replace them with the new ones) would break your system. It chooses safety over non-safety and does nothing. The package maintainer for Eclipse probably didn't specify that the new versions of eclipse-jdt and eclipse-pde replace the ones you've got. I can't guess what the reason was, but it could have simply been an oversight. In any case, apt is doing the right thing.

You may be able to remedy this problem by telling apt it's OK to uninstall the old packages (with [FONT="Courier New"][COLOR="DimGray"]apt-get remove eclipse-jdt eclipse-pde[/COLOR][/FONT]). Then trying installing the new Eclipse again.

HTH

---

### Post by dtfinch on 2005-10-16
Removing the libswt packages seems to have satisfied it. I'll know for sure when it finishes downloading and installing.

EDIT: It installed fine and seems to work. Thanks for the removal tip.

---

