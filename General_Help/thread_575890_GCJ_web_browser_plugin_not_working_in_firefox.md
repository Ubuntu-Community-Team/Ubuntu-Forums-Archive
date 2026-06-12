---
title: "GCJ web browser plugin not working in firefox"
date: 2007-10-14
forum: General Help
---

### Post by Angelbeast on 2007-10-14
Has anyone been able to get this to work?

---

### Post by Angelbeast on 2007-10-14
Anyone?  :popcorn:

---

### Post by geeknik on 2007-10-22
I installed this plugin when prompted on the 64bit version of Ubuntu 7.10 / Firefox 2.0.0.6 and it's not working for me either.

---

### Post by aidanr on 2007-10-22
[https://bugs.launchpad.net/ubuntu/+source/icedtea-java7/+bug/152362](https://bugs.launchpad.net/ubuntu/+source/icedtea-java7/+bug/152362)

> sudo apt-get build-dep icedtea-java7-plugin
sudo apt-get -b source icedtea-java7-plugin icedtea-java7-bin icedtea-java7-jre icedtea-java7-jdk
sudo dpkg -i icedtea-java7-*deb

Worked for me.

---

### Post by geeknik on 2007-10-24
> **aidanr said:**
> [https://bugs.launchpad.net/ubuntu/+source/icedtea-java7/+bug/152362](https://bugs.launchpad.net/ubuntu/+source/icedtea-java7/+bug/152362)

Worked for me.

This did not work for me. I just wasted a couple of hours doing this. WHen I visit [http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1) it tells me that Additional plugins are required to display all of the media on this page.  So I start the plugin finder and it tells me I need the GCJ web browser plugin.  So I tell it to download it.  And then it says that it's already installed.  Thanks!

---

### Post by wedge_antilles on 2008-01-13
> **aidanr said:**
> [https://bugs.launchpad.net/ubuntu/+source/icedtea-java7/+bug/152362](https://bugs.launchpad.net/ubuntu/+source/icedtea-java7/+bug/152362)



Worked for me.

Well, that took a ridiculously long time, but it worked. Thanks!! :guitar:

---

### Post by prole on 2008-01-31
.

---

