---
title: "Error with dpkg, dealing with JDK7 and OpenMPI"
date: 2012-10-25
forum: General Help
---

### Post by Damascushead on 2012-10-25
I am running 12.04, and am able to run java just fine. My programs which I write compile and run in java without error.  Just in case it is needed the output to** java -version** is:

```
 java version "1.7.0_05"
Java(TM) SE Runtime Environment (build 1.7.0_05-b05)
Java HotSpot(TM) Client VM (build 23.1-b03, mixed mode)

```I am trying to install OpenMPI and configure it on my system. I have the correct compilers, but when I run
 ```
sudo apt-get install libopenmpi-dev openmpi-bin openmpi-doc
```I get the following error:

[B]Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

The strange thing is, is that when I try to update (which should be done weekly), I get the **exact same error**. I have looked in my logs, but am a bit lost as to what I should even be looking for. I have not updated in months, as I am completely unable to.

I would like to be able to update, but more importantly I need o be able to download and install OpenMPI, as I am in a bit of a time crunch (by tomorrow) to get some other
MPI related software up and running. 

I have tried reinstalling java but nothing seems to be doing the trick.

Any help on the matter would be greatly appreciated!! 

Peace and Music

---

### Post by Bashing-om on 2012-10-25
hi ! Damascushead ;

You advise can not down load any updates ?
Likely a dpkg configuration situation...
let us look at what errors dpkg generates; post the results of terminal commands:
```
sudo apt-get update
sudo apt-get upgrade
```see if we can get this squared-away
[INDENT]warm regards <==BDQ

[/INDENT]

---

### Post by Damascushead on 2012-10-25
Ok I just solved the problem. The following codes fixed it:

```
sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
sudo apt-get update
```

I ran them right before I did a fresh install of Java 7.

I am not sure how I would have intrinsically known which files to look in for these removals to be made, but now the error is gone, and I have successfully installed OpenMPI. Even though I don't know why these files fixed the problem :P

Thank you for offering to help though. There is always great help on these forums!

---

