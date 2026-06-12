---
title: "Firefox 1.0"
date: 2004-10-15
forum: General Help
---

### Post by -baHam- on 2004-10-15
Any idea of how to run it on ubuntu..? If I uninstall the firefox already on ubuntu, ubuntu wants to remove ubuntu-desktop too.. So I cant install the debian package..

What to do ?  :shock:

---

### Post by ubuntu-geek on 2004-10-15
This will work :)

Download this: [http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/0.10.1/firefox-1.0PR-i686-linux-gtk2+xft.tar.gz](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/0.10.1/firefox-1.0PR-i686-linux-gtk2+xft.tar.gz)

Open up a terminal window:
tar xvzf firefox-1.0PR-i686-linux-gtk2+xft.tar.gz

sudo mv /usr/bin/firefox /usr/bin/firefox.orig
sudo ln -s /home/username/firefox/firefox /usr/bin/firefox

Then goto Computer &gt; Desktop Preferences &gt; Preferred Applications

Click on the Web Browser tab, select custom web browser and enter the path to firefox you downloaded..

/home/username/firefox/firefox %s

click close that should do it :)

---

### Post by -baHam- on 2004-10-15
Nah, doesnt work..

---

### Post by ubuntu-geek on 2004-10-15
Sure it does..  I have done it many times. What problem are you having?

---

### Post by -baHam- on 2004-10-15
I mean, the old firefox runs.. Also if I run the file from the directory where I untarred it  :shock:

---

### Post by ubuntu-geek on 2004-10-15
Kinda sounds like the sym link didnt work. If you cd into the untared firefox directory and run ./firefox and then look at the version is the new one?

---

### Post by Jspired on 2004-10-15
That worked for me.  I've had it up and running for a time now.

---

### Post by -baHam- on 2004-10-16
Yea Yea, I'm lame. It works.

---

