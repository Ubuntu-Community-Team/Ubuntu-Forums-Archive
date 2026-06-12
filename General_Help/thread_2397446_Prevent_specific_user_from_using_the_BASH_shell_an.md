---
title: "Prevent specific user from using the BASH shell and instead DOSEMU"
date: 2018-07-29
forum: General Help
---

### Post by warmango on 2018-07-29
So here is my delima, I am trying to have a second user i can access over SSH, named DOS for a reason, and then i plan on having this user only be able to use DOSEMU,

I can make DOSEMU start on login of the shell, but i cant seem to have it so when DOSEMU closes, it logs out.

Any ideas?

And MODS? DONT shove this in the SERVER catagory, almost no one actually looks there and if they do, i never get a notification that they replied.

---

### Post by HermanAB on 2018-07-30
Make a script that calls dosemu, so that you can add clean-up code after it exits.

---

### Post by Holger_Gehrke on 2018-07-30
```

man 5 passwd
man 5 shells
man 1 chsh

```
Get the idea ? Add dosemu to the list of valid login shells and change the users shell to that.
```

sudo cat $(which dosemu) >> /etc/shells
chsh -s $(which dosemu) DOS

```
should do it.

Holger

---

### Post by steeldriver on 2018-07-30
Ahem - I think you meant something more like

```

which dosemu | sudo tee -a /etc/shells

```

no?

FWIW I just tried it and it seems to work - although DOSEMU grumbles about keyboard mapping. Also you can't exit out of it with a regular DOS `exit`, you need to use `exitemu`

Another option might be to retain a regular Unix login shell, but make sure that you 
```

exec dosemu

```
from the shell startup file, rather than simply running it - `exec` will cause the dosemu process to **replace **the original login shell, rather than running as its child (hence there won't be a shell to return back to when it is exited).

---

### Post by Holger_Gehrke on 2018-07-30
Oops !

Sorry, The only excuse I have is heat and lack of sleep. If I had been thinking straight I would probably have written something like 'sudo bash -c 'which dosemu >> /etc/shells' (for some reason, the '| sudo tee'-idiom is something I rarely ever remember, even though I have seen it before and know it's advantages (environment differs with / without sudo ...) ) .

Holger

---

