---
title: "installed pidgin, now guifications?"
date: 2007-06-15
forum: General Help
---

### Post by billybag on 2007-06-15
anyone got instructions that anybody can understand, on how to install guifications on pidgin? The ones that come with the archive work for me until i get

```
checking for PIDGIN... configure: error: Package requirements (pidgin purple) were not met:

Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'gtk+-2.0', required by 'Pidgin', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PIDGIN_CFLAGS
and PIDGIN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
ummm.... what?

so i read the instructions again
```
Next run the configure script.  If you have installed Pidgin and it's headers
in the standard location, then configure should find the Pidgin source. If not,
you need to set the environment variable PKG_CONFIG_PATH to point to the
directory containing pidgin.pc before running configure. You should configure
with the same prefix was used for Pidgin (for packages this would be /usr), eg:

  PKG_CONFIG_PATH=/usr/local/lib/pkgconfig ./configure --prefix=/usr

```
...blinks twice at the screen and looks around....

the last time i installed it, it was for gaim and it was already in synaptic i believe... it must have been because i don't think i could have installed it myself with directions like that. i still have it installed according to synaptic... but it is for gaim and not pidgin. so anyway... how do you install guification for pidgin

---

### Post by zvacet on 2007-06-16
[http://ubuntuforums.org/showthread.php?t=441363&highlight=purple+package]("http://ubuntuforums.org/showthread.php?t=441363&highlight=purple+package")

---

