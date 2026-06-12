---
title: "US international (with dead keys) and double quotes"
date: 2013-02-22
forum: General Help
---

### Post by Sandertje on 2013-02-22
Dear people,

Since time immemorial I have been using US International (with dead keys) as keyboard layout. This is convenient for me, as I tend to write in multiple languages - some of which feature all the nice ä,ö,ü,ë,é etc etc. Up till now I have never run into issues, but now I've hit some kind of problem.

In nearly all software, whenever I hit the apostrophe/double quote button I do get an apostrophe(') or double quote(") after I hit space. But now, some IDEs (RStudio, Intellij IDEA) display ´ or ¨ whenever I try to type quotes.

I looked up the keyboard layout, and it seems like this is expected behavior, in the sense that normal quotes should be the third shift level (i.e., reachable by using the right alt). But then, I wonder, why does most software ignore this, and display normal quotes without having to hit the right alt? 

That said, is there a keyboard layout where I will always type normal quotes (without hitting right alt), but still retain the niceties of US international? 

I do use IBUS to occasionally switch to Anthy, could this be of influence?

I am using Ubuntu 12.04 LTS.

---

### Post by zhaozhou on 2013-02-22
Is "setxkbmap us -variant intl" what you are looking for?

---

### Post by Sandertje on 2013-02-22
No. I already have that. However, this produces ´ and ¨ whenever I want to type ' and " in some software.

---

### Post by gdmellott on 2014-02-08
You like want just the US keyboard.  Drop everthing after 'us' will likely work.

I've wondered what was going on for a ling time myself as the default setup choice that comes from testing test in setup chooses the us internatonal keyboard.
I'll add that from what I've exprienced today you will need to remember the "setxkbmap us" command as every time you restart the OS it will be reverted back
to the us international version.

Sincerely, gdm

---

