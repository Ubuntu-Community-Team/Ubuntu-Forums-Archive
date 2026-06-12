---
title: "how to release swap after closing an application?"
date: 2008-07-06
forum: General Help
---

### Post by chunchengch on 2008-07-06
Every time I open OpenOffice, it will use some swap, but when I close OpenOffice, the swap space is still occupied.

I just wonder if there is any command to release swap space instead of reboot?

Thanks for reply!

---

### Post by sdennie on 2008-07-06
It's probably not necessary to do this but, you should be able to accomplish it with:

```

sudo swapoff -a
sudo swapon -a

```

Are you sure that you really want the memory that's been swapped out to come back into memory?  It's usually swapped out for good reason (it's not being used).

---

### Post by ChameleonDave on 2008-07-06
> **chunchengch said:**
> Every time I open OpenOffice, it will use some swap, but when I close OpenOffice, the swap space is still occupied.

I just wonder if there is any command to release swap space instead of reboot?

Thanks for reply!

Why would you want it to release it?  It's probably putting a bit of data there to speed things up in some way.  Even if it's not necessary, it doesn't really matter.  It will probably clear if some other application requires the swap space.

---

### Post by ibutho on 2008-07-06
You don't have to do anything because the system will make sure that the swap space is used by other applications when needed.

---

