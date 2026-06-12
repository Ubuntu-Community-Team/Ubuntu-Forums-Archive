---
title: "Evolution 2.10 libexchange-storage Error"
date: 2007-04-18
forum: General Help
---

### Post by Aurelius33 on 2007-04-18
I'm using Ubuntu Edgy (2.6.17-11 kernel) and have been using it for about a week (Beryl is freakin sweet).  I've already uninstalled Evolution 2.8 (came with the distro).  After trying to compile Evolution 2.10, I get the following error:

checking for CAMEL_EXCHANGE... configure: error: Package requirements (libbonoboui-2.0 >= 2.4.2 libglade-2.0 libgnomeprint-2.2 libgnomeprintui-2.2 gthread-2.0 gconf-2.0 camel-provider-1.2 libebook-1.2 >= 1.9.4 libedataserverui-1.2 libexchange-storage-1.2 >= 1.9.4 libecal-1.2) were not met:

Requested 'libexchange-storage-1.2 >= 1.9.4' but version of libexchange is 1.8.1

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables CAMEL_EXCHANGE_CFLAGS
and CAMEL_EXCHANGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I've racked my brain and can't find a solution.  I'll bet its something simple, I just can't think straight anymore. :-k                While I'd like to finish my compile/install, I'd take an rpm at this point.

---

