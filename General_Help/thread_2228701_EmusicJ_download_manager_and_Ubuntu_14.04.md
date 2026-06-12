---
title: "Emusic/J download manager and Ubuntu 14.04"
date: 2014-06-09
forum: General Help
---

### Post by thedoctor818772 on 2014-06-09
I have an account with Emusic and had been using it on my old laptop for a while but it had lapsed. Now (for many reasons) I want to keep on using that account on my new laptop which runs Ubuntu 14.04. However, I am having a lot of difficulty installing Emusic/J on this new laptop. I have downloaded the appropriate 64bit file and after extracting it, and attempting to run it, I get just a txt file and within that file, a message stating that I need Java to run said program. I have open jdk 7 (?) installed on my box currently so I am not sure what the issue is. Any assiatance is apreciated. Thanks,

-Michael Dykes

---

### Post by KennethLarsen on 2014-06-09
This could be because Emusic/J is looking for another Java version. 

> **If you get an error when you run eMusic/J from the command line:**
It  probably means you have another version of Java installed, for example  GCJ or Blackdown. This means that the Sun Java may not be used. To fix  this, install and run galternatives. This will let you select which JDK is the default one. The command line equivalent to galternatives is to do:
sudo update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java 


from: [http://www.kallisti.net.nz/EMusicJ/InstallingJava](http://www.kallisti.net.nz/EMusicJ/InstallingJava)

---

### Post by thedoctor818772 on 2014-06-09
Upon trying that, I get the following error:

[I]error: alternative /usr/lib/jvm/java-1.5.0-sun/jre/bin/java for java not registered; not setting

[/I]

---

