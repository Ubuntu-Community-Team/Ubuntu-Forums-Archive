---
title: "Non-printable .PDFs"
date: 2006-11-27
forum: General Help
---

### Post by 0815user on 2006-11-27
Today I found a pdf containing non printable content. Despite the fact that there is no real reason to set "security" features of a pdf to not printable - you can always convert it using standard poppler tools, it really offends my "it's a matter of free speech and free beer"-attitude.

You can't distribute a document and really think you are the one to decide if others print it - that's DRM and we all do hate it, right?


Well, anyways, I found out, that evince in fact disables "print" when I open that pdf. Therefore the small and only question: "Why?".

---

### Post by cilynx on 2006-11-27
Because it's in the spec.  The goal of evince (and every other respectable project) is to impliment the public specification for what it does, not to make happy users by picking and choosing which parts to use and which not to.  Choosing what is easily printable and what is not is indeed DRM, but it is also a part of the PDF specification, so evince impliments it.

---

### Post by 0815user on 2006-11-27
> **cilynx said:**
> Because it's in the spec.

Ah. Ok. So "implementing specifications" overrides "do useful stuff".

EDIT: Ok, let's say, I found the right spot in sourcecode to look for such "features"....

---

### Post by cilynx on 2006-11-27
It all depends on what you consider "useful stuff".  If you wrote a document that you need some people to see, but you don't want any Joe User to be able to run off hardcopy, then disabling print is quite "useful stuff".  Ubuntu, as a corporately sponsored distribution, has the responsibility to play by the corporate rules and do their best to fully impliment the specifications that they are claiming support for.  To do anything else would be unethical.  As you came to find, the cool part of Open Source is that you can go into any application you like and hack up the features you (don't) want.  It's not Ubuntu's responsibility to make sure you're happy.  It's their responsibility to make sure that their paying customers are happy.  They're doing what they want with Open Source.  You're doing what you want.  That's the fantastic part.

---

