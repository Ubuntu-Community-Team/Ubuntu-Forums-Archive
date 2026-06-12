---
title: "Help! I've lost firefox in dependency mixups!"
date: 2005-06-23
forum: General Help
---

### Post by jnoreiko on 2005-06-23
Firefox has gone missing.
Back when I was on Warty, I got some strange messages form Synaptic about the ubuntu-desktop package, and someone in IRC said I could remove it as it was just a meta-package. So I did.
Then last week I upgraded to Hoary, using synaptic smart upgrade and the CD.

Today, I was asking why OOo wasn't using the Gnome widgets, and someone in IRC suggested I try installing ubuntu-desktop... so I did.

Since then, I've lost Firefox.
Any attempts at reinstalling say things like can't overwrite some file, or can't stat some file.
I had Hoary backports enabled, and it looks like that's caused problems with the firefox packages -- I had 'firefox' and also 'mozilla-firefox'.

I've tried removing them completely, and then putting ubuntu-desktop back, but I get the same file errors as before.

Any ideas? Should I give up and reinstall from scratch?

---

### Post by jnoreiko on 2005-06-26
I've installed the mozilla suite, so I'm back on Ubuntu.

The error messages from synaptic are:

```

Updating mozilla-firefox chrome registry...E: /usr/lib/mozilla-firefox/extensions/installed-extensions.txt still present. Registration might have gone wrong.
mv: cannot stat `/usr/lib/mozilla-firefox/defaults.ini': No such file or directory

```

Does that mean the firefox extensions I installed are to blame?

---

### Post by Xian on 2005-06-26
Read this [THREAD](http://www.ubuntuforums.org/showthread.php?t=17142) for more information.

---

### Post by jnoreiko on 2005-06-26
Thanks!  :grin:

---

