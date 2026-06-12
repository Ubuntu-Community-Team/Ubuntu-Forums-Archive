---
title: "deb making, folder ownership issues."
date: 2007-04-08
forum: General Help
---

### Post by ihavenoname on 2007-04-08
Hey, I am trying to learn how to make debs. I am doing this first by learning how to make a deb out of a few files. In this case I have a file that goes into the /opt folder. I have made a deb which creates the folder /opt/bye/ and puts a simple bash script in that folder bye. The command I used is 


```
install -D bye $(CURDIR)/debian/bye/opt/bye/
```

the code went into the debian/rules file under install. 

the deb works fine. But the problem is that when I uninstall the deb it removes the entire opt folder with it. However I made another deb (hello) which does the same thing as above except it installs a file named hello in the folder /opt/hello. Now if I install both these debs I have an /opt directory with the folders hello and bye. Uninstall bye no no longer removes /opt.  However if I uninstall both of these debs my /opt directory get's removed.

Does anyone know how I can make it so that my deb only owns it's own folders and not /opt?

---

### Post by bruenig on 2007-04-08
If a directory is empty, dpkg removes it. So put something in there and it won't remove opt, otherwise it will. The theory is though that it doesn't really matter if it removes /opt since /opt is empty. If you wanted /opt you could remake it.

---

### Post by ihavenoname on 2007-04-08
> **bruenig said:**
> If a directory is empty, dpkg removes it. So put something in there and it won't remove opt, otherwise it will. The theory is though that it doesn't really matter if it removes /opt since /opt is empty. If you wanted /opt you could remake it.

so it's not poor deb making on my part? . 

**Follow-up question:**
Is there anyway to setup an uninstall script?(For debs I mean). 
So that when dpkg uninstalls a package it can be told to do something right after it? (Ex. mkdir  /opt )

---

### Post by ihavenoname on 2007-04-08
Well, I think I just realized that any application that installs to /opt will probably make that dir if it needs it. But still, I think it would be nice to have an uninstall script.

---

### Post by bruenig on 2007-04-08
Any application that needs a directory that doesn't exist, will have that directory automatically made when dpkg installs. That is how dpkg works. For instance, since you are practicing, create a deb that installs files in /test.

As for the script that runs after removal, it is called a postrm script. It runs after all the files are removed. You put it in the DEBIAN directory before you build the deb.

---

### Post by ihavenoname on 2007-04-08
> **bruenig said:**
> 
As for the script that runs after removal, it is called a postrm script. It runs after all the files are removed. You put it in the DEBIAN directory before you build the deb.
Ah, so I just make a file called postrm in the debian directory and type in there everything I need it to do? Excellant. I'll try that.
Update:
It worked like a charm thank you very much!

---

