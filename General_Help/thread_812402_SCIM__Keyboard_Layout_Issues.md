---
title: "SCIM / Keyboard Layout Issues"
date: 2008-05-29
forum: General Help
---

### Post by BassKozz on 2008-05-29
I've been having these problems or a while now, I recently upgraded from Feisty (7.10) to Hardy (8.04), thinking it would've resolved these issues, but nope, sure enough they remain...

What the problem is, well It's hard to describe but sometimes out of the blue the SHIFT, CTRL, ALT, CAPS LOCK, keys all stop working, and my keyboard shortcuts go all out of whack; for example Sometimes when I hit any letter on the keyboard it closes the current window, which becomes a serious pain in the **** when I've setup a screensaver that locks the machine after I walk away for 10minutes, and I come back only to find out as soon as I start typing the first character of my password it makes the lock/password entry window disappear (the only work around is to click "switch users" and re-login completely).
And this is completely random when it happens, it seriously comes up out of the blue.

**_The Fix:_**
I have to keep going into **_A_pplications->_O_ther->_K_eyboard Layout** and removing and replacing my keyboard layout (US) and applying the change to fix.

Is it just me or is anyone else experiencing similar issues?

---

### Post by crjackson on 2008-05-29
> **BassKozz said:**
> I've been having these problems or a while now, I recently upgraded from Feisty (7.10) to Hardy (8.04), thinking it would've resolved these issues, but nope, sure enough they remain...

What the problem is, well It's hard to describe but sometimes out of the blue the SHIFT, CTRL, ALT, CAPS LOCK, keys all stop working, and my keyboard shortcuts go all out of whack; for example Sometimes when I hit any letter on the keyboard it closes the current window, which becomes a serious pain in the **** when I've setup a screensaver that locks the machine after I walk away for 10minutes, and I come back only to find out as soon as I start typing the first character of my password it makes the lock/password entry window disappear (the only work around is to click "switch users" and re-login completely).
And this is completely random when it happens, it seriously comes up out of the blue.

**_The Fix:_**
I have to keep going into **_A_pplications->_O_ther->_K_eyboard Layout** and removing and replacing my keyboard layout (US) and applying the change to fix.

Is it just me or is anyone else experiencing similar issues?

I'm sure you've already done this but I'll ask anyway...  Have you tried a different keyboard?

If the answer is yes, be sure to try a keyboard of a different type.  If your current keyboard is USB, then try a PS2 or vice-versa.

---

### Post by BassKozz on 2008-05-29
> **crjackson said:**
> I'm sure you've already done this but I'll ask anyway...  Have you tried a different keyboard?

If the answer is yes, be sure to try a keyboard of a different type.  If your current keyboard is USB, then try a PS2 or vice-versa.
Actually I haven't tried another keyboard (I don't have a spare otherwise I would), but I do know that this keyboard works just fine because I dual boot into my WinXP partition and I never have any issues, it's only in Ubuntu that these issues appear.

---

### Post by BassKozz on 2008-06-04
I now have reason to believe that VMware is the culprit of this issue, but I don't know how to best present the issue to VMware's support forums...
I was using my computer all day today without experiencing the problem at all until I launched my WinXP VM using VMware...

Is anyone else experiencing these issues w/ VMware?

---

### Post by BassKozz on 2008-06-05
Found the bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/195982](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/195982)

---

