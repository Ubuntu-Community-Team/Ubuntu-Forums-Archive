---
title: "KWallet Does Not Save ANY Passwords."
date: 2006-11-22
forum: General Help
---

### Post by jlacroix on 2006-11-22
Hello everyone, just as the topic suggests, KWallet is useless for me right now. Kontact asks for a password for each POP and SMTP every time I start it, and the same thing with Kopete. In Control Center under KWallet, I have both of the above applications set to "Always allow" and I always check the "Remember Password" box when typing in passwords.

Is there a work around for this?

---

### Post by karamba_kid on 2006-11-22
If you look at the Kmenu --> System Settings --> Security & Privacy window do you see any settings that need to be enabled?  I haven't had any trouble with Kwallet in Dapper.

---

### Post by jlacroix on 2006-11-22
Everything is turned on there.

---

### Post by Progressive on 2006-12-13
Same problem for me. It prompts for the kwallet password. Everything is enabled, and I check to "always allow" any programs that request access to kwallet. However, it seems to lose all of these settings every time I restart X.

This is very annoying. I hope there is a simple fix.

---

### Post by NeoChaosX on 2006-12-13
Try removing your exisitng wallet and let apps create their own wallet. I had a similar problem with KNetworkManager not saving encryption keys at first, but removing all the exisitng wallets and letting KNM recreate them fixed it for me.

---

