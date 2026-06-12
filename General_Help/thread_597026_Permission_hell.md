---
title: "Permission hell"
date: 2007-10-30
forum: General Help
---

### Post by thepocketdrummer on 2007-10-30
Ok. At this point, this OS is useless to me. I can't get help anywhere and I can hardly do anything without hitting a brick wall.

I'm trying to follow the instructions [HERE]("http://forums.gentoo.org/viewtopic-t-587921.html"), but it's hard to follow and none of the lines of code seem to work.

Then, after hopeless attempt to get my X-Fi to work I decide to delete the stupid folders. But, when I try to empty my recycle bin, it won't let me..... because I don't have "permission". Is there any GUI method to get this done, or do I really have to go back to the terminal to simply delete a file....

Sorry if I sound pissed, but I want an OS I can use and so far, it's not cutting it.

---

### Post by Botondus on 2007-10-30
Are you using sudo command? You shouldn't have any permission problems with that.
And if for some reason sudo doesn't let you to do something you can activate root terminal (be careful though):

```
sudo -s -H
```

---

### Post by thepocketdrummer on 2007-10-30
> **Botondus said:**
> Are you using sudo command? You shouldn't have any permission problems with that.
And if for some reason sudo doesn't let you to do something you can activate root terminal (be careful though):

```
sudo -s -H
```

Thank you Botondus. You're the first person to respond to any of my posts in the past 3 days.

What does this code do? Does it unlock the files in the recycle bin or do I type that, then type the location of the file I want to delete?

---

