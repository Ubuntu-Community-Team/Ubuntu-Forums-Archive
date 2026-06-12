---
title: "Mplayer to Open gl?"
date: 2008-05-13
forum: General Help
---

### Post by Kaneda187 on 2008-05-13
how do i set mplayer or movie player to open gl if possible! thanks in advance!

---

### Post by andrew.46 on 2008-05-13
Hi,

 Check if this is possible by running the following:

```
$ mplayer -vo help
```

and then if you see gl in the list try running:

```
$ mplayer -vo gl myfile.mpg
```

 Is this what you mean?

       Andrew

---

