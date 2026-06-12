---
title: "Firefox and aMSN crash"
date: 2008-02-24
forum: General Help
---

### Post by weiswang on 2008-02-24
When I run firefox as a normal user, it crashes on some Chinese websites, for example, wenxuecity.com and cmfu.com. However, it functions completely fine when I use root.

Similar story for aMSN. It crashes during logging in when I use it as a normal user but fine if I'm root.

My Linux distribution is the latest Ubuntu 7.10.

Anyone has a clue about what's going on? Thanks a lot!

---

### Post by weiswang on 2008-02-25
Just to bring draw more attention...... Anyone has similar problems?

I suspect there are some weird configurations associated with my normal user accounts so I deleted them and added some new ones. But still, the new accounts suffer the same problems even when I authorize the normal users the administrative privilege.

What could be the reasons?

---

### Post by UK-Wobbie on 2008-02-25
> **weiswang said:**
> Just to bring draw more attention...... Anyone has similar problems?

I suspect there are some weird configurations associated with my normal user accounts so I deleted them and added some new ones. But still, the new accounts suffer the same problems even when I authorize the normal users the administrative privilege.

What could be the reasons?

Have you had a go reinstalling aMsn and Firefox?

---

### Post by Aerin on 2008-02-25
> **weiswang said:**
> When I run firefox as a normal user, it crashes on some Chinese websites, for example, wenxuecity.com and cmfu.com. However, it functions completely fine when I use root.


Did you try running them from the terminal to see if it gave any error messages before crashing?

---

### Post by jqdkf on 2008-03-12
check  the value of LD_LIBRARY_PATH, clean .bash_profile .bashrc to see if the problem persist.

---

