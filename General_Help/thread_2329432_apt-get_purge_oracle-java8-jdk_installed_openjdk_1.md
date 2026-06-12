---
title: "apt-get purge oracle-java8-jdk installed openjdk 1.7 and removed other packages"
date: 2016-07-01
forum: General Help
---

### Post by dean.w.schulze on 2016-07-01
On Ubuntu 14.04 I did

  sudo apt-get purge oracle-java8-jdk

and not only was the jdk8 removed but openjdk7 was installed.  JDK7 wasn't shown in the options given by 

  sudo update-alternatives --config java

before the purge.

The apt-get purge also removed a couple of other packages which we create in house.  

Why did apt-get purge install openjdk7?  Is this to satisfy some dependencies that apt-get knows about?

Would the custom packages that were removed have been removed because they had a dependency on oracle-java8-jdk?

Thanks

---

### Post by Frogs Hair on 2016-07-01
> The apt-get purge also removed a couple of other packages which we create in house.   It is possible there was one or more shared dependencies. If you have synaptic installed open it and check under status and if it shows anything autoremovable or residual that may offer some clues as to what happened. I'm not suggesting removing anything else at this point, just see if any packages are listed and if you recognize them.

---

