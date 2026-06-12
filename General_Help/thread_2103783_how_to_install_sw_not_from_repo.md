---
title: "how to install s/w not from repo?"
date: 2013-01-11
forum: General Help
---

### Post by trisgti on 2013-01-11
hi all,
I've been using Linux for a while but have always installed s/w using the GUI.
 
now I want to install some image stacking s/w called Starstax but this is not in the repo but you have to download a .tgz file.
 
here's the download\install instructions: [http://www.markus-enzweiler.de/StarStaX/StarStaX.html#download](http://www.markus-enzweiler.de/StarStaX/StarStaX.html#download)
 
is there a "correct" way to do this? should I download the file and run a terminal command to unzip? also should I unzip to a specific location?
 
thanks for any help!

---

### Post by iMac71 on 2013-01-11
the easiest way is the following:
1) download the file (pay attention to the architecture, i.e. x86 or amd64, and to the Ubuntu version, i.e. 10.04 or 12.04);
2) open a Terminal window and type:```
cd Downloads
tar -xvzf filename
```where filename is the name of the file you've just downloaded;
3) during the extraction process it will be created a new directory the name of whom is the same of the file you've downloaded, but without .tgz
4) when the extraction process will be completed, type:```
cd dirname
```where dirname is the name of the directory;
5) finally, type:```
./StartStaX
```

---

### Post by stinkeye on 2013-01-11
I don't think it needs to be placed in any particular directory to run.
Just right click on the .tgz file and choose **Extract Here**.
Then just click on the **startStarStaXLinux.sh** and choose run.

---

### Post by trisgti on 2013-01-11
thanks for the quick replies guys!
 
so it is ok to just unzip and run from the downloads folder?  I guess I was wondering if I should unzip it elsewhere like /usr or /opt maybe?

---

### Post by iMac71 on 2013-01-11
> **trisgti said:**
> thanks for the quick replies guys!
 
so it is ok to just unzip and run from the downloads folder?  I guess I was wondering if I should unzip it elsewhere like /usr or /opt maybe?you can move the archive to another folder, e.g. your home folder, by dragging the archive icon in that folder and unzip in it the archive itself.
The unzip process creates a new folder that contains the StartStaX files; just double click on the icon of the new folder and then double click on the icon of StartStaX.sh.
The above is the GUI version of what I wrote in my previous post: it's to you to choose what way you like more

---

