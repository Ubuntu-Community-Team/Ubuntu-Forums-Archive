---
title: "Ies4Linux and multiple users"
date: 2008-02-08
forum: General Help
---

### Post by lemmy999 on 2008-02-08
My partner is having to work from home for a few weeks. She is going to have to use our Ubuntu only PC for her job. One of the sites she needs to visit will only work using IE6. I have installed Ies4Linux as root into my /home. How do I enable it so that my SO can use Ies4Linux from her account.

I have tried googling for the answer but the relevant page on the developers site shows a 404 error

---

### Post by SPr on 2008-02-08
> **lemmy999 said:**
> My partner is having to work from home for a few weeks. She is going to have to use our Ubuntu only PC for her job. One of the sites she needs to visit will only work using IE6. I have installed Ies4Linux as root into my /home. How do I enable it so that my SO can use Ies4Linux from her account.

I have tried googling for the answer but the relevant page on the developers site shows a 404 error

I don't know if this is the right way but I would create a group called (for example) "ie_group" and add yourself and your partner to this group. Then change the group ownership of the IE4Linux folder to the "ie_group" so you both may use it.

---

