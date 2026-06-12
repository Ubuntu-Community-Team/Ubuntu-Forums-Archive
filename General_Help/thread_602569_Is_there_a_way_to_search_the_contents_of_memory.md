---
title: "Is there a way to search the contents of memory?"
date: 2007-11-04
forum: General Help
---

### Post by Endolith on 2007-11-04
Is there a way to dump the contents of memory and swap space in order to search through it for plain text?

Like I just accidentally reloaded a web page, forgetting that I had entered a bunch of text into a text area and losing my work.  Obviously Firefox should just never let you lose data, but regardless, I know the text is still in memory somewhere, so I should be able to search for a key word and copy and paste it back into an application so it isn't lost.   Is there a way to do that?  cat | grep some /dev/ file or something?

---

### Post by kellemes on 2007-11-04
When you reload a page, you should be able to go back to the previous page (with content) using your "previous page"-button. In most cases anyway..
Firefox has nothing to do with this by the way.. it all depends on how the page is coded..
How to search memory? I don't know.

---

### Post by pismikrop on 2007-11-04
cat /dev/mem|grep -a "your text"

---

### Post by Endolith on 2007-11-04
> **kellemes said:**
> When you reload a page, you should be able to go back to the previous page (with content) using your "previous page"-button. In most cases anyway..

Not when you press reload, and not if the page is more than just HTML.
> **pismikrop said:**
> cat /dev/mem|grep -a "your text"

Heh.  That finds the HTML of your post in Firefox's memory.  :-)  It also spits out a lot of other stuff, though, which doesn't match the search.  How do I prevent that?

Also it says "cat: /dev/mem: Bad address" at the end.

Also you need to preface sudo

---

