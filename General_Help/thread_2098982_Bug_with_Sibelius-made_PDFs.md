---
title: "Bug with Sibelius-made PDFs"
date: 2012-12-28
forum: General Help
---

### Post by DavidSommen on 2012-12-28
Since the moment I upgraded to 12.10 (when it just got officially released), I have this problem on ubuntu reading pdfs made from Sibelius (on Mac OS X 10.6.8 on my macbook). The pdfs are rendered so badly that they are not readable, no note heads, no lyrics, and so on. Only in Okular (KDE pdf reader), this problem does not occur at all. In Evince, GIMP, PDF Shuffler, and so on, the pdf doesn't render right.

All my screenshots and files and more explanation you can find on this bug report:

[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/1067091](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/1067091)

I just want to know if you also experience this bug (all you have to do is check if the files render correctly or not on your system (in Evince or another program).

Nothing changed in Sibelius. When I was running 12.04 this was not a problem. So what has changed?

Thanks!

---

### Post by Lars Noodén on 2012-12-28
Edit- never mind

---

### Post by audiomick on 2012-12-28
I picked up the pdf file off the bug report site you linked to. Looks ok to me. I'm on 11.10 here, and I opened it with the standard image viewer. Evince? I think so...

---

### Post by DavidSommen on 2012-12-28
Yes, but you're on 11.10. Up to 12.04 it worked perfectly for me. The problem began when I installed 12.10...

---

### Post by audiomick on 2012-12-28
> **DavidSommen said:**
>  The problem began when I installed 12.10...

Ah, yes. You did say that in your post. Sorry, wasn't concentrating, I guess...

---

### Post by DavidSommen on 2012-12-29
> **audiomick said:**
> Ah, yes. You did say that in your post. Sorry, wasn't concentrating, I guess...

No problem :)

---

### Post by DavidSommen on 2012-12-31
Any ideas? (bump)

---

### Post by DavidSommen on 2013-01-06
I'd just like to know whether this problem occurs only on my system, or whether it is a general bug...

---

### Post by DavidSommen on 2013-02-05
Can someone please check with the provided attachments? I'd like to know whether my system is to blame, or whether it is a general bug.

---

### Post by Lars Noodén on 2013-02-05
I looked at the [PDF file](https://launchpadlibrarian.net/119822176/Ik%20wou%20een%20zwarte%20kater.pdf) that you attached to the bug report.  It renders fine for me in Document Viewer on Lubuntu 13.04a.  So I am unable to help there because I cannot duplicate the bug.

---

### Post by DavidSommen on 2013-02-05
Thanks. This might mean that a) only my system is to blame or b) the bug is fixed in 13.04...

---

### Post by Impavidus on 2013-02-06
It looks fine in evince on 12.04. I suspect a font problem. All lines are rendered correctly, but all text and fixed-shape music symbols (probably a font too) are rendered incorrectly. All fonts are embedded in the pdf, but not usable by your evince. The only thing I can imagine, apart from a bug in your version of evince, is interference between the embedded fonts and (malformed) fonts with the same identifiers installed on your machine. None of them seem installed on my machine.

---

