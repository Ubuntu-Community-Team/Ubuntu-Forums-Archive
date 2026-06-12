---
title: "Installing Ubuntu Server Edition"
date: 2007-06-28
forum: General Help
---

### Post by ajegoyal on 2007-06-28
Hello

I'm new to Ubuntu and Wubi. I want to install Ubuntu Server Edition thru Wubi on my Notebook. Does Wubi support Ubuntu Server Edition?

Thanks in Advance.

Regards
Ajay

---

### Post by ago on 2007-06-28
> **ajegoyal said:**
> Hello

I'm new to Ubuntu and Wubi. I want to install Ubuntu Server Edition thru Wubi on my Notebook. Does Wubi support Ubuntu Server Edition?

Thanks in Advance.

Regards
Ajay

Hmm not really, I mean we could easily add it, but I would not suggest to people to run a server in a nested filesystem. What you can do is edit C:\wubi\install\preseed.cfg BEFORE rebooting and replace ubuntu-desktop with ubuntu-standard. This way you will use Wubi to install the barebone system and from there you can grab any other server package you want.

---

