---
title: "Can't open  Access-Your-Private-Data.desktop  during recovery of encrypted home dir"
date: 2014-09-04
forum: General Help
---

### Post by klundermann on 2014-09-04
Following a crash, I'm running 14.04 on a live USB stick to recover the encrypted home directory on my hard drive.

I successfully ran  [FONT=system]ecrypt-recover-private[/FONT]  on my home directory.  Then I ran  [FONT=system]sudo nautilus[/FONT]  and navigated to  [FONT=system]/tmp/ecryptfs.[/FONT]*XXXXXXXX* , where I found, as expected, the file  [FONT=system]Access-Your-Private-Data.desktop[/FONT] , which had been created by [FONT=system]ecrypt-recover-private .[/FONT]

The trouble is that when I click on the file, I don't see my home directory.  Rather, two things happen.  Firstly, the following error message appears in the terminal window in which I opened Nautilus:

[COLOR=#ff0000](gnome-terminal;92460; GLIB-GIO-CRITICAL **; g_settings_get; the format string may not contain '&' (key 'monospace-font-name' from schema 'org.gnome.desktop.interface').  This call will probably stop working with a future version of glib.[/COLOR]

  Secondly, a terminal window flashes briefly open and immediately closes.

I seem so close to recovering my home directory; what do I need to do to actually get to my files?

---

