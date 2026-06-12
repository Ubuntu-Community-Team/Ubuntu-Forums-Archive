---
title: "Moneydance install"
date: 2007-02-07
forum: General Help
---

### Post by cssutto on 2007-02-07
When trying to install the latest ver of moneydance, I get the following error message:
Error: no `server' JVM at `/usr/local/moneydance/moneydance_linux_x86wj.sh.16516.dir/jre/lib/i386/server/libjvm.so'.

And sure enough, "server" is not in that directory.

How do I get it?

I downloaded the package that has JAVA included, so it would appear that I should have it.

CSSJR

---

### Post by cstudent on 2007-02-07
I use Moneydance, but I didn't go for the java included package. I use Sun java available in the Ubuntu repositories. Make sure you have the Universe and Multiverse repos enabled.

Install the package sun-java5-bin either by searching for it in Synaptic or using ```
sudo apt-get install sun-java5-bin
``` at the command line.

Download the Moneydance package without java and from the command line enter:

```
sudo sh moneydance_linux_x86.sh
```

Make sure you are in the correct directory where your downloaded file resides. Follow the prompts during the installation. It will place Moneydance in the /opt directory. It also creates a menu item under the Applications>Office menu.

---

