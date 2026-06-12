---
title: "error fix?"
date: 2016-03-10
forum: General Help
---

### Post by Lloydb39 on 2016-03-10
Can somebody tell me what this means, and what I should do?
"W:Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file), E:Some index files failed to download. They have been ignored, or old ones used instead."

---

### Post by slickymaster on 2016-03-10
*Moved to the ***General Help**[I] sub- forum

[/I]See this: &#8203;[http://www.webupd8.org/2016/03/fix-failed-to-fetch-google-chrome_3.html](http://www.webupd8.org/2016/03/fix-failed-to-fetch-google-chrome_3.html)

---

### Post by grahammechanical on 2016-03-10
Or,

[http://www.omgubuntu.co.uk/2016/03/fix-failed-to-fetch-google-chrome-apt-error-ubuntu](http://www.omgubuntu.co.uk/2016/03/fix-failed-to-fetch-google-chrome-apt-error-ubuntu)

I used the webupd8 method.

Regards.

---

### Post by ajgreeny on 2016-03-10
Sorry to have to add this note yet again to a third part suggestion but I notice that the way to do this shown in the link from grahammechanical is to use ```
sudo gedit /etc/apt/sources.list.d/google-chrome.list
```
Before anyone else gets to add their comments or ideas to this I would like to remind users that **you should not use sudo for GUI applications.**  You may be not doing any damage with gedit used this way but some other applications started with sudo could (and have to some users) lock you out of the system completely as your username.

You should use **gksudo gedit**, or if you have not installed the gksu package in order to do this, use **sudo -H gedit**, both of which are much safer.

---

### Post by Dennis N on 2016-03-10
I also saw the same error message in 14.04, but the apt history log indicates Chrome 64-bit was still updated despite the message:
chrome-stable:amd64 (48.0.2564.116-1, 49.0.2623.87-1)

So I am just ignoring the message if it appears.

---

### Post by v3.xx on 2016-03-10
A nice one line fix

[http://ubuntuforums.org/showthread.php?t=2316680&p=13453016&viewfull=1#post13453016](http://ubuntuforums.org/showthread.php?t=2316680&p=13453016&viewfull=1#post13453016)

---

