---
title: "Uninstalling Java from Ubuntu 14.04"
date: 2014-06-01
forum: General Help
---

### Post by Ash1403 on 2014-06-01
Dear all,
I need to uninstall Java from my OS so that I can successfully install my paid-for backup utility, Crashplan.

When I try to install CP, terminal tells me...

[I]The current version of Java (1.8) is incompatible with CrashPlan.
Please install one of the following version of the Sun JRE or OpenJDK: 1.5 1.6 1.7[/I]

I asked CP for advice and was told that I'd need to uninstall Java so that CP would detect an absence and install it itself.
I then had to ask how to uninstall Java...!

The reply was...
*You'll want to open the Ubuntu Software Center, click the button labelled "Installed" in the top menu bar and search for Java. If that doesn't bring up anything relevant, search for Oracle or openjdk.*

I did this, removing the items which appeared.

Trouble is, I'm still gettin this same error message about Java 1.8!

Can anyone please help?

I can follow clear instruction but I'm a noob, otherwise!

Thanks 
Ashley

---

### Post by sammiev on 2014-06-01
[This]("http://ubuntuhandbook.org/index.php/2013/07/install-oracle-java-6-7-8-on-ubuntu-13-10/") should help you out.

---

### Post by slickymaster on 2014-06-02
What Java are you running at the moment in your computer, OpenJDK or Oracle Java?

Can you please post back the output you get from running in a terminal```
update-alternatives --get-selections | grep java
```and from```
update-alternatives --get-selections | grep openjdk
```

---

