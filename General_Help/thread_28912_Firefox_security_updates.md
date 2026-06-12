---
title: "Firefox security updates"
date: 2005-04-22
forum: General Help
---

### Post by dsan on 2005-04-22
Is it me, or is there no official ubuntu update for the recent mozilla/firefox security issues?

---

### Post by heimo on 2005-04-22
To my understanding, security updates which came with Firefox 1.0.3 have been fixed and backported to 1.0.2:
 
Discussion about this subject:
[http://ubuntuforums.org/showthread.php?t=28469&highlight=firefox+1.0.3]("http://ubuntuforums.org/showthread.php?t=28469&highlight=firefox+1.0.3")
 
Changelog of Hoary mozilla-firefox package:
[http://packages.ubuntu.com/changelogs/pool/main/m/mozilla-firefox/mozilla-firefox_1.0.2-0ubuntu5/changelog]("http://packages.ubuntu.com/changelogs/pool/main/m/mozilla-firefox/mozilla-firefox_1.0.2-0ubuntu5/changelog")
 
Quote from changelog:
```
   
mozilla-firefox (1.0.2-0ubuntu5) hoary; urgency=low

  * Ensure default homepage is correct (US only) (Ubuntu: #8685)
  * Low risk fix for crasher caused by dragging images (Moz: #288006)
  * Trivial fix to make sidebar bookamrks work properly again (Moz: #287459)
	(The combination of the two above bugs is to give us the important bits of 
	Firefox 1.0.3)
  * Fix defaults/pref harder

-- Thom May <thom@ubuntu.com>  Tue,  5 Apr 2005 18:20:21 +0100


```

---

### Post by nocturn on 2005-04-22
[QUOTE=heimo]To my understanding, security updates which came with Firefox 1.0.3 have been fixed and backported to 1.0.2:
 
Discussion about this subject:
[http://ubuntuforums.org/showthread.php?t=28469&highlight=firefox+1.0.3]("http://ubuntuforums.org/showthread.php?t=28469&highlight=firefox+1.0.3")
 
Changelog of Hoary mozilla-firefox package:
[http://packages.ubuntu.com/changelogs/pool/main/m/mozilla-firefox/mozilla-firefox_1.0.2-0ubuntu5/changelog]("http://packages.ubuntu.com/changelogs/pool/main/m/mozilla-firefox/mozilla-firefox_1.0.2-0ubuntu5/changelog")
 
Quote from changelog:
```
   
mozilla-firefox (1.0.2-0ubuntu5) hoary; urgency=low

  * Ensure default homepage is correct (US only) (Ubuntu: #8685)
  * Low risk fix for crasher caused by dragging images (Moz: #288006)
  * Trivial fix to make sidebar bookamrks work properly again (Moz: #287459)
	(The combination of the two above bugs is to give us the important bits of 
	Firefox 1.0.3)
  * Fix defaults/pref harder

-- Thom May <thom@ubuntu.com>  Tue,  5 Apr 2005 18:20:21 +0100


```[/QUOTE]

AFAIK, Ubuntu-Firefox still has the javascript flaw... I should test to make sure though.

---

### Post by heimo on 2005-04-22
[QUOTE=nocturn]AFAIK, Ubuntu-Firefox still has the javascript flaw... I should test to make sure though.[/QUOTE]
 
Ok. 
 
Fixed in Firefox 1.0.3 (vanilla)
```
 
[MFSA 2005-33]("http://www.mozilla.org/security/announce/mfsa2005-33.html")[url="http://www.mozilla.org/security/announce/mfsa2005-33.html"] Javascript "lambda" replace exposes memory contents
[/url][MFSA 2005-34]("http://www.mozilla.org/security/announce/mfsa2005-34.html")[url="http://www.mozilla.org/security/announce/mfsa2005-33.html"] javascript: PLUGINSPAGE code execution
[/url][MFSA 2005-35]("http://www.mozilla.org/security/announce/mfsa2005-35.html")[ Showing blocked javascript: popup uses wrong privilege]("http://www.mozilla.org/security/announce/mfsa2005-33.html")
context
[MFSA 2005-36]("http://www.mozilla.org/security/announce/mfsa2005-36.html")[url="http://www.mozilla.org/security/announce/mfsa2005-33.html"] Cross-site scripting through global scope pollution
[/url][MFSA 2005-37]("http://www.mozilla.org/security/announce/mfsa2005-37.html")[url="http://www.mozilla.org/security/announce/mfsa2005-33.html"] Code execution through javascript: favicons
[/url][MFSA 2005-38]("http://www.mozilla.org/security/announce/mfsa2005-38.html")[url="http://www.mozilla.org/security/announce/mfsa2005-33.html"] Search plugin cross-site scripting
[/url][MFSA 2005-39]("http://www.mozilla.org/security/announce/mfsa2005-39.html")[url="http://www.mozilla.org/security/announce/mfsa2005-33.html"] Arbitrary code execution from Firefox sidebar panel II
[/url][MFSA 2005-40]("http://www.mozilla.org/security/announce/mfsa2005-40.html")[url="http://www.mozilla.org/security/announce/mfsa2005-33.html"] Missing Install object instance checks
[/url][MFSA 2005-41]("http://www.mozilla.org/security/announce/mfsa2005-41.html")[ Privilege escalation via DOM property overrides]("http://www.mozilla.org/security/announce/mfsa2005-33.html")

``` 
 
 
The lambda is fixed:
* Apply patch from moz: 288688; Ubuntu: 8611
JS "lambda" replace exposes malloc heap space after end of JS string
 
If I understand, this has been fixed in Hoary, but not in Warty:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=4679]("https://bugzilla.ubuntu.com/show_bug.cgi?id=4679")
 
These are critical and still open (patches available):
[https://bugzilla.ubuntu.com/show_bug.cgi?id=9926]("https://bugzilla.ubuntu.com/show_bug.cgi?id=9926")
[https://bugzilla.ubuntu.com/show_bug.cgi?id=9927]("https://bugzilla.ubuntu.com/show_bug.cgi?id=9927")
 
This is critical, open and not fixed in 1.0.3? :
[https://bugzilla.ubuntu.com/show_bug.cgi?id=9928]("https://bugzilla.ubuntu.com/show_bug.cgi?id=9928")
 
 
So yes, it seems that there are some patches in 1.0.2, but some are missing. :|

---

### Post by nocturn on 2005-04-26
I just tested a proof-of-concept page.

The javascript vuln. allows reading and writing files in your home directory.  Very concerning.

---

