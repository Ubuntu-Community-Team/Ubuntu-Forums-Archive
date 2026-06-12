---
title: "Problem in update-manager"
date: 2016-01-20
forum: General Help
---

### Post by mhortal on 2016-01-20
When I start my computer I get a "prohibited" sign with the error message:
update-manager crashed with SystemError in open(): E:The package jre1.8.0-66 needs to be reinstalled, but I can't find an archive for it
I have downloaded jre-8u66-linux-x64.tar.gz
moved it to /usr/java
and tar xvfz jre-8u66-linux-x64.tar.gz
but I continue gwtting the same message
What can I do?

---

### Post by ian-weisser on 2016-01-20
Dowloading and placing is NOT the same is reinstalling using the package manager.
The system is asking you to do the latter.

---

### Post by mhortal on 2016-01-20
> **ian-weisser said:**
> Dowloading and placing is NOT the same is reinstalling using the package manager.
The system is asking you to do the latter.

Thanks, but how can I do the latter?

---

### Post by ian-weisser on 2016-01-20
Did you ever install JRE from the Software Center, or using the terminal, that didn't involve downloading and unpacking a tarball?
Hint: You did, and your did it from someplace that wasn't the Ubuntu repositories (I can tell by the name 'jre1.8.0-66')

It's a bad idea to mix the same software in both packaged and unpackaged form - you break stuff that way.

You have three options.
1) You can uninstall your manually-installed JRE and use the package manager to install an updated JRE from wherever you got the last one from. (I don't know where - you must tell us that)
2) You can uninstall your manually-installed JRE *and* your from-someplace-else packaged JRE, and the install ordinary, supported openjdk-8-jre package from the Software Center.
3) You can uninstall your from-someplace-else packaged JRE, and stick with your manually-installed JRE.

Which option do you want us to help you do?
If we have any input, we usually recommend #2 - packages are very much easier to maintain on a Debian/Ubuntu system. But it's *your* system.

---

### Post by mhortal on 2016-01-20
Probably what I did wrong was to change jre1.8.0_66 into jre1.8.0-66. Now my Software Center does not work (it produces also the same error as the software-updater). How can I tell the package manager that it should use  jre1.8.0_66 and not jre1.8.0-66?

---

### Post by mhortal on 2016-01-20
Or better still. How can I ignore jre1.8.0-66 and use the runtime environment inside jdk1.8.0_71?

---

### Post by slickymaster on 2016-01-20
*Moved to the ***General Help*** sub-forum*

---

### Post by ian-weisser on 2016-01-20
So you seem to want have an Option #4: Uninstall your manually-installed JRE and your from-somewhere-else-JRE package, and use the package manager to  install a from-somewhere-else.

What repository are you getting these JRE and misnamed-JRE and JDK packages from?


> **mhortal said:**
> Or better still. How can I ignore jre1.8.0-66 and use the runtime environment inside jdk1.8.0_71?
I don't understand the question. Ignore? 
You simply uninstall the old package and install the new package.

```
sudo apt remove package-X
sudo apt install package-Y
```

Since we already know you have at least one broken package, the removal may fail.
If it fails, please post the complete output here, so we can help you remove it safely.

---

### Post by mhortal on 2016-01-20
Finally I managed to remove the package and find out where it came from: it was an .rpm file downloaded from the JAVA site and made a .deb file by means of alien. Then installed the .deb file using dpkg and it got everything wrong. Thanks very much for your help. Now the Software Center works again.

---

### Post by slickymaster on 2016-01-21
Great. Glad you got it fixed.

Please mark your thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so other people searching the forums know that it provides a working solution.

---

