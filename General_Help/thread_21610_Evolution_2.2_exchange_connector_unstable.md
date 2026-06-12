---
title: "Evolution 2.2 exchange connector unstable"
date: 2005-03-23
forum: General Help
---

### Post by mcptron on 2005-03-23
Evolution 2.2 on hoary with the exchange connector to access a MS Exchange 2000 server behaves extremely unstable. The exchange backend process crashes nearly every time when opening the calendar view or accessing the active directory address lookup (address autocompletion) and causes an evolution application crash also.

Evolution 2.0 on warty was quiet stable... has anyone experienced the same problems? Any ideas or solutions?

I'm currently using:
ii  evolution      2.2.1.1-0ubunt The groupware suite
ii  evolution-data 1.2.1-0ubuntu1 evolution database backend server
ii  evolution-exch 2.2.1-0ubuntu1 Exchange plugin for the Evolution groupware
ii  evolution-webc 2.2.0-0ubuntu1 webcal: URL handler for GNOME and Evolution
ii  libcamel1.2-3  1.2.1-0ubuntu1 Generic messaging library for evolution data
ii  libebook1.2-3  1.2.1-0ubuntu1 Client library for evolution address books
ii  libecal1.2-2   1.2.1-0ubuntu1 Client library for evolution calendars
ii  libedata-book1 1.2.1-0ubuntu1 Backend library for evolution address books
ii  libedata-cal1. 1.2.1-0ubuntu1 Backend library for evolution calendars
ii  libedataserver 1.2.1-0ubuntu1 Utility library for evolution data servers
ii  libedataserver 1.2.1-0ubuntu1 Utility library for evolution data servers

tanks in advance,
mike

---

### Post by phsims on 2005-03-23
I am!  Seems to have been reported as bug # 8071

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8071](https://bugzilla.ubuntu.com/show_bug.cgi?id=8071)

---

### Post by gil-galad on 2005-03-23
[QUOTE=mcptron]Evolution 2.2 on hoary with the exchange connector to access a MS Exchange 2000 server behaves extremely unstable. The exchange backend process crashes nearly every time when opening the calendar view or accessing the active directory address lookup (address autocompletion) and causes an evolution application crash also.

Evolution 2.0 on warty was quiet stable... has anyone experienced the same problems? Any ideas or solutions?

I'm currently using:
ii  evolution      2.2.1.1-0ubunt The groupware suite
ii  evolution-data 1.2.1-0ubuntu1 evolution database backend server
ii  evolution-exch 2.2.1-0ubuntu1 Exchange plugin for the Evolution groupware
ii  evolution-webc 2.2.0-0ubuntu1 webcal: URL handler for GNOME and Evolution
ii  libcamel1.2-3  1.2.1-0ubuntu1 Generic messaging library for evolution data
ii  libebook1.2-3  1.2.1-0ubuntu1 Client library for evolution address books
ii  libecal1.2-2   1.2.1-0ubuntu1 Client library for evolution calendars
ii  libedata-book1 1.2.1-0ubuntu1 Backend library for evolution address books
ii  libedata-cal1. 1.2.1-0ubuntu1 Backend library for evolution calendars
ii  libedataserver 1.2.1-0ubuntu1 Utility library for evolution data servers
ii  libedataserver 1.2.1-0ubuntu1 Utility library for evolution data servers

tanks in advance,
mike[/QUOTE]
 I have had similiar problems with Evolution 2 in general.

---

### Post by mcptron on 2005-03-24
Evolution 2.0.x crashed also sometimes, but most times only directly after starting it. Once it ran, it was quiet stable.

I wonder if there is a possibility to downgrade to evolution 2.0 on hoary until the 2.2 will be fixed. Does anybody know how to do this without screwing up the hoary repository sources? Can i simply add the warty sources to synaptic and install evolution 2.0?

---

### Post by sfranklin on 2005-03-26
[QUOTE=mcptron]Evolution 2.2 on hoary with the exchange connector to access a MS Exchange 2000 server behaves extremely unstable. The exchange backend process crashes nearly every time when opening the calendar view or accessing the active directory address lookup (address autocompletion) and causes an evolution application crash also.[/QUOTE]

I'm running it all day at work and am seeing the same thing.

The connector seems to have another problem as well.  The OWA interface on the Exchange server where I work is on port 82 instead of the standard port 80.  In Warty the connector had no problem working with this.  In Hoary it seems to be stripping the ":82" off the server address "exchange.myjob.org:82".  The error message says it can't find the path at "exchange.myjob.org."  No ":82".

---

