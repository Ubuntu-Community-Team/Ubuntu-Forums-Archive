---
title: "Apt Errors"
date: 2007-09-09
forum: General Help
---

### Post by Linux_Man on 2007-09-09
Ok, I was testing out apt-get and I did



sudo apt-get purge



And it hung for a while and so I did ctrl + C to stop it, however it was removing alot of files, even though I "thought" it was only to remove broken packages So, should I spend some time repairing it until 7.10 comes out? Or should I just save my settings and just reinstall ubuntu? Because now when I try to run dolphin from the command line I get


X Error: BadDevice, invalid or uninitialized input device 169
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device


even though dolphin starts up and runs fine. So am I just making a big deal about nothing? Or did I really mess up my system?

---

### Post by Linux_Man on 2007-09-09
Also, is there a way that you can turn off updating for certain programs? Because I compiled a build of Firefox but Ubuntu keeps insiting that its version is more recent although they are both 2.0.0.6 also, can you update firefox from help/check for updates without running it as root? Because that just seems insecure and I don't want a new binary one replacing the hours I spent compiling it....

---

### Post by zvacet on 2007-09-09
For first go to **synaptic>file>history.**There you will see all removed packages and maybe that help you to reinstall them again.
For second synaptic>mark package you don´t want to be upgraded and **edit>lock version**

---

