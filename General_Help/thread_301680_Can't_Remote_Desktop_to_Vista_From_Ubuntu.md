---
title: "Can't Remote Desktop to Vista From Ubuntu"
date: 2006-11-17
forum: General Help
---

### Post by AkiraXXX on 2006-11-17
Has anyone successfully used Remote Desktop to connect to a Vista machine from their Ubuntu machine?  I have no trouble getting to a Vista machine from Windows XP and I can connect to pretty much anything from Ubuntu except Vista.

Just wondering.  I know I'm still using a Vista beta and the issue may be cleared up by the time the release is final (at the end of the month for me), but I'd like to know if anyone else is having troubles.

Thanks.

---

### Post by frediE on 2007-01-14
There is an option under the Remote Desktop settings that gives 3 options:

1.Don't allow
2.Allow connection from computers running any version of RD
3.Allow connection only from computers running RD with Network Level Authentication

to get XP to connect to Vista you need option 2. However that does not seem to help with Ubuntu.

anyone else have better luck connecting from Ubuntu?

---

### Post by frediE on 2007-01-14
looks like we need rdesktop 1.5+
[http://www.ubuntuforums.org/showthread.php?t=267866](http://www.ubuntuforums.org/showthread.php?t=267866)

---

### Post by K0LO on 2007-02-18
Yes, I just got this working. See the following thread for instructions on how to compile rdesktop 1.5 from source:
[http://www.ubuntuforums.org/showthread.php?t=224212](http://www.ubuntuforums.org/showthread.php?t=224212)

You don't need to install the .zip file on the Vista machine unless you want the "seamless window" capabilities. If you just want to use Remote Desktop to connect to a Vista machine you only need to upgrade rdesktop to version 1.5, which is described in the referenced post. Here are the steps from the article that worked for me. I did this on my Kubuntu 6.06 box and the first step was unnecessary because it already had the latest versions of those packages:
```

sudo apt-get install rdesktop openssl libssl-dev libx11-dev
wget http://howtoforums.net/downloads/rdesktop-1.5.0-rc1.tar.bz2
tar -xjf rdesktop-1.5.0-rc1.tar.bz2
cd rdesktop-1.5.0-rc1
./configure
make
echo "backup rdesktop original";sudo cp -vp /usr/bin/rdesktop /usr/bin/rdesktop1.4BKUP
sudo mv /usr/bin/rdesktop /usr/bin/rdesktop1.4
sudo make install
sudo chmod +x /usr/local/bin/rdesktop
sudo ln -s /usr/local/bin/rdesktop /usr/bin/rdesktop
```After upgrading, I simply ran the GUI front-end for rdesktop (tsclient) and it connected to my Vista machine.
**Edit - I can confirm that this also succeeded on my Kubuntu 6.10 (Edgy) box.

---

### Post by GoldWing on 2007-02-19
+1

God, I love this forum

Not worth a sticky How-To ? Or even better, a forced upgrade ?

---

### Post by CP-Geek on 2007-02-27
worked for me, Vista + Ubuntu 6.10. All works except mouse-movement is busted. I can connect, i can use Vista with keyboard, but mouse position doesn't update on screen. All is well wehn RDP:ing to XP. Ideas are welcome :)

---

### Post by K0LO on 2007-02-27
Afraid that I can't offer any ideas on how to fix this, but I do observe that mouse action in Rdesktop 1.5 when connecting to a Vista machine is screwy (erratic). When connecting to an XP machine it seems fine. I've observed this on two different Linux PCs; one is a ThinkPad with a trackpoint for a mouse, the other is a desktop PC with a Microsoft Wireless mouse. Both exhibit erratic mouse movement when controlling a Vista machine via RDP and are fine when controlling XP machines.

I suspect that there's something about the Vista RDP protocol that is different and not accounted for in Rdesktop 1.5; perhaps it will get fixed eventually.

---

