---
title: "conflict between &quot;unset LANG&quot; in .bashrc and menu bar clock"
date: 2016-10-10
forum: General Help
---

### Post by parminides on 2016-10-10
Some time ago, I added "unset LANG" to .bashrc in order to show uppercase files first. (Call me a traditionalist.) Somehow, this made the menu bar clock disappear. If I remove that line from .bashrc, the clock returns. How can I keep my clock and list uppercase files before lowercase ones? It would also be nice if someone could explain why this strange correlation occurs. I am running Ubuntu 14.04.5 LTS.

---

### Post by steeldriver on 2016-10-10
"list uppercase files before lowercase ones" in what context? Rather than unsetting LANG, I'd probably try something like

```

export LC_COLLATE="C"

```

---

### Post by parminides on 2016-10-10
> **steeldriver said:**
> "list uppercase files before lowercase ones" in what context? 

For "ls" command and folder views.

Your trick (export LC_COLLATE="C") worked without messing up the clock. Problem solved. Thanks.

Just for curiosity's sake, it would be nice if someone could explain why "unset LANG" killed the clock.

---

