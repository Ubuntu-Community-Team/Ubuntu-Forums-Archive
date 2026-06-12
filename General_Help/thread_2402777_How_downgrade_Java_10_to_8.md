---
title: "How downgrade Java 10 to 8?"
date: 2018-10-04
forum: General Help
---

### Post by borucki-andrzej on 2018-10-04
I try 
sudo add-apt-repository ppa:webupd8team/java

is:

gpg: keyserver receive failed: End of file

---

### Post by i7Fd-2sCB1 on 2018-10-04
> **borucki-andrzej said:**
> I try 
sudo add-apt-repository ppa:webupd8team/java

is:

gpg: keyserver receive failed: End of file

If you have followed the instructions did you issue 

```

sudo apt-get update

```

After adding that repository? 

You'll then need to install java 8 from 
```

sudo apt-get install oracle-java8-set-default

```

 to set it to default to java 8 from what I've read on [http://ubuntuhandbook.org/index.php/2018/05/install-oracle-java-jdk-8-10-ubuntu-18-04/](http://ubuntuhandbook.org/index.php/2018/05/install-oracle-java-jdk-8-10-ubuntu-18-04/) and [http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)

Though is there an actual reason you wanting to downgrade java to a previous release rather than an up-to-date version? Java 10 should work with previous java releases or java apps...

---

### Post by ajgreeny on 2018-10-04
Do you have a specific reason for using Oracle java instead of openjdk?

Openjdk is already on version 11 for Ubuntu 18.04, which I assume you are using, but I believe you can install version 8 instead of, or as well as 11, if needed.

---

