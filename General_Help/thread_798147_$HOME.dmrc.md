---
title: "$HOME/.dmrc"
date: 2008-05-17
forum: General Help
---

### Post by malfist on 2008-05-17
Whenever I log in, I get the warning that $HOME/.dmrc is being ignored and blah blah blah about sessions and such.

Anyone know what's going on and how to fix it?

Thanks,
Malfist

---

### Post by Oldsoldier2003 on 2008-05-17
> **malfist said:**
> Whenever I log in, I get the warning that $HOME/.dmrc is being ignored and blah blah blah about sessions and such.

Anyone know what's going on and how to fix it?

Thanks,
Malfist
restart to a recovery console (select the recovery mode option from the grub menu)

```
chmod 700 /home/<yourusername>
chmod 644 /home/<yourusername>/.dmrc
reboot now
```

and it should clear up just fine :)

---

### Post by darco on 2008-05-17
A few threads going on about this....a "search" would do wonders :)

darco

---

### Post by malfist on 2008-05-17
That fixed it, thanks. I wish the ubuntu team hadn't taken away the handy search after you type in a title, it was much more effective than the search the forum offers. I can never find anything with it. I have better luck with google.

---

