---
title: "Disabling Helvetica font in Hardy"
date: 2008-04-25
forum: General Help
---

### Post by Dingbats on 2008-04-25
I just installed Hardy Heron, and now I see that a lot of webpages are displayed with the rather ugly Helvetica fonts instead of the native Sans.  Changing the preferences in Firefox makes no difference, since Sans is already the default, it's just that when Helvetica is specified in the CSS, it will be used.

I've been searching all over for fixes to this problem, but none have worked.  Is there some way to just disable that font completely?

EDIT:  I think what I referred to as Sans is Deja Vu Sans.

---

### Post by peterdk on 2008-04-26
You could remove the helvetica font from ubuntu, but that would mean that you can't use it at all anymore.

But after a little searching: I can't find a helvetica font myself. So I guess a other named font mimics helvetica.

---

### Post by Dingbats on 2008-04-26
I fixed it.  It wasn't Helvetica, it was the Nimbus fonts.  I changed them to better looking ones in /etc/fonts/conf.d/30-metric-aliases.conf.

---

