---
title: "Inexplicable Java Problems"
date: 2007-09-08
forum: General Help
---

### Post by LodeRunner on 2007-09-08
As I said in [http://ubuntuforums.org/showthread.php?p=3321298#post3321298]this]("http://ubuntuforums.org/showthread.php?p=3321298#post3321298") thread, I've been using Interactive Broker's TWS platform for a year now when it suddenly quit on me.  No error, no nothing it just sits there in bash without producing the GUI.  This happened on my laptop and desktop simultaneously, so I figured an system update (which lately I've just been blindly installing, 'cause the pop-up notifiers are annoying and there isn't an obvious STFU button--a wee bit too Windows-like if you ask me, but that's a rant for another day) was to blame.

After a few hours of tinkering I've still gotten nowhere (can't seem to find a recently installed package to blame), so I decide to confirm that TWS will run like it used to with a fresh feisty install.  BUT... this is what I get when trying to install the JDK while running the livecd:

Setting up sun-java6-bin (6-00-2ubuntu2) ...
/usr/lib/jvm/java-6-sun-1.6.0.00/bin/java: error while loading shared
libraries: libjli.so: cannot open shared object file: No such file or
directory
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127

Same error if I try using the java5 JDK instead.

I'm too tired to make sense of it anymore.  The install disc is the same and the repository I downloaded it from is the same.  I've installed Feisty damn near a half dozen times in the past few months, always with the JDK, and never seen this before (ok, so I'm trying to "install" it while running the liveCD but that shouldn't matter.)  

Basically, I've got one baffling Java problem making it impossible for me to troubleshoot another baffling Java problem. I would say that they're related, except I can't see how that could possibly be the case--neither the JDK nor anything else obviously Java-related was updated on my machines in the past week (in fact, I can say with 95% certainty that nothing other than kerberos was updated since the last successful TWS login.)

I guess I could try a manual jdk install...

---

