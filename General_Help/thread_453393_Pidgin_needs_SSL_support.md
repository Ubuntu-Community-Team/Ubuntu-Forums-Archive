---
title: "Pidgin needs SSL support"
date: 2007-05-24
forum: General Help
---

### Post by PartisanEntity on 2007-05-24
I downloaded the Pidgin source, compiled and installed it, now when I launch pidgin from the terminal I get a message window informing me that MSN requires SSL, and that I should install an SSL library.

Anyone which library I need to install?

Thanks,

---

### Post by gmc on 2007-05-24
> **PartisanEntity said:**
> I downloaded the Pidgin source, compiled and installed it, now when I launch pidgin from the terminal I get a message window informing me that MSN requires SSL, and that I should install an SSL library.

Anyone which library I need to install?

Thanks,

Try installing 'sudo apt-get install libssl-dev' and recompile. Note, you might have to rerun ./configure to get the ssl developement libraries to be included.

Gord

---

### Post by PartisanEntity on 2007-05-24
That was it, thanks very much, I had to recompile and now it is working.

---

### Post by Ryanson on 2007-05-25
I installed the .deb for pidgin, and am getting the SSL error. I looked around, but can't find anything on fixing it with the .deb.

---

### Post by PartisanEntity on 2007-05-25
> **Ryanson said:**
> I installed the .deb for pidgin, and am getting the SSL error. I looked around, but can't find anything on fixing it with the .deb.

In that case try compiling it from source, it's really not that hard and you will be informed about which dependencies you are missing.

---

### Post by gmc on 2007-05-25
> **Ryanson said:**
> I installed the .deb for pidgin, and am getting the SSL error. I looked around, but can't find anything on fixing it with the .deb.

You may want to check and see if libssl (not libssl-dev) is installed. I would assume the deb file of which you speak, has libssl as a dependancy, but maybe not.

Just a thought.

Gord

---

### Post by eternalfire129 on 2007-05-30
yeah that worked great, as a note, make sure a full recompliation and 'code: make install' is done and it should do the trick

---

### Post by rebroad on 2008-02-23
That's a bit of a pain considering how long it took to compile on this rather old Pentium III processor.

It would be nice if the configuration script could be modified to make a clear warning that it is about to be compiled without SSL support so as to give the person compiling a chance to download libssl-dev first!

---

### Post by rebroad on 2008-02-23
Well. I re-configured and recompiled, but it's still giving the same error about lacking SSL support.

Are we sure it isn't libgnutls-dev that's required instead? (I saw that mentioned in the configure files as being used for SSL support.)

---

### Post by Yellow Pasque on 2008-02-23
> **rebroad said:**
> Well. I re-configured and recompiled, but it's still giving the same error about lacking SSL support.

Are we sure it isn't libgnutls-dev that's required instead? (I saw that mentioned in the configure files as being used for SSL support.)
You have both libssl0.9.8 and libssl-dev, correct?

---

