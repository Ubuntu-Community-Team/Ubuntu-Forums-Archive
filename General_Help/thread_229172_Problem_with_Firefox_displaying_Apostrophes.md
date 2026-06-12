---
title: "Problem with Firefox displaying Apostrophes"
date: 2006-08-04
forum: General Help
---

### Post by jeff_ on 2006-08-04
It seems firefox is having trouble displaying certain apostrophes, for example in news headlines on googles personalized homepage or in rss feeds. Instead of the apostrophe it displays a square box with what looks like 0 0 on top and 9 2 on the bottom. I'll post a screen shot if need be. Thanks --Jeff

---

### Post by shirizaan on 2006-08-10
I am also experiencing this issue.  Any assistance would be appreciated.

---

### Post by steve.horsley on 2006-08-10
The value 0x0092 is not a valid character code in either unicode or in ISO-8859-1. What characterset does the page **claim** to be using? It should be in tthe headers if you view the page source.

---

### Post by shirizaan on 2006-08-10
UTF-8

I have tried switching to other charsets and it still has the same problem though D:

---

### Post by jeff_ on 2006-08-10
Firefox doesn't even seem to let me change the character encoding. Google, which is the main page I have a problem with claims to be using UTF-8.

---

### Post by steve.horsley on 2006-08-11
Firefox has a menu View->Character Encoding that may help viewing a page, but as I say, 0092 (decimal 146) is not a printable character code in utf8 or in many other charactersets. This is not a firefox bug, its a bug in those web sites. Firefox is correctly telling you that this character code is not printable, here is the hex value instead.

---

### Post by shirizaan on 2006-08-11
You're correct, it may not be a bug with Firefox.  My Windows computer (running Firefox) does not have this issue.  In addition to that, we're talking about Google's website being one of the affected sites.

---

### Post by jeff_ on 2006-08-11
Yes, I don't believe it to be a bug with firefox since I get it with various other apps such as RSS feeds and the pages source itself. I suppose it may be a problem with Google in which case it should be taken up with them.

---

