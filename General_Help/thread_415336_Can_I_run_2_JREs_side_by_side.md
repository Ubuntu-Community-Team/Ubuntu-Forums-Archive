---
title: "Can I run 2 JREs side by side?"
date: 2007-04-20
forum: General Help
---

### Post by TheFuzzy0ne on 2007-04-20
Hi everyone. 

I'm having a little bit of a dilemma with Java. I run Frostwire (a P2P client), which uses Java5, and works happily with it. I have recently decided that I'd like to take advantage of the benefits Java has to offer developers, and so I installed the NetBeans IDE, along with all of it's dependencies, one of which happens to be Java6. I don't have a problem with running Java6, but for some Frostwire does. It starts up, and then exits with an error message stating that they recommend Frostwire is used with Java 1.5.

I assumed that the latest release would be backwards compatible, and would only off more useful stuff on top of the previous version, and that upgrading Java shouldn't be an issue. Evidently, this is not the case...

I seem to have both Java5 and Java6 installed, but within aptitude, Java5 compnents are marked with an "A", which I believe will automatically remove it once it's not longer needed. Both Frostwire, and NetBeans seem to work, but I now get a Java exception thrown when I start Netbeans. Should I be doing everything using repositories, or can I download the binaries from Sun and install them? Also, can I install them both safely, but to separate locations?

Can anyone make any recommendations as to what my next actions should be. I don't want to get rid of either application, but I will do as I must.

Best wishes, and many thanks in advance.

Daz.

---

### Post by TheFuzzy0ne on 2007-04-20
Hi everyone.

I think I've solved my problem. It took a while, but I finally got there, and the answer is yes, you can have more than one version of the JRE running side by side. What's plaguing me now, is if there is anything I can do to upgrade my JRE to the latest version, without screwing up what's been installed from the repositories. I've done a test on the Java Web site, to verify my Java installation, and it says I am not running the latest version. 

Should I just install the latest version? If so, how/where do I need to update my environment variables to reflect this, so the system knows which version to use? I can see a whole host of sym links in /etc/alternatives, but there are a lot there, and I'm not sure if I should be messing with them.

Many thanks.

Daz.

---

### Post by jamb on 2007-04-22
Hi,
I do not know if this may help, but so you are aware about these options.
Verify running Java version and quickly re-configure it in a terminal window:

 - Check running Java version:
```
java -version
```

- Reconfigure the Java versions by:
```
sudo update-alternatives --config java
```

This will prompt you to choose (or keep the existing Java version).
From the list, pick the version of Java you want to be configured.

For the environment, edit the 'hidden' file '.bash_profile' in your home directory.
Append the new path (with your path and version) to the existing PATH.

```
nano .bash_profile
PATH=$PATH:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin

```

Hope this helps.

---

