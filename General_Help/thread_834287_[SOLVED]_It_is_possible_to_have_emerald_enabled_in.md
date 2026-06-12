---
title: "[SOLVED] It is possible to have emerald enabled in 1 user account and disabled in oth"
date: 2008-06-19
forum: General Help
---

### Post by Dan_Dranath999 on 2008-06-19
It is possible to have emerald enabled in 1 user account and disabled in other?

-I use Compiz Fusion+Emerald in my personal account, and a "guest account" with just Metacity ¿Could i enable just the woobly windows plugin without changing to Emerald in the guest account?

---

### Post by damis648 on 2008-06-19
I am pretty certain you can, as compiz settings are only saved per-user. :popcorn:

---

### Post by Dan_Dranath999 on 2008-06-19
I want Compiz enabled in both accounts, but Emerald in the Main account and Metacity in the Guest account.

I don't have any problems with the main account, i already have it configured the way i want. But when i enable Compiz in the guest account, Emerald pops up as the default windows manager (and i can't find the way to disable it just for that account)

so:
main account: CompizFusion + Emerald (ok)
guest account: CompizFusion + Metacity (!)

---

### Post by damis648 on 2008-06-19
In the compiz settings, go into Windows Decorations. In the field with "command", put
```
metacity --replace
```
and log out and back in and see how it goes.

---

### Post by Dan_Dranath999 on 2008-06-20
well, nothing happened...

---

### Post by Forlong on 2008-06-22
Try this in your guest account:
```
mkdir -p $HOME/.config/compiz && echo USE_EMERALD=no >> $HOME/.config/compiz/compiz-manager
```

---

### Post by Dan_Dranath999 on 2008-06-23
Thanks! i'll try that when i get home.

---

### Post by Dan_Dranath999 on 2008-06-23
> **Forlong said:**
> Try this in your guest account:
```
mkdir -p $HOME/.config/compiz && echo USE_EMERALD=no >> $HOME/.config/compiz/compiz-manager
```

Yesssir, you got it! thanks!

but i used a variant: 

```
echo USE_EMERALD="no" >> ~/.config/compiz/compiz-manager
```
from [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/153650](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/153650)

So, the only thing that compizfusion needs to stop using emerald is a little text file inside /.config/compiz/ ... (there should be a button or something for this)

And, as someone wrote at launchpad.net: "Setting the "command" in the Window Decorations plugin in ccsm fails to have any effect; it's simply ignored."

---

