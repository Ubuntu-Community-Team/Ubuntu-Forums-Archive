---
title: "Vim not showing (--insert--) when in insert mode!"
date: 2014-08-20
forum: General Help
---

### Post by Imperium Guard on 2014-08-20
I installed a fresh copy of Ubuntu 14.04.1 on my desktop computer, but when I enter vi through the command internface, --insert-- doesn't appear (just a minor nuisance). How do I fix this?[ATTACH=CONFIG]255683[/ATTACH]

---

### Post by bizhat on 2014-08-21
Run

```

:set showmode

```

To make it perm, edit

~/.vimrc 

and add

```

set showmode

```

showmode can be replaced with smd, short form.

---

