---
title: "[SOLVED] Locales problem (LC_ALL hates en_US)"
date: 2007-08-06
forum: General Help
---

### Post by MarkusRTK on 2007-08-06
So a while ago I got hit by some filesystem corruption -- saved by fsck, though not after a great deal of panic -- and on coming back I noticed that my locales had somehow gotten screwed up. 

For the life of me I can't make Linux accept LC_ALL=en_US.utf8 (or any variation thereof -- just en_US, en_US.utf-8, en_US.UTF-8, with or without quotes, etc).  It insists that [highlight]locale: Cannot set LC_ALL to default locale: No such file or directory[/highlight] and then, of course, Perl plotzes and certain applications don't run.

Doing dpkg-reconfigure locales has been no help, and I've reinstalled all the pertinent languagepacks; nothing. What really gets me is that if I set the locale to something nonexistent, the error is different than this one (in addition to LC_ALL, LC_MESSAGES and one other one also display errors). So why is it just LC_ALL that has a problem with en_US?

I can get around it fine by just setting LC_ALL="C", or using any other locale -- right now I'm on Canadian English (en_CA.utf8 ). But dates in programs like Thunderbird aren't quite right in either of these, and besides it bothers me that my locale would just suddenly stop working. Is it possible that my en_US was corrupted during that fsck incident, and if so, how do I fix that? Alternately, what else can I try?

Thanks in advance for any suggestions

---

### Post by ayoli on 2007-08-06
you may want to try this :
```
sudo dpkg-reconfigure -phigh locales 
```

---

### Post by MarkusRTK on 2007-08-06
Nope, same story; dpkg-reconfigure doesn't seem to be modifying the en_US locale, or at least addressing the problem. Thanks though. Other ideas?

---

### Post by MarkusRTK on 2007-08-09
Update: Solved it, after taking the rather obvious step of renaming the old en_US directory (in /usr/lib/locales) and then doing *dpkg-reconfigure locales*, which forced it to regenerate en_US fresh. Locale worked perfectly after that.

I'm assuming there was some kind of corruption or something in the preexisting en_US files, that for whatever reason wasn't getting replaced by dpkg-reconfigure. Whatever. Thanks again ayoli for your help.

---

