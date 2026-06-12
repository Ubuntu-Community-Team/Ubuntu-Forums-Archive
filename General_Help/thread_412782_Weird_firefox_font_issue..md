---
title: "Weird firefox font issue."
date: 2007-04-18
forum: General Help
---

### Post by xopher on 2007-04-18
I don't know what could have caused this, today, after I restarted firefox, my fonts were all tahoma, and looked kinda weird.

I didn't alter any settings, install any new extensions or anything. Only thing I did was edit the ~/.mozilla/firefox/ejkfzpyw.default/mimeTypes.rdf, so that my .pdf's would 'Ask for action' - not just download by default. No idea why they started to act like that either by the way..

Still, I attached a screenshot of the problem.

Thanks.

---

### Post by xopher on 2007-04-18
Hehe, I obviously forgot I was playing around with my ~/.wine/c/windows/fonts directory, which is actually a link to ~/.fonts.

So the problem wasn't in firefox, it was in the user (as usual).

I had added tahoma.ttf, and firefox preferred that before any other fonts it seems. This has to be a rendering problem in firefox then I guess. Because, even though the font is a microsoft one, it should still render properly.

Thanks to you guys who had a look at my thread.

---

### Post by xopher on 2007-04-18
> **xopher said:**
> Hehe, I obviously forgot I was playing around with my ~/.wine/c/windows/fonts directory, which is actually a link to ~/.fonts.

So the problem wasn't in firefox, it was in the user (as usual).

I had added tahoma.ttf, and firefox preferred that before any other fonts it seems. This has to be a rendering problem in firefox then I guess. Because, even though the font is a microsoft one, it should still render properly.

Thanks to you guys who had a look at my thread.

Edit: And that too was fixed when I got the files: tahomab0.ttf and tahomabd.ttf, it seemed I didn't have a **bold** version of the font - so no wonder the text didn't render properly.
Edit2: Bah, can't even see the difference between 'Edit' and 'Quote' anymore, I guess it's time to go to bed. Good night!

---

### Post by earobinson on 2007-04-18
Thanks for the update.

---

