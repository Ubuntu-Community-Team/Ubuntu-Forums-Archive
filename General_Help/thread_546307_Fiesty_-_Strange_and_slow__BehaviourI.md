---
title: "Fiesty - Strange and slow  BehaviourI"
date: 2007-09-08
forum: General Help
---

### Post by ricardoec on 2007-09-08
I have an HP nw8440, dual core, 2 GB mem, ATI x1600 an of course, Ubuntu 7.04.

An almost fresh installation other than the tewaks nescessary to get thiss unstable, but nice-to-work with distro working.

A few days (not hours) to get Compiz Fusion running, as it shoud (using XGL and ATI binarie video drivers (8.40.8) since the mesa stuff dont get well with this setup.

Everiting works fine, but suddenly.... SLOW... SLOW... I must say that I have Vmware Server installed so I can do Win XP stuff. Vmwar working fine, and then suddently, does not want to load, or takes time to do so, or gives me storage messages such as thatit Wmwar is not installed or not currently installed, .. that it cannot gry Vmware to worok because .. bla... bla ...bla.. wait for 15 mins, and Vmware is Up and running fine.

this morning I wathecd my favourite sport.. Formula 1... [www.formula1.com](www.formula1.com) has a Java applet wich provides real time inof as to how the race is going..... Half an hour to get the Java component load.. so I decided to birng up the VM and Win XP and swiftly fowllowed the race using XP 's Internet eplorer.

Now, this is not a matter of missconfiguration or *.conf files missplaced.. or disk space which I have plenty (100 GB all together) is a matter of UBUNTU 7.04.. which I do like.. but i is starting to drive me nuts

Any Ideas???

---

### Post by ricardoec on 2007-09-08
Forgot to say, that when this Java applet is trying to laod... the CPU goes up to 100%.. Strange ah?

---

### Post by Steveway on 2007-09-08
Try a non-XGL-session.
Java has some problems under composited enviroments.

---

### Post by ricardoec on 2007-09-08
Got it friend. As a matter of fact, Java a Compiz dont get along well.. a thing to be sorted in a Java (linux) environment.

I went to my plain vanilla Gnome and works fine, still not as well as in the Virtualized XP. There  must be something wrong with the Java Box running under the current Fiesty Kernel (2.20.16) . I dont recall having the same issue on the lowlatency one.

Thanks for your help.

---

