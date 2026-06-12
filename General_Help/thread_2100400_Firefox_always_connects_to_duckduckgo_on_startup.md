---
title: "Firefox always connects to duckduckgo on startup"
date: 2013-01-01
forum: General Help
---

### Post by bobnn on 2013-01-01
Ubuntu and Lubuntu 11.10 Firefox 17.01.

This happens in a fresh profile and even in safe-mode.

Startpage and homepage set to blank.

Does not happen on firefox 17.01 on Windows 7.

Packet traces shows DNS query for duckduckgo.com, then a TCP connection is made, then a few seconds later it is terminated.

No data is apparently exchanged, unless something is being done w/ sequence number or timestamp options or some such - which I doubt.

The browser window itself is blank.

Does anybody know why this is happpening?

---

### Post by orb9220 on 2013-01-01
Ok if wanting to change default search just go here.
[http://www.linuxmint.com/searchengines.php](http://www.linuxmint.com/searchengines.php)
It was what I used to change to Google default search

Scroll down and click on google as an example.
Then go to search bar and select manage search engines.
.

---

### Post by bobnn on 2013-01-01
> **orb9220 said:**
> Ok if wanting to change default search just go here.
.

Been there, done that.  Default is google.

---

### Post by brainwash on 2013-01-02
Blocking these suspicious connections is not an option? Looks like nobody knows why Firefox has to check duckduckgo on startup.

---

### Post by zacbrannigan on 2013-01-02
Hey all, Zac from DuckDuckGo here. We're trying to get to the bottom of this so if you have any updates--feel free to drop them here and we'll try to respond as often as possible. 

Thanks!

---

### Post by bobnn on 2013-01-02
Zac: 

Interesting that you're here and haven't (yet) an answer.  

I know that this is off topic for this forum, but: Firefox on Centos6 10.0.0.11 - real old - and IceWeasel on the latest Knoppix DVD - also very old, 10.something - do not do this.

---

### Post by bobnn on 2013-01-02
> **brainwash said:**
> Blocking these suspicious connections is not an option? Looks like nobody knows why Firefox has to check duckduckgo on startup.

The connections don't bother me that much, since no data is sent or received.  I just want to know why it's doing that - and who put that in and *where*.

---

### Post by chadk5utc on 2013-01-02
if changing it in your browser preferences didnt resolve it? did you save your setting in "The Cloud" anonymously? if not then its more than likely something installed so I would look at plugins or extensions and java. 
try pressing Ctrl+Shift+Del then a box pops up set it to clear all cookies/cache Etc

---

### Post by zacbrannigan on 2013-01-03
Posted the same question here: [https://support.mozilla.org/en-US/questions/945830#answer-393752](https://support.mozilla.org/en-US/questions/945830#answer-393752) 

Response: 

Do you have any pages bookmarked (e.g. feed items) that may be causing this? 
Did you use a reset to get the new profile or did you use the Profile Manager with a really clean profile? 
 
[LIST]
[*][http://kb.mozillazine.org/Profile_Manager](http://kb.mozillazine.org/Profile_Manager)
[*][https://support.mozilla.org/kb/Managing+profiles](https://support.mozilla.org/kb/Managing+profiles)
[/LIST]




^^sorry for cross-streaming forums.

---

### Post by brainwash on 2013-01-03
So I upgraded Ubuntu from 11.10 to 12.04 and suprisingly Firefox doesn't connect to duckduckgo on startup anymore.

---

### Post by zacbrannigan on 2013-01-05
Thanks! Please let us know if anyone else is still seeing this issue.

---

