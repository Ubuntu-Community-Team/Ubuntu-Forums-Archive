---
title: "One user sees Flash in FIrefox, another doesn't--where to look for config difference?"
date: 2007-11-18
forum: General Help
---

### Post by jejones3141 on 2007-11-18
On my wife's computer, I have Gutsy Gibbon installed, with flashplugin-nonfree installed as well. She cannot view Flash when using Firefox on her account, but I can on my account on her computer, so the difference must be in our respective configurations... but when I check her preferences, it says that .SWF and .SPL files should both be opened with Shockwave Flash, just as it says in my preferences. Where should I look to find what is keeping her from seeing, for example, fancast.com?

---

### Post by ddrichardson on 2007-11-18
Is it installed in both profiles?

---

### Post by Rev60073 on 2007-11-18
In my case, the Adobe Flash Player files installed in ~/.macromedia/Flash_Player. So maybe you'll have to install it while logged on as her user.

---

### Post by jejones3141 on 2007-11-18
> **Rev60073 said:**
> In my case, the Adobe Flash Player files installed in ~/.macromedia/Flash_Player. So maybe you'll have to install it while logged on as her user.

Perhaps I don't understand exactly what happens when one enters the command

```
sudo apt-get install flashplugin-nonfree

```

Does that not set up the plugin for all users?

---

