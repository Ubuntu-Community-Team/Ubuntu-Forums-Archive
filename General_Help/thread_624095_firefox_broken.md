---
title: "firefox broken"
date: 2007-11-26
forum: General Help
---

### Post by tubunu on 2007-11-26
After doing a fast user switching and then suspend and wake up, I found that my firefox doesn't want to start. 
I uninstalled it, then tried installing again, nothing. Then update manager tells me to do **apt-get install -f** and here's what I get with that:

```
:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  firefox
Suggested packages:
  firefox-gnome-support latex-xft-fonts
Recommended packages:
  ubufox
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
[COLOR="Red"]1 not fully installed or removed.[/COLOR]
Need to get 0B/9183kB of archives.
After unpacking 26.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 98472 files and directories currently installed.)
Unpacking firefox (from .../firefox_2.0.0.8+2nobinonly-0ubuntu1_i386.deb) ...
[COLOR="Red"]dpkg: error processing [/COLOR]/var/cache/apt/archives/firefox_2.0.0.8+2nobinonly-0ubuntu1_i386.deb (--unpack):
[COLOR="Red"] unable to make backup link of `./usr/lib/firefox/libxpcom_core.so' before installing new version: Operation not permitted[/COLOR]
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_2.0.0.8+2nobinonly-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Fellow *buntu geeks, please help me out. Thank you.

---

### Post by retrow on 2007-11-26
Perhaps firefox is still running in the background.

Go to Administration > System Monitor and under processes check if you see if firefox is running. If it is, you need to kill that process and then restart firefox. If there was something wrong in the previous session, it would be a bad idea to "Restore session". My advice would be to start a New Session.

---

### Post by tubunu on 2007-11-26
Ummm, no, firefox isn't running under system monitor. But I'm typing this from Iceape. Should that matter?

---

### Post by tubunu on 2007-11-26
Here's the output from Synaptic:
```
E: /var/cache/apt/archives/firefox_2.0.0.8+2nobinonly-0ubuntu1_i386.deb: unable to make backup link of `./usr/lib/firefox/libxpcom_core.so' before installing new version
```

:?

---

