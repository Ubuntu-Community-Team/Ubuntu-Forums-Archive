---
title: "Charset problems with Norwegian characters"
date: 2008-01-29
forum: General Help
---

### Post by Cavanagh on 2008-01-29
I'm quite new to Linux/Ubuntu, and have only been using it for a couple of weeks. It has worked fine until now.

My problem is a weird fault in the charset. When I write to people through IRC (for example irssi) and use the Norwegian letters æ, ø and å they look normal to me, but to several of the windows xp users they look weird and nothing like the letters I see.


Cavanagh

---

### Post by Cavanagh on 2008-02-03
bump

---

### Post by Cavanagh on 2008-02-15
bump...

---

### Post by Icebear on 2008-02-15
I am not sure but it could be something about the font is being used.

or more likely something about the settings in Linux utf8 is the best but not sure what in windows to set it to (or if they use use utf8 )

---

### Post by kesman on 2008-02-15
Check your irssi config with /set term_charset
If it's something with UTF-8 with it, the tell your friends to start using utf-8 too, and if not, try setting it to en.US.UTF-8 or something similar.

---

### Post by Cavanagh on 2008-02-17
Thanks!

The problem was that the windows users were using old versions of of mIRC which didn't support UTF-8.

Problem solved

Cavanagh

---

