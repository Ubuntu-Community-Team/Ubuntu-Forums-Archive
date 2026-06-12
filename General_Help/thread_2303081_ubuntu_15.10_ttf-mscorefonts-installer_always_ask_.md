---
title: "ubuntu 15.10 ttf-mscorefonts-installer always ask to install"
date: 2015-11-16
forum: General Help
---

### Post by sebastiaan5 on 2015-11-16
Specs: ubuntu 15.10 i7 nvidia gtx 860m 16gb ram


This is the pop-up I always get when starting up:

```
 Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.


ttf-mscorefonts-installer


The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.
```

How can I fix this?


greetings

---

### Post by ajgreeny on 2015-11-16
To install the ttf-mscorefonts-installer package you have to accept the license terms which may have been hidden depending on how you installed them.

Try again in terminal this time with command ```
sudo apt-get install ttf-mscorefonts-installer
``` and I think the license window will appear unhidden.  Use tab key to highlight the OK or Yes (I can't remember which it shows) and hit enter.

---

### Post by sebastiaan5 on 2015-11-16
Well if I do that it says I already installed it :/

---

### Post by Vladlenin5000 on 2015-11-16
> **sebastiaan5 said:**
> Well if I do that it says I already installed it :/

Then just reinstall:
```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```
and make sure to accept the EULA.

---

### Post by sebastiaan5 on 2015-11-17
Did that, but when installing it gives this error:

```
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
Get:1 http://downloads.sourceforge.net/corefonts/andale32.exe [969 B]
Fetched 969 B in 0s (1,237 B/s)                                                     
E: Failed to fetch http://downloads.sourceforge.net/corefonts/andale32.exe  Hash Sum mismatch

E: Download Failed
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu2) ...


```

---

### Post by ajgreeny on 2015-11-17
See if you can find that faulty downloaded file. I don't think it will be in /var/cache/apt/archives but look there first and if it is not there run ```
find -name andale32.exe
``` and then delete it with ```
sudo rm /path/to/andale32.exe
```
Now try installing again as it sounds as if there was a bad download first time.

PS: Sorry about the mix-up with the install --reinstall requirement.  I was not thinking quick enough.

---

### Post by sebastiaan5 on 2015-11-17
So I tried to look for andale32.exe but I don't find it, terminal doesn't even give any output.

ps. I reinstalled ubuntu-restricted-extras, then ttf-mscorefonts-installer but got a new error:

```
Err http://downloads.sourceforge.net/corefonts/arial32.exe
  The HTTP server sent an invalid Content-Range header
E: Failed to fetch http://downloads.sourceforge.net/corefonts/arial32.exe  The HTTP server sent an invalid Content-Range header

E: Download Failed


```

---

### Post by buzzingrobot on 2015-11-17
The Sourceforge server that hosts those font files has been a problem for me several times. It's often offline or so slow the transaction times out.

The package you install does not contain the font files, but a script that downloads the fonts from Sourceforge and installs them. That fails after the package itself successfully installs.

I never came up with anything better than to wait it out until the server cooperated. Then I gathered all the font files and stashed them away so I can avoid this annoyance in the future.

Btw, you probably would not miss the fonts if they weren't installed.

---

