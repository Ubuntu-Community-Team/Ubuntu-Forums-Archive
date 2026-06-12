---
title: "Remove words shorter than 8 Characters"
date: 2008-06-28
forum: General Help
---

### Post by m994301009 on 2008-06-28
How could I remove all the words shorter than 8 characters long from a massive word list. Is there a way to do this in the default "Text Editor" or would I need a different program?

---

### Post by ConMan318 on 2008-06-28
I'm sure you could do it with a BASH script, but I don't know how off the top of my head.  I do know how to do it very easily in python, though.  I'd have to know how the words are seperated, i.e. are they seperated by spaces?

---

### Post by m994301009 on 2008-06-28
They are separated by newlines, AFAIK.

---

### Post by ghostdog74 on 2008-06-28
this is very simple.
```

 awk 'length > 7' file

```
also try read up the bash manual in my sig when you are free

---

### Post by m994301009 on 2008-06-28
Thanks! That worked perfectly, now time to compute my massive WPA hash file. :) (If I can get my program to compile. Make says that 'DLT_IEEE802_11_RADIO’ is undefined, and I can't seem to fix it.)

EDIT: Isn't there a way to mark this post as solved and thank you guys or something? I remember doing it somehow before, but I can't seem to find an option for it now.

---

### Post by ConMan318 on 2008-06-29
To mark as sovled, to to "Thread tools" written in red near the top of the page and then click "mark as solved".  To give thanks, just click the star thing at the bottom right of a user's post.

And nice link ghostdog, as I have been needing to learn some Bash other than simple stuff.

---

