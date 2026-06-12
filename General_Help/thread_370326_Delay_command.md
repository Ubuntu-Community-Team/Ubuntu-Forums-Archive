---
title: "Delay command?"
date: 2007-02-25
forum: General Help
---

### Post by malfist on 2007-02-25
Is there a delay command? Say I'm listening to my music as I go to sleep and want Rhythmbox to shut off in 60min but leave the computer running for torrents how would I do that? What would the command to kill rhythmbox and how would I set a delay?

---

### Post by ~LoKe on 2007-02-25
```
sleep 360 && killall rhythmbox
```
Something like that.

---

### Post by llamakc on 2007-02-25
You could use "at".

---

### Post by llamakc on 2007-02-25
> **~LoKe said:**
> ```
sleep 360 && killall rhythmbox
```Something like that.

I like this one better.

---

### Post by malfist on 2007-02-26
Is the 360 seconds or minutes?

---

