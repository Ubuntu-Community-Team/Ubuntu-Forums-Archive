---
title: "How can I automatically start Beryl on login?"
date: 2006-11-29
forum: General Help
---

### Post by Vinze on 2006-11-29
Hey, I'm using Xubuntu Edgy, I've got Beryl svn installed and really like it. One problem though: it will only start after I run ```
killall xfwm4 && beryl-manager &
```
Now, I could add it to the autostarted applications, but that doesn't work and if it did, it would still be imperfect as it would first run xfwm4, then kill it and then start Beryl.

So, any other way to do this?

---

### Post by lordchaos on 2006-11-29
Im using Xubuntu Edgy too.

I simply added the command 'beryl-manager' in the autostarted applications.

Works fine.

---

### Post by Vinze on 2006-11-30
> **lordchaos said:**
> Im using Xubuntu Edgy too.

I simply added the command 'beryl-manager' in the autostarted applications.

Works fine.

Weird... I'll add it again, perhaps now with all the updates I received recently it'll work again...

---

