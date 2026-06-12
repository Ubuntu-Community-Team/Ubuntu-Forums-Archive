---
title: "Text editor that does regular expressions"
date: 2008-01-29
forum: General Help
---

### Post by stchman on 2008-01-29
Hello all.

I am needing to search a large text file and replace data.

I need a text editor that does regular expressions.  Gedit does not from what I see.  Is there a plugin for gedit?

Thanks.

---

### Post by ~LoKe on 2008-01-29
Here's the plugin for GEdit + Regular Expressions.

[http://tapioca-voip.sourceforge.net/regexsearch_gedit_plugin.tar.gz](http://tapioca-voip.sourceforge.net/regexsearch_gedit_plugin.tar.gz)

---

### Post by stchman on 2008-01-29
> **~LoKe said:**
> Here's the plugin for GEdit + Regular Expressions.

[http://tapioca-voip.sourceforge.net/regexsearch_gedit_plugin.tar.gz](http://tapioca-voip.sourceforge.net/regexsearch_gedit_plugin.tar.gz)

How do you install plugins into Gedit?

Is there a ~/.gedit folder?

---

### Post by nick_h on 2008-01-29
vim will also do search and replace with regular expressions.

---

### Post by Whiffle on 2008-01-29
Kate will too, if you're a kde user.

---

### Post by stchman on 2008-01-30
I found out how to add plugins to gedit.

unzip the archive into the /usr/lib/gedit-2/plugins folder.

---

### Post by andrewkk on 2008-02-01
The only regex plugin I've seen for gedit is limited to searches. If you're looking for a search/replace functionality, you might be better off with a combination of the [External Tools]("http://live.gnome.org/Gedit/ToolLauncherPlugin") plugin and traditional text processing tools like [sed]("http://www.grymoire.com/Unix/Sed.html#uh-1").

Kate has a decent regex search/replace though. And KRegExpEditor is kind of cool.

---

### Post by Maulwuff on 2008-07-08
eclipse is very nice at that, too. With code assist for substitutions

---

