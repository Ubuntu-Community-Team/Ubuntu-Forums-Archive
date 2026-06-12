---
title: "automate save-as in firefox?"
date: 2006-12-14
forum: General Help
---

### Post by geuis on 2006-12-14
not sure what exact forum to post this in, so I apologize in advance. :)

Does anyone reading this have any idea how I could automate webpage Save-as in Firefox/Mozilla?

What I'm exactly looking for is a command-line option that would let me pass a url to Firefox, and have it save it locally. 

I'm wanting to do this in Ubuntu because 1) I'm a linux fan, 2) Linux makes this kind of stuff easy, 3) someone else might have done this before.

Thanks guys,

Geuis

---

### Post by mcduck on 2006-12-14
I wouldn't do that with Firefox, as we already have great 'wget' to do exactly that kind of things ;)

see 'man wget' for more info.

---

### Post by geuis on 2006-12-14
wget doesnt fully support external stylesheets and CSS, such as background images. I've tried every which way w/ wget and its not everything I need.

---

### Post by mcduck on 2006-12-14
```
wget --convert-links -r http://www.gnu.org/
```

This way links inside pages should be converted so that CSS and pictures work just fine.

---

### Post by geuis on 2006-12-14
Sorry to disappoint. I've been banging on this problem for a couple months. Wget won't do it. Just ran your code again to make sure I didn't miss something. It completely ignores <link>

---

