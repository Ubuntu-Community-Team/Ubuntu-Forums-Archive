---
title: "dpkg was interrupted in terminal"
date: 2013-10-11
forum: General Help
---

### Post by ddubbz1979 on 2013-10-11
getting this at the end return of anything i do in the terminal.  dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.  started when I tried to work out an issue with my broadcom 4318 wifi (which still isn't fixed.)  Any help appreciated.

---

### Post by slickymaster on 2013-10-11
Did you to run the command he was telling you to?```
sudo dpkg --configure -a
```

---

### Post by ddubbz1979 on 2013-10-11
> **slickymaster said:**
> Did you to run the command he was telling you to?```
sudo dpkg --configure -a
```

I did and the terminal hung up and never completed leaving me this for last lines of output.

[IMG][[IMG]http://s24.postimg.org/8ifzas2f5/dkmsinstallcompleted.jpg[/IMG]]("http://postimg.org/image/8ifzas2f5/")[/IMG]

---

### Post by slickymaster on 2013-10-13
One thing you could try, even though it's not guaranteed to solve it, is to clean the content of **/var/lib/apt/lists** directory and rebuild it```
sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
```

You can also take a look at this bug, as it addresses a similar situation: [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/1171048](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/1171048)

---

