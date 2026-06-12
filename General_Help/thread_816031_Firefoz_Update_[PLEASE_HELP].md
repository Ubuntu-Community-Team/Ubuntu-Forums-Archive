---
title: "Firefoz Update [PLEASE HELP]"
date: 2008-06-02
forum: General Help
---

### Post by HpZ on 2008-06-02
I'm on Ubuntu and I have NO idea how to update Firefox to its latest version. When I go to Help the "Check For Updates" button is greyed out i.e un-clickable. It doesn't upgrade itself and yes, I've got "Check For Updates Daily" on the Update Manager.

---

### Post by Nepherte on 2008-06-02
The latest stable version of Firefox, 2.0.0.14 is in the universe repository. Firefox 3.0 rc1 is in the proposed repository. If you enabled those repos, you should be able to install the version you want with synaptic.

---

### Post by HpZ on 2008-06-02
> **Nepherte said:**
> The latest stable version of Firefox, 2.0.0.14 is in the universe repository. Firefox 3.0 rc1 is in the proposed repository. If you enabled those repos, you should be able to install the version you want with synaptic.

where is this "universe repository"?

---

### Post by babylon2233 on 2008-06-02
I think updating to Firefox 3 RC1 is unnecessary because a lot of users said it has more bugs than beta 5. So, I suggest you wait for the final release that will come out before the end of this month.

---

### Post by leito666 on 2008-06-02
I have read that RC2 is coming soon, may be you should wait a bit.

---

### Post by tom56 on 2008-06-02
Updates to Firefox (like everything else in Ubuntu) are supplied through the Ubuntu Update Manager at System -> Administration -> Update Manager.

---

### Post by Nepherte on 2008-06-02
> **HpZ said:**
> where is this "universe repository"?
System > manage > software sources (or something alike). Then check the box that says universe at the end. Installing Firefox 2 will most likely give you problems because FF 3 beta 5 and FF 2 will share the same .mozilla folder, so we want to backup it:
```
cd ~/ && mv .mozilla .mozilla-backup
```
Then you can install firefox 2 by typing in a terminal:
```
sudo apt-get update && sudo apt-get install firefox-2
```


But I'd rather go for Firefox 3 RC1 since Hardy comes with the beta after all.
System > manage > software sources > updates tab > check the box with hardy-proposed
Upgrade your current Firefox 3 beta 5 by typing in a terminal:
```
sudo apt-get update && sudo apt-get upgrade
```

I use Firefox 3 RC1 on a lot of different pcs and didn't experience any problem with it. This is very machine related of course and since it's a beta problems still exist on some configurations.

---

### Post by heatblazer on 2008-06-02
I`ll report too that rc1. has more bugs than 5b. So you`d better stick with 5b (unless you don`t have FF2, which is way better).

---

### Post by Nepherte on 2008-06-02
If you want guaranteed stability, I'd go for Firefox 2 as well.

---

