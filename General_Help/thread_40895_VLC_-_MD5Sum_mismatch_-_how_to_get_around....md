---
title: "VLC - MD5Sum mismatch - how to get around..."
date: 2005-06-10
forum: General Help
---

### Post by karlbonde on 2005-06-10
I'm trying to install VLC because I read that it can play music streams encoded with aacPlus.  I have the same apt-get repositories as the UbuntuGuide, but I get the following error while trying to install VLC:

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe wxvlc 0.8.1-1ubuntu7 [311kB]
Fetched 311kB in 1s (266kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/wxvlc_0.8.1-1ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/wxvlc_0.8.1-1ubuntu7_i386.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Synaptic cannot install it either.

Could anyone point me in the right direction?  Perhaps there is a different file I could download and install the 'old-fashioned' way?

---

### Post by jovencomunista on 2005-06-11
I have the same problem, i tried with a friend sources.list but it didn't work. I want to know how to fix this problem... and it not only happends with vls, with other too.

---

### Post by coaxx on 2005-06-12
I have the same Problem here. Any ideas anyone? Thanks!

---

### Post by vassie on 2005-06-12
[QUOTE=coaxx]I have the same Problem here. Any ideas anyone? Thanks![/QUOTE]
 Try
```
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/wxvlc_0.8.1-1ubuntu7_i386.deb
sudo dpkg -i wxvlc_0.8.1-1ubuntu7_i386.deb
```
Ben

---

### Post by Xian on 2005-06-12
The 'us.archive.ubuntu.com' mirrors are acting flaky this weekend. Replace each instance of them in your /etc/apt/sources.list with the 'archive.ubuntu.com' prefix instead. Then do an 'apt-get update' session and you should be back on track.

---

### Post by ubuntu_demon on 2005-06-14
[QUOTE=Xian]The 'us.archive.ubuntu.com' mirrors are acting flaky this weekend. Replace each instance of them in your /etc/apt/sources.list with the 'archive.ubuntu.com' prefix instead. Then do an 'apt-get update' session and you should be back on track.[/QUOTE]
 great this works!

Let's continue all md5 threads here :

[http://www.ubuntuforums.org/showthread.php?t=41647](http://www.ubuntuforums.org/showthread.php?t=41647)

I'm closing this thread

---

