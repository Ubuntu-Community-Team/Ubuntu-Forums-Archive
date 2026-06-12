---
title: "Installing teamviewer 11 on Ubuntu 14.04 LTS : Issues"
date: 2016-07-02
forum: General Help
---

### Post by Pandee on 2016-07-02
I'm following a few guides such as

[http://www.ubuntumaniac.com/2015/12/install-teamviewer-11-on-ubuntu-1604.html](http://www.ubuntumaniac.com/2015/12/install-teamviewer-11-on-ubuntu-1604.html)

But when I am finally going to launch teamviewer I get:

Verification of your Teamviewer failed! Team viewer will quit for security reasons. Please reinstall TeamViewer;

I have tried reinstalling but i get the same error. What am i doing wrong?

---

### Post by howefield on 2016-07-02
The tutorial looks a bit off, it asks you to download a file called teamviewer_i386.deb but install teamviewer_linux.deb.

Just tested on a virgin copy of 14.04 with the downloaded .deb package from teamviewer.com which installed just fine. Try double clicking on the file that you downloaded with wget.

---

### Post by Pandee on 2016-07-02
Hello thanks!

I did a re-download and installed it. What file do i use to launch it? Maybe I'm running the wrong file?

---

### Post by howefield on 2016-07-02
You mention that you are using Ubuntu so are using the Unity desktop environment ?

Just search the Dash for teamviewer..

---

### Post by Pandee on 2016-07-02
Hello!

Yes I'm using Ubuntu 14.04 LTS with VNC, i did an alt-f2 but typing in teamviewer doesn't bring up anything

-----------------

Edit:

I found the application under the normal Application Finder. Same error.

-------------------

Edit2: 

I have looked around and  tried: 

"sudo dpkg -i /path/to/deb/file followed by sudo apt-get install -f"

And It i still get the error >_<

---

### Post by howefield on 2016-07-02
Double clicking the teamviewer_i386.deb file that you downloaded should initiate the installation process via your default software manager, possibly the Software centre ?

Using the terminal code..

```
teamviewer --version
``` 

should tell you which version is installed, and confirming that it is installed, eg

```
hugh@trusty:~$ teamviewer --version

 TeamViewer                           11.0.57095  (DEB) 

hugh@trusty:~$
```

The executable should be found in..

```
/usr/bin/teamviewer
```

---

### Post by Pandee on 2016-07-02
Hello!

I get the same version and information in your code in box 2.

I went to the executable path you put in code box 3 but it still gives the same error. 

I've tried installation via command line and with GDebi PI as well.

---

### Post by howefield on 2016-07-03
Try purging the Teamviewer installation and starting again.

```
sudo apt-get purge teamviewer
```

Then reinstall the package.

---

### Post by Pandee on 2016-07-03
Hello I will try that!

Last time i tried a fresh installation it restarted/killed my vnc service. Will it happen again?

---

### Post by Pandee on 2016-07-17
Hello,

I have tried things over and over. Not working. Perhaps you can recommend me a program other than teamviewer for remote access and control?

----------------------

I tried installing and removing folders that still existed for teamviewer,

now everytime i launch it, vnc says "connection has been gracefully closed" after, it then crashes.

---

