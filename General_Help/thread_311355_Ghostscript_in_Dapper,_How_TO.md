---
title: "Ghostscript in Dapper, How TO??"
date: 2006-12-02
forum: General Help
---

### Post by Portable_Jim on 2006-12-02
How do you install ghostscript in dapper??

---

### Post by Portable_Jim on 2006-12-02
I want to know how to print using using it!! Whoops.

---

### Post by windwalker78 on 2006-12-18
> **Portable_Jim said:**
> I want to know how to print using using it!! Whoops.

Maybe you should try gv filename.ps

If you are missing gv (ghostview), then you should:
#sudo apt-get install gv

Keep in mind that I am having very big problems with some fonts and ghostscript (gs-esp) in Dapper!!! I will make a post soon. I had to downgrade to gs-esp v 7.07.1 and now everything is fine. I fellow compiled the latest version from source, but another one complained about problem with HPlj and I am depending on this package.

I hope this helps.

Todor

---

