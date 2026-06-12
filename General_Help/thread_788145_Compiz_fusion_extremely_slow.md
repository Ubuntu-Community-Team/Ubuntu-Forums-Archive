---
title: "Compiz fusion extremely slow"
date: 2008-05-09
forum: General Help
---

### Post by Onay on 2008-05-09
My compiz fusion installation was working perfectly fine on my newly installed Hardy installation. I was somewhat disappointed with firefox 3 since I cannot install my previous plugins that I so religiously used in firefox 2, so I decided to install that.

After a reboot of my computer, my compiz fusion is extremely slow. I have a 256mb graphics card, so it shouldn't be a problem. However, when I use indirect rendering as a compiz option, it seems to work beautifully. I have never needed to do this before in any previous compiz installations... and I'm sure my graphics card can handle direct rendering.

I removed firefox 2 and the problem persists. Perhaps it is unrelated to firefox 2... How do I figure out the problem and solve it?

---

### Post by prshah on 2008-05-09
> **Onay said:**
> 
After a reboot of my computer, my compiz fusion is extremely slow. I have a 256mb graphics card, so it shouldn't be a problem. However, when I use indirect rendering as a compiz option, 

Please post output of the below command for information```
LIBGL_DEBUG=verbose glxinfo | grep -A 5 -B 5 direct
```

---

