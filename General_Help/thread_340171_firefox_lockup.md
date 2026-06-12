---
title: "firefox lockup"
date: 2007-01-16
forum: General Help
---

### Post by bkeithly on 2007-01-16
I have looked all around the forums and there doesn't seem to be a fix for the supposed firefox crash/system lockup issue.

So, just wanting to know how others are handing this.  By this I mean, are some using other browsers, has anyone found a way to correctly point the finger at firefox (i.e: what logs to look at), or anything that might be a step in the right direction???

However, PLEASE do not suggest using a different linux distro.  I have used countless others and ubuntu tops the list as far as a desktop goes.

Thanks!

---

### Post by aysiu on 2007-01-16
What do you mean by "the supposed firefox crash/system lockup issue"?

---

### Post by tronica on 2007-01-16
just an idea, what if you start firefox from the terminal, and when it crashs, maybe it will output some errors. just my 2 cents

---

### Post by bkeithly on 2007-01-17
I think I might have found something:

LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libflashplayer.so [/usr/lib/firefox/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so [/usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so: wrong ELF class: ELFCLASS32]


Now I just need to figure out how to get it to stop loading these plugins.

---

### Post by napzilla on 2007-01-20
Load Firefox in safe mode?

[INDENT]/path/to/firefox/firefox -safe-mode[/INDENT]

That would at least let you test your hypothesis.

*Command line from: [http://kb.mozillazine.org/Safe_mode]("http://kb.mozillazine.org/Safe_mode")*

---

