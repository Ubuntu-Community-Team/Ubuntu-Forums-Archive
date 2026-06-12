---
title: "[SOLVED] PGP Keys, Seahorse, GnuPG, Idea support"
date: 2007-09-19
forum: General Help
---

### Post by StewartM on 2007-09-19
I installed Seahorse for management of my PGP keys. They're legacy PGP keys (RSA, MD5, IDEA algorithm) created on my defunct Windows box.

The keyrings load into Seahorse fine. However, when I try to change the passphrase on one of them, nothing happens.

I suspect that this is because they are 'legacy' PGP keys (RSA, MD5, IDEA) and GnuPG doesn't support the IDEA algorithm anymore (I vaguely recall this). I also vaguely recall, though, that there's a plugin that will allow GnuPG to recognize keys using IDEA. I don't see it (so far) on the GnuPG site.

(I could run a version of PGP under WINE, but I'd rather not if GnuPG can use these keys).

Stewart

---

### Post by StewartM on 2007-09-20
Found out that's probably it:

From: [http://www.gnupg.org/documentation/faqs.html](http://www.gnupg.org/documentation/faqs.html)

3.3) How do I include support for RSA and IDEA?

RSA is included as of GnuPG version 1.0.3.

The official GnuPG distribution does not contain IDEA due to a patent restriction. The patent does not expire before 2007 so don't expect official support before then.

However, there is an unofficial module to include it even in earlier versions of GnuPG. It's available from <ftp://ftp.gnupg.dk/pub/contrib-dk/>. Look for:

   idea.c.gz        (c module)
   idea.c.gz.sig    (signature file)

   ideadll.zip      (c module and win32 dll)
   ideadll.zip.sig  (signature file)

Compilation directives are in the headers of these files. You will then need to add the following line to your ~/.gnupg/gpg.conf or ~/.gnupg/options file:

load-extension idea 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

So, probably better to continue to use PGP via WINE until IDEA is included; or maybe to use
PGP under WINE to revoke my old keys and create new GnuPG-compliant ones.

Stewart

---

