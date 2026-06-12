---
title: "Gaim-Rhythmbox plugin"
date: 2005-07-19
forum: General Help
---

### Post by ounn on 2005-07-19
Hi

Had just installed gaim-rhythmbox ([http://gaim-rhythmbox.sourceforge.net](http://gaim-rhythmbox.sourceforge.net) /) plugin with no problem. They say to put something like %rb in the away message or on my personal information and i did it. The activate the plugin in the gaim plugins menu, Ok done it.  But then.. it is just not working, i cant see any information about the music i'm playing with Rhythmbox.

What im doing wrong? Someone managed a way to make this plugin  working? Or just not work with msn and jabber?

Thanks

ounn

---

### Post by brian g on 2005-10-12
[QUOTE=ounn]Hi

Had just installed gaim-rhythmbox ([http://gaim-rhythmbox.sourceforge.net](http://gaim-rhythmbox.sourceforge.net) /) plugin with no problem. They say to put something like %rb in the away message or on my personal information and i did it. The activate the plugin in the gaim plugins menu, Ok done it.  But then.. it is just not working, i cant see any information about the music i'm playing with Rhythmbox.

What im doing wrong? Someone managed a way to make this plugin  working? Or just not work with msn and jabber?

Thanks

ounn[/QUOTE]
only works with Oscar protocol (AIM) not msn or jabber

---

### Post by brian g on 2005-10-12
how the heck do I install gaim-rythmbox on Ubuntu?

---

### Post by edm00se on 2005-12-02
I am having a bit of trouble myself with this package. I run ./configure and it tells me that my gaim version is not higher than 0.79 when it is really 1.5.0
  Any thoughts?

---

### Post by JazzCrazed on 2006-03-02
I'm encountering this exact same error:

```
checking for gaim... configure: error: Package requirements (gaim >= 0.79) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the gaim_CFLAGS and gaim_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
```

I see that it's suggesting I check the PKG_CONFIG_PATH variable, but I don't know where to find that. I checked the configure file, where the error text is stored, but couldn't find the variable anywhere in there.

Any help with this is much appreciated!

Thanks in advance,
JazzCrazed

---

