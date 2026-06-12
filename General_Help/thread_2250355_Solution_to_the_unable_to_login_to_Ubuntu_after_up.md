---
title: "Solution to the unable to login to Ubuntu after updating 14.01"
date: 2014-10-28
forum: General Help
---

### Post by evilishan on 2014-10-28
Firstly I apologise if I am posting in the wrong place, I'm posting here because I don't have enough 'reputation' on the AskUbuntu community thing to answer the question. I don't know where else to put this, so I thought it might be useful to put here.

[LIST=1]
[*]Enter Recovery Mode at Grub Menu.
[*]Run fsck (to change filesystem state to read/write mode).
[*]Navigate to the home directory of the user who cannot login.
[*]Change the ownership of the .Xauthority file under the user that cannot login back to the user.
[/LIST]
You should be good to go!

---

