---
title: "Flock and flash-related crashing under Edgy"
date: 2006-10-31
forum: General Help
---

### Post by Flamekebab on 2006-10-31
I've recently upgraded to Edgy and apart from a few issues, things are just fine and dandy.

I've done the fix thing on Firefox (modifying /etc/firefox/firefoxrc) and it works just fine. However, I have no idea where to find the corresponding file for *Flock*, my browser of choice (based on Firefox).

Could anyone provide any help?

Please?

I'll give you chocolate..

---

### Post by Flamekebab on 2006-10-31
Nice to see my thread is already at the bottom of the page and descending rapidly with no sign of help in sight!

---

### Post by jpmorelli on 2006-10-31
I think I have the same problem, someone can help ?](*,)

---

### Post by Flamekebab on 2006-11-01
I think I've fixed it, with a little help from hikaricore in [this post]("http://ubuntuforums.org/showpost.php?p=1696115&postcount=26").

If you've got Flock installed in /opt/flock, as I have, you can do the following, I think:

```
sudo gedit /opt/flock/flock
```

Find the line that says..
```
export MOZ_PIS_API MOZ_PIS_MOZBINDIR MOZ_PIS_SESSION_PID MOZ_PIS_USER_DIR
```
..and change it to..
```
export MOZ_PIS_API MOZ_PIS_MOZBINDIR MOZ_PIS_SESSION_PID MOZ_PIS_USER_DIR XLIB_SKIP_ARGB_VISUALS=1
```

That seems to be working for me, although I don't want to count my chickens, so to speak!

---

### Post by jpmorelli on 2006-11-01
Thank you Flamekebab, that fix did work for me ! :D

---

