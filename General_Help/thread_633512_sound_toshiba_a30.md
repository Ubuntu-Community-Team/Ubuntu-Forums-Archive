---
title: "sound toshiba a30"
date: 2007-12-06
forum: General Help
---

### Post by Jem00 on 2007-12-06
Hey guys,

The sound on my toshiba a30 laptop doesn't work.

What can I do?

---

### Post by spec456 on 2007-12-15
What type of sound card do you have?

Applications > Accessories > Terminal

Then type:

```
lpsci | grep -i audio
```

---

### Post by Jem00 on 2007-12-19
Hey thanks fo the reply,

I have a Realtek AC'97 sound card.
```
 lspci | grep -i audio
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller

```

---

### Post by Jem00 on 2008-02-16
Whats the next step?

Anyone?

---

