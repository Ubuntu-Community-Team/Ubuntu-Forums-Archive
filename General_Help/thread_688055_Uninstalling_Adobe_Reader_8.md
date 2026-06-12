---
title: "Uninstalling Adobe Reader 8"
date: 2008-02-05
forum: General Help
---

### Post by awilki01 on 2008-02-05
I just installed Adobe Reader 8 to open some encrypted eBook files I purchased.  However, after searching on the net, I learned that the FileOpen API doesn't work well with Adobe Reader 8 and Linux.  I installed Adobe Reader 7 and it works flawlessly. 

Now, how do I uninstall Adobe Reader 8?  I used 'sudo make' commands to install it in my /opt/Adobe folder.  I don't think 'make uninstall' is going to work as I've tried it.

Any help would be appreciated.

Regards...

---

### Post by zvacet on 2008-02-05
In folder from wich you compile it run

```
sudo make unistall
```

---

### Post by awilki01 on 2008-02-06
> **zvacet said:**
> In folder from wich you compile it run

```
sudo make unistall
```

Thanks, however, It did not work....

```

adam@adam-ubuntu:~/Desktop/temp/AdobeReader$ ls
COMMON.TAR  ILINXR.TAR  INSTALL  ReadMe.htm
adam@adam-ubuntu:~/Desktop/temp/AdobeReader$ sudo make uninstall
[sudo] password for adam:
make: *** No rule to make target `uninstall'.  Stop.
adam@adam-ubuntu:~/Desktop/temp/AdobeReader$ 


```

---

