---
title: "Citrix plugin install fails - sort of"
date: 2006-12-13
forum: General Help
---

### Post by marcw on 2006-12-13
I've had the Citrix plugin and client running fine on my previous Breezy and Dapper installs.  I've recently performed a fresh install of Edgy.  Everything works fine.  But when I performed the normal Citrix client and plugin install, the plugin does not show up in my Firefox about:plugins.  When I run the fat client that was installed (and shows up in my Gnome menu) it works fine.  It's just the plugin that doesn't show up.

A few points:
1) When I run Firefox about:plugins through a term session, I receive the following error:
LoadPlugin: failed to initialize shared library /usr/lib/ICAClient/npica.so [/usr/lib/ICAClient/npica.so: undefined symbol: XtWindowToWidget]
2) When I run firefox as root (sudo) there is no error, the plugin shows up and works as it should.
3) The Citrix install script was run as root as I have always done in the past.
4) I found a couple of posts referring to needing libXaw and libmotif installed.  That was done.

I would be most grateful for any help with this.  Thanks!  (sorry about the stupid smilies)

---

### Post by marcw on 2007-01-02
Even though I haven't been able to find the cause of the above behavior I did find a solution.  I simply deleted my existing Firefox profile (~/.mozilla/firefox/*.default) and started over.  Yes, I was forced to reload bookmarks, saved passwords, extensions, etc.  But at least I now have the Citrix plugin working under my own credentials instead of sudo.

I just wish I knew what was the root cause...

---

