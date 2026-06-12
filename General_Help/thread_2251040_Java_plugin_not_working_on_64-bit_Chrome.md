---
title: "Java plugin not working on 64-bit Chrome?"
date: 2014-11-01
forum: General Help
---

### Post by user1397 on 2014-11-01
Has anyone had luck getting java applets to run in 64-bit google **chrome** (not chromium)?  I tried the instructions [here]("https://www.java.com/en/download/help/enable_browser_ubuntu.xml") as well (symlinks icedtea plugin to chrome plugins folder) to no avail.

Icedtea plugin also does not appear in the plugins section of chrome settings.  Also, java plugin is working fine on firefox.

Running 64bit ubuntu 14.04 unity with openjdk-7 and icedtea-plugin-7.

---

### Post by bashiergui on 2014-11-02
According to this, Firefox is the preferred browser. Doesn't look like it works in Chrome according to Oracle. 
[https://www.java.com/en/download/faq/chrome.xml](https://www.java.com/en/download/faq/chrome.xml)

---

### Post by Cavsfan on 2014-11-02
Install java via the link in my signature. It uses Web Upd8's ppa and keeps it up to date.
You can also check the version via the other (red) link.

You'll also want to install default-jre as well.

---

### Post by Cavsfan on 2014-11-02
This might help if the other doesn't work.
[https://www.java.com/en/download/help/enable_browser_ubuntu.xml](https://www.java.com/en/download/help/enable_browser_ubuntu.xml)

Here's the link for installing pepper flash too in case you're interested.

[http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html](http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html)

---

### Post by user1397 on 2014-11-02
> **bashiergui said:**
> According to this, Firefox is the preferred browser. Doesn't look like it works in Chrome according to Oracle. 
[https://www.java.com/en/download/faq/chrome.xml](https://www.java.com/en/download/faq/chrome.xml)Yea I saw that too...maybe it just doesn't work with chrome/chromium anymore

> **Cavsfan said:**
> Install java via the link in my signature. It uses Web Upd8's ppa and keeps it up to date.
You can also check the version via the other (red) link.

You'll also want to install default-jre as well.How would that fix the problem though? I believe the problem lies with the deprecation of the NPAPI plugin in chrome/chromium therefore I don't think java applets run at all anymore?

> **Cavsfan said:**
> This might help if the other doesn't work.
[https://www.java.com/en/download/help/enable_browser_ubuntu.xml](https://www.java.com/en/download/help/enable_browser_ubuntu.xml)

Here's the link for installing pepper flash too in case you're interested.

[http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html](http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html)That first link is the one I linked in the original post.  And I'm talking about chrome not chromium so flash is already included.

---

