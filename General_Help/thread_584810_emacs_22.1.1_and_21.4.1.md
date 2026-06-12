---
title: "emacs 22.1.1 and 21.4.1"
date: 2007-10-21
forum: General Help
---

### Post by evillan on 2007-10-21
I installed emacs 21.4.1 (Applications -> Programming) under 7.04.

When I upgraded to 7.10, it seems like emacs 22.1.1 was installed as well, but this time at Applications -> Accessories.
Now I have to versions of emacs and I really only need one.

Also, I have two versions of emacs (at Applications -> Accessories), emacs 22 (client) and emacs 22 (GTK), what is the difference?

---

### Post by mali2297 on 2007-10-21
I think it is emacs 22 (GTK) that you want. The new version of emacs integrates better with Gnome (and XFCE). If you use KDE, you might want the simple emacs22 package instead of emacs22-gtk. Either way, you can uninstall emacs21. These things can be done in Synaptic.

As for emacs 22 (client), I found this from *man emacsclient*:
> 
You  can  either call emacsclient directly or let other programs run it for you when necessary.  On GNU and Unix systems many programs consult the environment  variable  EDITOR  (sometimes  also  VISUAL)  to obtain  the  command  used  for editing.  Thus, setting this environment variable to &#8217;emacsclient&#8217; will allow these programs to use an already running Emacs for editing.  Other operating systems  might  have their own methods for defining the default editor.

For emacsclient to work, you need an already running Emacs with a server.  Within Emacs, call the functions &#8216;server-start&#8217; or &#8216;server-mode&#8217;.  (Your &#8216;.emacs&#8217; file can do this automatically if you add either &#8216;(server-start)&#8217; or &#8216;(server-mode 1)&#8217; to it.)

I don't know how useful this client is but it comes with the package. You can hide it from the menus though.

---

### Post by evillan on 2007-10-21
Thank you.

---

