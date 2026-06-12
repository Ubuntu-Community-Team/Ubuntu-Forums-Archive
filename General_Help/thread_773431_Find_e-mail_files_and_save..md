---
title: "Find e-mail files and save."
date: 2008-04-28
forum: General Help
---

### Post by cutiger95 on 2008-04-28
I want to do a fresh install on my system and totally wipe everything.  However I would prefer to keep all of my swiftfox bookmarks and my e-mails that are downloaded and saved locally.

Problem is that I havent a clue as to how to do it.  Anybody know of instructions or can give a chap a hand.

Thanks ahead of time.

Oh by the way I am using Thunderbird for my mail client.

---

### Post by Monicker on 2008-04-28
> **cutiger95 said:**
> I want to do a fresh install on my system and totally wipe everything.  However I would prefer to keep all of my swiftfox bookmarks and my e-mails that are downloaded and saved locally.

Problem is that I havent a clue as to how to do it.  Anybody know of instructions or can give a chap a hand.

Thanks ahead of time.

Oh by the way I am using Thunderbird for my mail client.

Thunderbird mail will be in /home/username/something.default/Mail

*Note: mail for an imap account will be in ImapMail instead of Mail*


Dunno about swiftfox, but I assume its a variant of Firefox.  For Firefox the path is /home/username/.mozilla/firefox/something.default/bookmarks.html.

You could try the following command from a terminal:
```

find ~/ -name bookmarks.html
```

---

### Post by cutiger95 on 2008-04-28
Just what I was looking for.  Thank you very much I am going to move the files over to my USB stick then wipe this puppy clean and install 8.04.

---

