---
title: "Frost Wire"
date: 2007-11-09
forum: General Help
---

### Post by combnii on 2007-11-09
I installed Frost wire but when i try to open it i cant. My java version is java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

any hints pls?

---

### Post by mmilitia9 on 2007-11-09
Try opening up symnatic and searching for "java".. isn't there like a 1.6 runtime?  that's what I have installed.. works great with frostwire

hope that helps..

-nick

---

### Post by rsambuca on 2007-11-09
Are you using 32bit or 64bit Ubuntu?

---

### Post by Maestro23 on 2007-11-09
Should take care of your java problem:

> sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
java -version

Or if you want to use Synaptic (GUI). Just search for sun-java6, Mark the above packages for install.

---

### Post by combnii on 2007-11-10
I am using a 32 bit when i try sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

and when i tried to use synaptic i had this error
sun-java6-bin:
 Depends: sun-java6-jre but it is not going to be installed
 Depends: unixodbc  but it is not installable
 Depends: libstdc++5  but it is not installable

sun-java6-demo:
 Depends: sun-java6-jre but it is not going to be installed
 Depends: sun-java6-jdk but it is not going to be installed

sun-java6-fonts:
 Depends: sun-java6-jre but it is not going to be installed

sun-java6-javadb:
 Depends: sun-java6-jdk but it is not going to be installed

sun-java6-jdk:
 Depends: sun-java6-jre but it is not going to be installed

sun-java6-jre:
 Depends: java-common (>=0.24) but it is not installable
 Depends: sun-java6-bin but it is not going to be installed or
 	ia32-sun-java6-bin (=6-03-0ubuntu2) but it is not installable

sun-java6-plugin:
 Depends: sun-java6-bin but it is not going to be installed

sun-java6-source:
 Depends: sun-java6-jdk but it is not going to be installed

---

### Post by kidguayas on 2007-11-10
Hey thanks for the heads up in how to set frostwire. I have one problem with the installation. I don't have the Java plugin repository. I looked in the sypmnaptic as well and I could not find it. Where can I get it?  This is the message I get every time I try to run it:

[B]Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
[/B]
 I'm running a 64-bit machine and thank you in advance

---

### Post by rsambuca on 2007-11-10
**combnii **- you need to activate all of your repositories.  Go to the top menu bar and select "System -> Administration -> Software Sources".  On the first tab, make sure all of the repositories are checked, then close the Window and Reload your repositories when prompted.  You will then be able to install the java.

**kidguayas **- If you are using the 64bit Ubuntu, then you have to install a different Java version.  You will need to make sure all of your repositories are active as well (see the previous instructions for combnii).  Then open a terminal and enter:```
sudo apt-get install ia32-sun-java6-bin
```Then ```
sudo update-alternatives --config java
```choose the ia32 version when asked.  You should be good to go.

---

