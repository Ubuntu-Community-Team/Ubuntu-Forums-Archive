---
title: "why no forefox 54.0.1?"
date: 2017-07-25
forum: General Help
---

### Post by missmoondog on 2017-07-25
why am i not getting firefox updated to version 54.0.1, which has been out for a good while now, on any of my linux computers? both my windows computers got the update and my tablet and even my phone!!

thank you

---

### Post by vasa1 on 2017-07-25
> **missmoondog said:**
> why am i not getting firefox updated to version 54.0.1, which has been out for a good while now, on any of my linux computers? both my windows computers got the update and my tablet and even my phone!!

thank you
I'm guessing there may be some technical difficulties. The [release notes for 54.0.1]("https://www.mozilla.org/en-US/firefox/54.0.1/releasenotes/") do indicate changes that affect Linux users. Sometimes, when a minor release doesn't affect Linux users, there isn't a release for Linux users but that isn't the case this time.

BTW, I have Firefox 54.0.1 but I get mine direct from Mozilla.

Meanwhile,```
$ apt policy firefox
firefox:
  Installed: (none)
  Candidate: 54.0+build3-0ubuntu0.16.04.1
  Version table:
     54.0+build3-0ubuntu0.16.04.1 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     45.0.2+build1-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
$ 
```

---

### Post by col48 on 2017-07-25
My tuppence worth...
I have 64bit Ubuntu rather than Lubuntu but I too have Firefox 54.0 (not 54.0.1) which replaced 53.0.3 according to the Changelog.
For me, apt policy firefox gives exactly the same info as vasa1 in post #2 except that the Installed info is the same as the Candidate info.
I think it came to me in mid-June 2017 from the software centre.

---

### Post by walts48 on 2017-07-26
I guess nobody is having a problem with Netflix, which is one of the items in the release notes.

> Fix a Netflix issue on Linux

Most likely there is no 54.0.1 because there weren't any security vulnerabilities fixed.

[https://www.mozilla.org/en-US/security/known-vulnerabilities/firefox/](https://www.mozilla.org/en-US/security/known-vulnerabilities/firefox/)

---

