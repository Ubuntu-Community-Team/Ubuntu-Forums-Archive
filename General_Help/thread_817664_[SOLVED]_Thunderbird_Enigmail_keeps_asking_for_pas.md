---
title: "[SOLVED] Thunderbird: Enigmail keeps asking for passphrase"
date: 2008-06-03
forum: General Help
---

### Post by jordon on 2008-06-03
I'm using the Thunderbird and Enigmail packages from the Hardy Heron repositories. My problem is that I can't set "Remember passphrase for __ minutes of idle time." No matter what number I set it to, I get prompted for my passphrase whenever I attempt to view or reply to an encrypted message.

So I have an encrypted message I want to view, and Enigmail prompts me for my passphrase. Then I press "Reply" to reply to the message, and Enigmail asks me for my passphrase again, no matter what. Isn't the "Remember passphrase" option supposed to prevent it from asking me the second time?

This happens when I disable all my other extensions, it happens when I use the official build of Enigmail, and it happens whether "Never ask for any passphrase" is checked or not.

---

### Post by jordon on 2008-06-05
I've found a way to get around this. In seahorse, I went to Edit -> Preferences ->  PGP Passphrases and selected "Always remember passphrases when logged in." This way, Enigmail will only ask for my passphrase once per login.

---

