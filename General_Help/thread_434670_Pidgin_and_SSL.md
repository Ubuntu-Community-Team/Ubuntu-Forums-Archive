---
title: "Pidgin and SSL?"
date: 2007-05-06
forum: General Help
---

### Post by mahy on 2007-05-06
Hello everybody,

i chose to download the new Pidgin 2.0 and give it a try. Donwloaded, unpacked, ran ./configure. It went smoothly. But then i looked at the summary when the configure script ended. It contained a line that sort of scared me off:

```
SSL Library/Libraries......... : None (MSN and Google Talk will not work without SSL!)
```

I have libgtk2.0-dev, libglib2.0-dev and libssl-dev all installed. What's wrong with it? Any ideas? TIA

---

### Post by coolcalt on 2007-05-06
I had the same issue 

before I got to see 
SSL Library/Libraries......... : Mozilla NSS

I used Synaptic package manager to search for and add any development packages that it seemed to be looking for (which reminds me I need a journal for my computer.)

libraries I added include but may not be all of them, and some are not required, they are just what I have installed related to ssl, nss, and nspr.
libnspr-dev
libnspr4
libnspr-0d
libnss3
libnss3-0d
libnss-db
libnss-dev
libssl-0.9.7
libssl0.9.7-dbg
libssl0.9.8
libssl-dev
open-ssl
ssl-cert

I didn't have to add any options to ./configure

I did have to keep running ./configure and adding packages till it worked.

Good luck.  Perhaps someone else can refine my list and shorten the list to what is actually required.

---

### Post by Nano on 2007-05-06
If I'm not wrong the package libnss-dev should be enough to compile it with msn support

---

### Post by mahy on 2007-05-07
> **Nano said:**
> If I'm not wrong the package libnss-dev should be enough to compile it with msn support

Wow, that fix it! THX to both of you guys!

---

### Post by bogyit on 2007-05-07
libnss-dev worked for me, I'm on Xubuntu 5.10, thanks :)

---

### Post by moredhel on 2007-05-07
you could use the .deb from getdeb.net to save you some trouble on future partitions ;)

---

### Post by khughitt on 2007-05-07
Cool. that worked for me as well..

Initially when i ran configure, the output was:

```
SSL Library/Libraries......... :  GnuTLS
```

And when i tried to run pidgin after installing, it would not work with google talk (*"Server requires TLS/SSL for login. No TLS/SSL support found." *) After installing libnss-dev however, i re-ran ./configure (and also make + make install) and got:

```
SSL Library/Libraries......... : Mozilla NSS and GnuTLS
```

And pidgin works fine :) I just use the same settings as before, and resource = "gmail" (not sure if it matters though).

thanks!

---

### Post by Nano on 2007-05-07
And don't forget to install the gstreamer headers in order compile it with sound suppot ;)

---

### Post by mahy on 2007-05-08
> **moredhel said:**
> you could use the .deb from getdeb.net to save you some trouble on future partitions ;)

IMO, that package is for Feisty only...

I'd rather build my own one with checkinstall.

---

### Post by starlily on 2007-06-27
HOW I FIXED THE TLS/SSL ERROR FOR GOOGLE TALK IN PIDGIN

In a couple of Really Easy Steps:

Since there is no Pidgin Package for Ubuntu yet, I assume you are already building from the source.

do 'make clean' if you have already built it and you get the error.

Open Synaptic Package Manager, search for and install 'libgnutls-dev'

When you run ./configure to build Pidgin, do './configure --enable-gnutls=yes', then look for
SSL Library/Libraries......... : GnuTLS
when it finishes.

do sudo make install (as normal) to finish.

You're Welcome.

Lily

---

### Post by AvalonSkies on 2007-07-07
> **Nano said:**
> If I'm not wrong the package libnss-dev should be enough to compile it with msn support

I had the same problem, this worked for me too. Thanks, mate.

---

### Post by LukeCarrier on 2007-09-25
Doesn't work :'(

---

### Post by seren6ipity on 2007-10-28
Lily, you are a star. Works for me too. Thanks.

---

### Post by stolid_agnostic on 2007-10-29
dot

worked for me!  :D

---

