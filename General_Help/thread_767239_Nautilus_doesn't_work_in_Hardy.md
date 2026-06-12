---
title: "Nautilus doesn't work in Hardy"
date: 2008-04-25
forum: General Help
---

### Post by Ayzen on 2008-04-25
I updated Ubuntu 7.10 to 8.04 and Nautilus couldn't start now, the error message is "nautilus: symbol lookup error: nautilus: undefined symbol: eel_drect_empty".

I tried to remove it and then install again, but it still doesn't work. :(

---

### Post by Naatan on 2008-04-25
try removing your "~/.nautilus" directory.. you'll start out with a fresh install of nautilus (meaning that your settings are cleared)

---

### Post by Ayzen on 2008-04-25
> **Naatan said:**
> try removing your "~/.nautilus" directory.. you'll start out with a fresh install of nautilus (meaning that your settings are cleared)

Thanks for your reply.

I removed ~/.nautilus and all other folders related to Nautilus, then I reinstalled it again... Still doesn't work...

---

### Post by Naatan on 2008-04-25
Try installing an older version and see if that works for you, if it does then you might want to consider reporting it on launchpad

---

### Post by Ayzen on 2008-04-26
> **Naatan said:**
> Try installing an older version and see if that works for you, if it does then you might want to consider reporting it on launchpad

Downgraded version of Nautilus (from Gutsy) is working. I'll report that on launchpad.

Thanks.

---

