---
title: "cant install anything"
date: 2008-03-05
forum: General Help
---

### Post by computer_guy98 on 2008-03-05
I recently had to downgrade to Feisty fawn from gutsy gibbon. And After doing the 190
updates Add/Remove, Package Manager, and Update manager will not run.
they all will open but half way through loading they just close.

Any help would be greatly appreciated ](*,)

---

### Post by gobbles414 on 2008-03-05
> **computer_guy98 said:**
> I recently had to downgrade to Feisty fawn from gutsy gibbon. And After doing the 190
updates Add/Remove, Package Manager, and Update manager will not run.
they all will open but half way through loading they just close.

Any help would be greatly appreciated ](*,)

Are you prompted for your password before Add/Remove, Package Manager, and Update Manager crash? Does Software Sources launch successfully? You might try entering *sudo apt-get update* into the terminal, and then launching the utilities that have been crashing.

I assume that by downgrading you mean that you totally erased your Gusty installation when you installed Feisty. Although there have been some discussions of adding an OS downgrade function to Ubuntu, I don't think that any of them have been implemented.

Also, why did you downgrade to Feisty (just curious)?

---

