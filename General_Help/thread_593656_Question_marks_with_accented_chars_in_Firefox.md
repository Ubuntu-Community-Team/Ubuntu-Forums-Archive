---
title: "Question marks with accented chars in Firefox"
date: 2007-10-27
forum: General Help
---

### Post by Majorix on 2007-10-27
Hi!
In Firefox, with some sites, I get question marks instead of accented characters and sometimes quotes (I think). There is a black diamond shape with a ? in the center of it instead of the character it was supposed to show.

On Windows, there is no problems using FF2.0.0.8 with the same sites.

And like I said, the very same characters display fine under some other sites.

I followed the suggestions in [this]("http://ubuntuforums.org/showthread.php?t=254598") and [this]("http://ubuntuforums.org/showthread.php?t=312905") thread to no avail.

Please help if you can. Thanks!

---

### Post by TidusBlade on 2007-10-27
I get the same thing too, I think Ubuntu cant read that language or it dosen't know what it is so it gives out the diamond.

---

### Post by Majorix on 2007-10-27
No fixes though?

---

### Post by Majorix on 2007-10-28
Anybody?

---

### Post by RIchard James13 on 2008-01-23
I found that if you change the character encoding to Western (ISO-8859-1) it fixes the problem.

Find it under View->Character Encoding->More Encodings->West European->Western (ISO-8859-1)

It seems Firefox is using Unicode UTF8

---

### Post by Majorix on 2008-01-24
I have it set to Western however it still won't quit it with those Q marks. And yes, sadly the problem is still there......

---

### Post by erginemr on 2008-01-24
Hi,

Normally, you should see almost all pages with no font problems as Firefox supports all major languages. Generally speaking, UTF8 supports many encodings and ISO-9959-9 is, as you may also know, for Turkish.

Can you please post here the addresses of the sites where you are having viewing problems, so that I can check with my browser to see if this is domething related to Firefox or to your system only?

---

### Post by Majorix on 2008-01-24
The problem occurs on my univ's students site for example. That page requires you to be a student, so not sure if you can view it.

Other than that, there was a page this morning but now when I google for it there aren't any results. Very, very odd.

I will be on the look-out for any links though, so will let you know.

---

### Post by erginemr on 2008-01-24
I see. Knock yourself out... 

Meanwhile, you may consider installing another browser, say "epiphany" or "opera", and visit this problematic site, just to cross-check whether this problem is firefox-specific or system-wide.

---

### Post by hal736 on 2008-04-15
I found that if you only use the Western((ISO-8859-1) from the list found in View-Character Encoding,   you will still get the question mark-diamond.  However, when I used View-Character Encoding-More Encodings-West European-Western((ISO-8859-1),  the question mark-diamond disappeared.  Sounds weird, I know. It may be a bug in Mozilla. but I haven't checked yet.
Hope this works for you.  YMMV.

---

