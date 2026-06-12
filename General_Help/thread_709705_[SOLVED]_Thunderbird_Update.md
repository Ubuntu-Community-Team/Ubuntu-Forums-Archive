---
title: "[SOLVED] Thunderbird Update"
date: 2008-02-27
forum: General Help
---

### Post by stonehouse on 2008-02-27
I am new to linux so please excuse my ignorance. I have downloaded the new version of thunderbird (2.0.0.12) in a tar.gz format.  I can unzip the package but the directory just sits in the desktop area. How do I now install this over the previous version of thunderbird which resides in the /usr/lib directory?

---

### Post by ajeetraj on 2008-02-27
can i ask which version of ubuntu are you using?

Did you try to update your computer and then tried to reinstall it from the repo. I think the thunderbird 2.0 is available in the repo (not sure) but while you are installing or after install you can always notice it. well, just to make sure :) just type this in the terminal:```
sudo apt-get install mozilla-thunderbird
```

hope this helps and of course you can always ask questions if it does work :)

---

### Post by stonehouse on 2008-02-27
I am using 7.10 of Ubuntu.  I have 2.0.0.6 of thunderbird loaded, but would like to install the new version which was released a few days ago.
I did try your suggestion, but I just got the same older version re-installed.
I think my question is not only a thunderbird question but a generic one.  I like to tinker with new and upgraded shareware/freeware.  Often they are written first for Red Hat or Suse distros rather than in a deb or rpm format.  How do I install these preograms in Ubuntu?

---

### Post by aysiu on 2008-02-27
I don't really know that 2.0.0.12 really offers much beyond 2.0.0.6. Ubuntu tends to work its own security fixes into Firefox and Thunderbird without necessarily bumping up the version number.

If you really feel you want the latest version, though, UbuntuZilla should help:
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by stonehouse on 2008-02-27
Thank you very much - ubuntuZilla worked perfectly to update my version of Thunderbird to 2.0.0.12.  Much appreciated.

---

### Post by NJC on 2008-02-27
> **aysiu said:**
> I don't really know that 2.0.0.12 really offers much beyond 2.0.0.6. 

> **Fixed in Thunderbird 2.0.0.12**

      [MFSA 2008-12]("http://www.mozilla.org/security/announce/2008/mfsa2008-12.html")     Heap buffer overflow in external MIME bodies
     [MFSA 2008-07]("http://www.mozilla.org/security/announce/2008/mfsa2008-07.html")     Possible information disclosure in BMP decoder
     [MFSA 2008-05]("http://www.mozilla.org/security/announce/2008/mfsa2008-05.html")     Directory traversal via chrome: URI
     [MFSA 2008-03]("http://www.mozilla.org/security/announce/2008/mfsa2008-03.html")     Privilege escalation, XSS, Remote Code Execution
     [MFSA 2008-01]("http://www.mozilla.org/security/announce/2008/mfsa2008-01.html")     Crashes with evidence of memory corruption (rv:1.8.1.12)[http://www.mozilla.org/projects/security/known-vulnerabilities.html#thunderbird2.0.0.12](http://www.mozilla.org/projects/security/known-vulnerabilities.html#thunderbird2.0.0.12)

The colouring doesn't show up - but MFSA 2008-12 is marked as Critical. But not sure if it applies to Linux.

---

### Post by aysiu on 2008-02-27
> **NJC said:**
> [http://www.mozilla.org/projects/security/known-vulnerabilities.html#thunderbird2.0.0.12](http://www.mozilla.org/projects/security/known-vulnerabilities.html#thunderbird2.0.0.12)

The colouring doesn't show up - but MFSA 2008-12 is marked as Critical. But not sure if it applies to Linux.
I know, but I'm saying that Ubuntu often patches security holes in Firefox and Thunderbird without necessarily changing the version number.

---

### Post by febrile on 2008-02-29
Intriguing if that's how security fixes are incorporated into the ubuntu package.
It raises a minor annoyance for those dual-booters sharing a profile between ubuntu & windows: if the Tb version numbers aren't the same then it has to check add-on compatibility every time on opening Tb in one OS after having opened it in the other OS.

---

### Post by NJC on 2008-02-29
> **febrile said:**
> 
It raises a minor annoyance for those dual-booters sharing a profile between ubuntu & windows: if the Tb version numbers aren't the same then it has to check add-on compatibility every time on opening Tb in one OS after having opened it in the other OS.

Always wondered why that happens.

---

### Post by Foster Grant on 2008-02-29
The Update Manager gave me Thunderbird 2.0.0.12 today, some time after it was released.

---

