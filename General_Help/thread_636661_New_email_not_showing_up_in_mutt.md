---
title: "New email not showing up in mutt"
date: 2007-12-10
forum: General Help
---

### Post by Aseld on 2007-12-10
I've just installed mutt, and it's working pretty well (I can send mail, and the first time I tried I could receive it as well) but now when I get new mail it's not showing up. fetchmail seems to be getting it, but when I run mutt it's not there. Is there something special I need to do to access it? I'm just seeing an empty inbox.

I'm running on Gutsy Server, by the way.

.muttrc is as follows:

```
set mbox_type=maildir
set mbox="~/mail/inbox/"
set spoolfile="~/mail/inbox/"
set folder="~/mail/"
set record="~/mail/sent/"

macro index G "!fetchmail\n" "Invoke fetchmail"
macro pager G "!fetchmail\n" "Invoke fetchmail"
```

Thanks a lot.

Edit: Sorry, had procmail configured incorrectly. Solved.

---

