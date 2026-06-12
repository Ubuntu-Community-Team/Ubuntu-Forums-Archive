---
title: "Epiphany and GWget"
date: 2006-10-27
forum: General Help
---

### Post by d3x7r0 on 2006-10-27
Ok So I installed epiphany, epyphany-extension-gwget and gwget but I can't seem to make them work together, I don't see any options in epiphany to use it...

---

### Post by niels on 2006-10-29
> **d3x7r0 said:**
> Ok So I installed epiphany, epyphany-extension-gwget and gwget but I can't seem to make them work together, I don't see any options in epiphany to use it...

I have the exact same problem...

---

### Post by niels on 2006-10-29
I just figured out the problem. It seems like the Gwget extension is packed for Epiphany 2.15.

Here is how you fix it:
You will have to copy the content of /usr/lib/epiphany/2.15/extensions to /usr/lib/epiphany/2.16/extensions

Do it like this:
```
sudo cp /usr/lib/epiphany/2.15/extensions/* /usr/lib/epiphany/2.16/extensions/
```

Then restart Epiphany and select the GWGet extension.

It's an stupid bug - how do I report it?

---

### Post by puccaso on 2007-05-24
my one epiphany reports 2.18???  i dont have a 2.15 or .16 directory
what do i do?

---

