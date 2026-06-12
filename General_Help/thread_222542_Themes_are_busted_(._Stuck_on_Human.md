---
title: "Themes are busted :(. Stuck on Human"
date: 2006-07-25
forum: General Help
---

### Post by Jaymo on 2006-07-25
Hey all,
recently my themes have started acting strangely and it has driven me nuts :\.
No matter what theme I change to, the scrollbar, window border and the highlighted text colour remain orange.
I can't for the life of me figure out what's gone wrong, I've restarted gnome-settings daemon and even restarted my PC a few times to no avail.

Anyone had a similar problem? Any idea of how I can go about fixing it?

---

### Post by Dirhael on 2006-07-25
I had a similar problem a few days ago after installing the "gtk2-engines-gtk-qt" package. To solve it, just open a terminal and type: *rm ~/.gtk**

You might also want to remove that package if you have it installed.

---

### Post by Jaymo on 2006-07-25
edit: Ah ok, I'll give that a whirl in a sec :)
Here's a pic for those interested;
[IMG]http://digitalparamount.com/forumtrash/borkedtheme.png[/IMG]

---

### Post by Jaymo on 2006-07-25
I didn't have the specific package you mentioned but I uninstalled some unofficially supported engines and it all cleared up.
Cheers mate :D.

edit: I spoke too soon :\. Still having the same problem. Only the thumbnails changed.

---

### Post by Dirhael on 2006-07-25
> **Jaymo said:**
> I didn't have the specific package you mentioned but I uninstalled some unofficially supported engines and it all cleared up.
Cheers mate :D.

edit: I spoke too soon :\. Still having the same problem. Only the thumbnails changed.

Did you do this part:
```

rm ~/.gtk*

```

?

---

### Post by Jaymo on 2006-07-25
Ah yes, just did that and it fixed my initial problem.
However, now I don't have my ubuntu icon next to my Applications menu :O.

---

