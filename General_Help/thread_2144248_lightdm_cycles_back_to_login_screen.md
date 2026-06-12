---
title: "lightdm cycles back to login screen"
date: 2013-05-11
forum: General Help
---

### Post by DuckHook on 2013-05-11
This morning, lightdm would not get past the login screen. It would accept my password, but then just flicker and cycle back to the login screen. TTY logins still worked fine. After searching the forums, I found a solution by deleting (or renaming) the .Xauthority file which X just rebuilt at next login. This solution works, but I'm perplexed, and concerned, as to why it happened. I'm also curious why deleting the .Xauthority file worked. All education, explanations and comments are greatly appreciated.

<edit>
Now noticing further wonky behaviour. Some apps are opening up maximized and <Alt>+<Tab> switching box has been reduced to 1/5 original size. Starting to get concerned!
</edit>

<2nd edit>
Ignore first edit. Restart put Unity into 2D, which seemed to be the problem. Additional restart, this time selecting 3D, solves wonky behaviour. Cause of original problem still bothers me, though.
</edit>

---

### Post by steeldriver on 2013-05-11
Did you look at the ownership / permissions of the .Xauthority file before you deleted it?

Typically what happens is that someone runs something like 'sudo startx', which causes *root* to write a .Xauthority file in the *user*'s home dir. Since the default permissions of .Xauthority are 600 (-rw-------), the X server can't write to it next time the user tries to start an X session - so the session fails to start

---

### Post by DuckHook on 2013-05-11
Thanks for the tip, steeldriver.

It didn't occur to me to check ownership/permissions, but since I deleted it with the simple rm command (no sudo), I doubt if it was owned by root. I didn't do anything out of the ordinary between last night and this morning either, and certainly not something like "sudo startx". Does my creating a new .Xauthority have other ramifications? For example, have I hosed any passwords or decoupled any keyrings? It seems to be behaving normally again, other than that first glitch with Unity starting up in 2D.

---

### Post by 25tom on 2013-05-11
I had this problem with Lubuntu Oneiric once - tried changing the ownership of the .Xauthority file, but without any improvement on ability to log in. I think the problem was that I installed Xfce and it switched the DM from lxdm to lightdm, and that somehow caused the problem. In my case, at the time I had to resort to a clean reinstall :(

---

### Post by steeldriver on 2013-05-11
> **DuckHook said:**
> Thanks for the tip, steeldriver.

It didn't occur to me to check ownership/permissions, but since I deleted it with the simple rm command (no sudo), I doubt if it was owned by root. 

Actually that doesn't follow - since you own and have execute permissions in the parent directory, you can delete a root-owned file without sudo - even if you can't write to it

---

### Post by DuckHook on 2013-05-11
> **steeldriver said:**
> ...since you own and have execute permissions in the parent directory, you can delete a root-owned file without sudo - even if you can't write to it

I see. Well, since the problem is now solved, though the mystery remains as to how it came to be, I am marking the thread "solved". Thanks for your teaching.

---

