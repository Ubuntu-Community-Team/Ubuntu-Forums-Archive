---
title: "Updata Manager tzdata java problem"
date: 2008-06-09
forum: General Help
---

### Post by chezzo on 2008-06-09
just ran the update manager, and it's saying that i have to do a "partial upgrade"
it seems to think that in order to upgrade the "tzdata" (timezone information) package, it needs to remove 5 java packages - "openjdk-6-jre", "openjdk-6-jre-headless", "openjdk-6-jre-lib", "icedtea-gcjwebplugin" and "tzdata-java"
this can't be right, surely?!

---

### Post by chezzo on 2008-06-09
bump

---

### Post by prshah on 2008-06-10
> **chezzo said:**
> just ran the update manager, and it's saying that i have to do a "partial upgrade"

I fixed partial upgrade problems with a ```
sudo apt-get update && sudo apt-get upgrade
```

Also of interest to you:> 
upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; [b]under no
           circumstances are currently installed packages removed,[/b] or packages
           not already installed retrieved and installed. 

---

### Post by the4thchild on 2008-06-11
I encountered the partial upgrade and now keep getting the error when trying to install tzdata-java that it depends on "tzdata (= 2008b-1ubuntu1) but 2008c-1ubuntu0.8.04 is to be installed".  On another Ubuntu 8.04 system, tzdata-java 2008c appears to have been installed ok.

tzdata 2008c has been successfully installed on both systems, according to dpkg.  I've tried to refresh the package listing but still haven't been able to install tzdata-java (and the rest of OpenJDK).  Anyone else encountering a similar issue?  Any way to fix this configuration?

---

### Post by the4thchild on 2008-06-11
I solved my broken packages issue by manually downloading the latest tzdata-java package, installing it, and reinstalling OpenJDK.  Still not sure though why we got asked for a partial upgrade, though.  Looking for the tzdata-java package helped me discover the binary packages pages (which is pretty cool!), including one for tzdata-java:

[https://launchpad.net/ubuntu/hardy/i386/tzdata-java/](https://launchpad.net/ubuntu/hardy/i386/tzdata-java/)

Opening the package told me that an older version was in the software repository, so I went ahead and installed the newer version I had just downloaded.  "dpkg -l tzdata-java" showed that it had installed successfully, and "sudo apt-get install openjdk-6-jdk" installed the Java suite.

---

### Post by oliviacond on 2008-06-20
tzdata-java 2008c still in "updates" repo.
i think i'm gonna wait for general repo.

---

