---
title: "an app won't work from another account?"
date: 2014-03-25
forum: General Help
---

### Post by kurja on 2014-03-25
Heyall, I'm having a problem launching a game (KSP). It normally runs without any install procedure to speak of, just put the files somewhere and launch. Now, [COLOR=#333333]I copied the entire KSP folder to my other computer, chown'd (-R) to relevant username, and chmod +x'd the binary but whenever I try to launch the game it just hangs.

[/COLOR][COLOR=#333333]So I tried copying the game over to another user account's home directory on this same computer (on which the game runs normally), and the problem is exactly the same. I tried launching with sudo ./<filename>, same story. I removed the configuration file (new one autocreated at startup), didn't help. I really can't think of anything else. Ideas?[/COLOR]

---

### Post by kurja on 2014-03-26
The account from which the game works is an admin account, the one from which it won't is a user account - but that shouldn't make a difference here, should it?

---

### Post by kurja on 2014-04-22
solved, the game itself has a problem with systems localized to use a comma as a decimal separator. Solution here, in case someone needs it [http://bugs.kerbalspaceprogram.com/issues/1575](http://bugs.kerbalspaceprogram.com/issues/1575)

---

