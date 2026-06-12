---
title: "Help me move a file."
date: 2012-10-26
forum: General Help
---

### Post by ManyBeers on 2012-10-26
I would like help on how to move file on desktop=test.wav
to /usr/share/skype/sounds.

---

### Post by codemaniac on 2012-10-26
> **ManyBeers said:**
> I would like help on how to move file on desktop=test.wav
to /usr/share/skype/sounds.

just open up a terminal and paste the following.

```
mv ~/Desktop/test.wav /usr/share/skype/sounds
```

---

### Post by ManyBeers on 2012-10-26
> **codemaniac said:**
> just open up a terminal and paste the following.

```
mv ~/Desktop/test.wav /usr/share/skype/sounds
```

Thanks. I actually figured it out by cding to Desktop and using this
sudo mv -i test.wav -t /usr/share/skype/sounds.

---

