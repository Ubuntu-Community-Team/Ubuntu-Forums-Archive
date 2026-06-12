---
title: "How to migrate Evolution mail accounts?"
date: 2006-07-23
forum: General Help
---

### Post by LordMau on 2006-07-23
Hi, I'm stumped on this. Got a new drive since my old one's getting flasky. After install was stable, I copied my old .evolution folder to my new home directory (of the same name as the old). Started evolution and so far I see all my old email. But the issue is all the various mail accounts don't show up under the new install.

Under the ~/.evolution/mail/pop folder the folders for my old accounts exist. 

Althoug I guess i can recreate the mail account properties its kinda a pain ahehe. Specially considering the old emails themselves show up.

Any tips on how to do this properly?

---

### Post by jordilin on 2006-07-23
I don't know but perhaps doing File->import? If not, it would be interesting to know because every time we upgrade to another version of Ubuntu is the same story.

---

### Post by LordMau on 2006-07-23
Well it seems there already is a wiki for this issue:

[MigrateEvolutionToNewComputer]("https://help.ubuntu.com/community/MigrateEvolutionToNewComputer")

On my part I generally got the process as described but failed to do one part:

```
gconftool-2 --shutdown
```

which may have prevented me from importing the account details. Now i'm  happy camper!

---

