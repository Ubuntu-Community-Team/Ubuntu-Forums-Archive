---
title: "Thunderbird 2"
date: 2007-05-12
forum: General Help
---

### Post by AlanR8 on 2007-05-12
Evening

Thunderbird 2 is available via Automatix. Check that you have V2 of Automatix. Go to Adept or Synaptic and check. Download and install if necessary.

Here's the catch. The installation REMOVES the old 1.5 version so whatever you, and the LEAST you should do is COPY the mozilla.thunderbird folder from your home folder. But, whilst you can just copy your old mail folders back to the new installation, now in home/.thunderbird BTW, I had a MAJOR problem with the address book.

Word to the wise. EXPORT your address book from 1.5 as a LDIF file and save it somewhere safe. When Thunderbird 2 is installed, go to the address book and from tools, import.....

I've just saved you about an hour of head scratching...

---

### Post by Paul41 on 2007-05-12
[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

This link shows you how to install Thunderbird 2 without removing the repository version.

---

### Post by aysiu on 2007-05-12
Or use this script:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Thunderbird](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Thunderbird)

---

### Post by Derevko on 2007-05-13
You can find a feisty backport in my repository [http://ubuntu.iuculano.it/](http://ubuntu.iuculano.it/)

[http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)

---

### Post by cgrahge on 2007-05-13
> **AlanR8 said:**
> Evening

Thunderbird 2 is available via Automatix. Check that you have V2 of Automatix. Go to Adept or Synaptic and check. Download and install if necessary.

Here's the catch. The installation REMOVES the old 1.5 version so whatever you, and the LEAST you should do is COPY the mozilla.thunderbird folder from your home folder. But, whilst you can just copy your old mail folders back to the new installation, now in home/.thunderbird BTW, I had a MAJOR problem with the address book.

Word to the wise. EXPORT your address book from 1.5 as a LDIF file and save it somewhere safe. When Thunderbird 2 is installed, go to the address book and from tools, import.....

I've just saved you about an hour of head scratching...

Automatix actually copies your ~/.mozilla-thunderbird to ~/.thunderbird after installing Thunderbird 2.0. So this whole copying and pasting  that you did was a waste of time (Automatix had already done it for you)

---

### Post by AlanR8 on 2007-05-13
Beg to differ...at least not on my installation!

It was therefore  appropriate to post a warning in case someone else made the same mstake somewhere along the line that I did!

---

