---
title: "Restricting Access To Programs"
date: 2007-09-15
forum: General Help
---

### Post by Mikey_MW on 2007-09-15
Ok, I've set up ubuntu on the family computer and everything just works (after 3 years of windows dying I finally convinced them) Anyway, there is just one thing I need to adjust. I'd like to be able to restrict my younger brother from accessing Open Arena. Is there some way to put a password on that one game? I enjoy it, but its not exactly a kids game. He has his own user account.

Thanks.

---

### Post by p_quarles on 2007-09-15
Running the following commands in the terminal should do the trick:
```
sudo chown *your-user-name* /usr/games/openarena
```
Then:
```
sudo chmod 744 /usr/games/openarena
```
The first command makes you the owner of the executable that runs OA. The second prevents any one but the owner from executing the file. Hope this helps.

---

