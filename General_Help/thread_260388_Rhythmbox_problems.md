---
title: "Rhythmbox problems"
date: 2006-09-18
forum: General Help
---

### Post by osotogari on 2006-09-18
Hey all,
Rhytmbox was working perfectly until I had my server break down on me, I was sharing my music from the server on the network, now whenever i try to run Rhytmbox it crashes after a few moments. I ran it from the terminal with the -d option and it seems that Rhytmbox is trying to load files from the server which doesnt exist anymore and as a result crashes when it cant find these files. Does anyone know of a workaround for this? Is there a way to clear my library in Rhytmbox so when it runs it won't go looking for these files?

Thanks

---

### Post by Harold P on 2006-09-18
In order to clear your playlist run the following:

```
rm -rf ~/.gnome2/rhythmbox/*
```

Hope it works. 

:]

---

### Post by osotogari on 2006-09-18
that seems to have done the job, thanks man! :)

---

### Post by Harold P on 2006-09-18
Just to explain what that did:

It cleared the saved library xml files "playlists.xml" and "rhythmdb.xml", which is where your tracks and such are kept, 

Glad it worked. :]

---

### Post by osotogari on 2006-09-18
Thanks for the explanation and thanks again for the help!

---

