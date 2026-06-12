---
title: "sudo apt-get purge is not removing everything"
date: 2017-01-06
forum: General Help
---

### Post by tonma on 2017-01-06
First I installed java jdk using "**sudo apt-get install openjdk-8-jdk**" and it required 169 MB of storage.
Now when I want to completely remove it using "**sudo apt-get purge openjdk-8-jdk**" it only shows that 540 KB will be freed, and even when doing so, and then using "**sudo apt autoremove**", it frees additional 56 MB only, so where did the rest of 100+ MB go?

*Edit: I still see openJDK installed if I type "**java -version**" in the terminal, so it didn't actually remove it?
Ty!

---

### Post by Frogs Hair on 2017-01-06
Was this installed via PPA ? If so, the ppa-purge program would work best .

[http://askubuntu.com/questions/307/how-can-ppas-be-removed](http://askubuntu.com/questions/307/how-can-ppas-be-removed)

---

### Post by &amp;KyT$0P# on 2017-01-06
Check [FONT=Courier New]/var/log/apt/history.log[/FONT] for the entry where you installed [FONT=Courier New]openjdk-8-jdk[/FONT].  It should list all the packages that were installed at the time.

Does that help?

---

### Post by tonma on 2017-01-06
It was not installed via PPA, all I did was to type [B]sudo apt-get install openjdk-8-jdk
[/B]Could you guys give it a try yourselves? I mean install openJDK using **sudo apt-get install openjdk-8-jdk**, and then purge it? It's only Java :P, and maybe if you try it yourself you will find a way to remove the missing 100+ MB?

---

### Post by ian-weisser on 2017-01-06
Unable to reproduce your problem.

Follow halogen2's advice and post the install and remove log entries.

---

### Post by tonma on 2017-01-07
Here are the install, purge, and autoremove logs:
> Commandline: apt-get install openjdk-8-jdk
Install: ca-certificates-java:amd64 (20160321, automatic), libpthread-stubs0-dev:amd64 (0.3-4, automatic), libice-dev:amd64 (2:1.0.9-1, automatic), x11proto-kb-dev:amd64 (1.0.7-0ubuntu1, automatic), openjdk-8-jdk:amd64 (8u111-b14-2ubuntu0.16.04.2), openjdk-8-jre:amd64 (8u111-b14-2ubuntu0.16.04.2, automatic), libxt-dev:amd64 (1:1.1.5-0ubuntu1, automatic), libsm-dev:amd64 (2:1.2.2-1, automatic), xtrans-dev:amd64 (1.3.5-1, automatic), libbonobo2-common:amd64 (2.32.1-3, automatic), libxcb1-dev:amd64 (1.11.1-1ubuntu1, automatic), openjdk-8-jdk-headless:amd64 (8u111-b14-2ubuntu0.16.04.2, automatic), x11proto-core-dev:amd64 (7.0.28-2ubuntu1, automatic), libxau-dev:amd64 (1:1.0.8-1, automatic), libgif7:amd64 (5.1.4-0.3~16.04, automatic), libxdmcp-dev:amd64 (1:1.1.2-1.1, automatic), fonts-dejavu-extra:amd64 (2.35-1, automatic), libgnome-2-0:amd64 (2.32.1-5ubuntu1, automatic), x11proto-input-dev:amd64 (2.3.1-1, automatic), libx11-dev:amd64 (2:1.6.3-1ubuntu2, automatic), libx11-doc:amd64 (2:1.6.3-1ubuntu2, automatic), openjdk-8-jre-headless:amd64 (8u111-b14-2ubuntu0.16.04.2, automatic), libgnomevfs2-common:amd64 (1:2.24.4-6.1ubuntu1, automatic), xorg-sgml-doctools:amd64 (1:1.11-1, automatic), libgnomevfs2-0:amd64 (1:2.24.4-6.1ubuntu1, automatic), liborbit-2-0:amd64 (1:2.14.19-1build1, automatic), libbonobo2-0:amd64 (2.32.1-3, automatic), java-common:amd64 (0.56ubuntu2, automatic), libgnome2-common:amd64 (2.32.1-5ubuntu1, automatic)


Commandline: apt purge openjdk-8-jdk
Purge: openjdk-8-jdk:amd64 (8u111-b14-2ubuntu0.16.04.2)


Commandline: apt auto-remove
Remove: libpthread-stubs0-dev:amd64 (0.3-4), libice-dev:amd64 (2:1.0.9-1), x11proto-kb-dev:amd64 (1.0.7-0ubuntu1), libxt-dev:amd64 (1:1.1.5-0ubuntu1), libsm-dev:amd64 (2:1.2.2-1), xtrans-dev:amd64 (1.3.5-1), libxcb1-dev:amd64 (1.11.1-1ubuntu1), openjdk-8-jdk-headless:amd64 (8u111-b14-2ubuntu0.16.04.2), x11proto-core-dev:amd64 (7.0.28-2ubuntu1), libxau-dev:amd64 (1:1.0.8-1), libxdmcp-dev:amd64 (1:1.1.2-1.1), x11proto-input-dev:amd64 (2.3.1-1), libx11-dev:amd64 (2:1.6.3-1ubuntu2), libx11-doc:amd64 (2:1.6.3-1ubuntu2), xorg-sgml-doctools:amd64 (1:1.11-1)


*And again, the command "**java -version**" still shows me 
> openjdk version "1.8.0_111"
OpenJDK Runtime Environment (build 1.8.0_111-8u111-b14-2ubuntu0.16.04.2-b14)
OpenJDK 64-Bit Server VM (build 25.111-b14, mixed mode)


so it didn't fully remove it.
I do have Android-Studio installed, but when I did "**java -version**" prior to installing openJDK, this command showed nothing, so it is not related (At first I installed Android Studio, checked my Java, did not have, and only then did I install the openJDK)

---

### Post by mc4man on 2017-01-07
autoremove doesn't quite deal with recommends of recommends well so this would leave you without any java - 
```
sudo apt-get purge openjdk-8-jre-headless
```

---

### Post by tonma on 2017-01-07
Thank you! that did it, maybe a short explanation of what happened? and how did you know only by the log that, purging openjdk-8-jre-headless would also remove the other packages, and not choosing any other? (Just curious as I'm an Ubunu/Linux novice and wants to learn)

---

