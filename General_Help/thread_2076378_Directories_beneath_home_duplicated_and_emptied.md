---
title: "Directories beneath home duplicated and emptied"
date: 2012-10-25
forum: General Help
---

### Post by mcsmith on 2012-10-25
This morning I awoke to my 12.04 system being frozen (completely non-responsive and LEDs on keyboard blinking).  I did a hard shutdown.  When the system came up and I logged in, the desktop environment looked for all intents and purposes like a newly created account.  All my settings had reverted to defaults, startup programs hadn't run, etc.

After a little more investigation, things look even stranger.  The directories that are typically created beneath $HOME (e.g. Desktop, Downloads, Documents, Music, Pictures, Public, Templates and Videos) are duplicated and devoid of content.

To illustrate:
```

~$ ls -l D* Mu* P* Templates* V*
Desktop:
total 0

Desktop:
total 0

Documents:
total 0

Documents:
total 0

Downloads:
total 0

Downloads:
total 0

Music:
total 0

Music:
total 0

Pictures:
total 0

Pictures:
total 0

Public:
total 0

Public:
total 0

Templates:
total 0

Templates:
total 0

Videos:
total 0

Videos:
total 0

```

I'm using an encrypted home directory, and it appears to be mounted, since other directories seem fine.

Can someone suggest an explanation as to what happened and whether it's possible to recover the content of these directories (other than to recover from a backup)?

Thanks,

Mike

---

### Post by mcsmith on 2012-10-26
Well I'm still in the dark regarding the cause, but the recovery process is fairly straightforward.  

Note that there were additional hidden files and directories that were duplicated beyond what I mentioned in my original post.

I created a new directory, $HOME/mystery, and moved each of file and/or directory that had a duplicate entry into $HOME/mystery.  As it turned out, the "first of the duplicates" was the bogus entry.  After the moves, the valid files and directories were left under $HOME.  A minor complication was $HOME/.gvfs, which needed some sudo encouragement (umount, chmod, mv) before it complied.

If anyone can explain how this all happened, I'm sure interested.

Thanks!

---

