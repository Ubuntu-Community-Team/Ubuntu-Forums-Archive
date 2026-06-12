---
title: "Help installing a new gnutls package"
date: 2014-08-09
forum: General Help
---

### Post by project722 on 2014-08-09
I'm running Ubuntu 14.04LTS with libgnutls26 and libgnutls28. gnutls26 is at 2.2.23 and 28 is on 3.2.11. According to the security advisory CVE-2014-0092, I need to patch gnutls26 2.2.23 and update gnutls28 to 3.2.12. When I ran an apt-get upgrade libgnutls28 it ran ok but I'm still at 3.2.11. How can I force apt-get to pull the most up to date version?  

I'm also considering doing this manually by going to [ftp://ftp.gnutls.org/gcrypt/gnutls/v3.2](ftp://ftp.gnutls.org/gcrypt/gnutls/v3.2) to get the packages. I can see 3.2.12 but its an tar.xz with a corresponding smaller file that's got a tar.xz.sig extension. I have no idea what to do with these. I suppose I can use Alien to convert these into a format that I can use in Ubuntu but I'd like if I do this method how do I then force it to upgrade the existing gnutls package I have instead of installing another instance? Anybody got any suggestions?

---

### Post by oldos2er on 2014-08-09
Moved to General Help.

---

### Post by mc4man on 2014-08-09
Here are the recent changelogs via synaptic - 
> gnutls26 (2.12.23-12ubuntu2.1) trusty-security; urgency=medium

  * SECURITY UPDATE: memory corruption due to server hello parsing
    - debian/patches/CVE-2014-3466.patch: validate session_id_len in
      lib/gnutls_handshake.c.
    - CVE-2014-3466

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Sun, 01 Jun 2014 11:03:46 -0400

gnutls26 (2.12.23-12ubuntu2) trusty; urgency=medium

  * SECURITY UPDATE: certificate validation bypass
    - debian/patches/CVE-2014-0092.patch: correct return codes in
      lib/x509/verify.c.
    - CVE-2014-0092

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Mon, 03 Mar 2014 14:10:30 -0500


> gnutls28 (3.2.11-2ubuntu1) trusty; urgency=medium

  * Resynchronise with Debian.  Remaining changes:
    - Drop gnutls-bin and -doc since we want to use the versions in gnutls26
      as the defaults instead.
  * Add arm64 and ppc64el to the list of non-ia64 architectures on which
    guile-gnutls is built.

 -- Colin Watson <cjwatson@ubuntu.com>  Wed, 05 Mar 2014 10:31:28 +0000

gnutls28 (3.2.11-2) unstable; urgency=high

  * Bump version of Build-Depends on libp11-kit-dev, as required by 3.2.11.
  * 20_CVE-2014-0092.diff by Nikos Mavrogiannopoulos: Fix certificate
    validation issue. CVE-2014-0092

 -- Andreas Metzler <ametzler@debian.org>  Sat, 01 Mar 2014 08:48:21 +0100


So both have already been patched.

---

### Post by project722 on 2014-08-09
Ok that works for me thanks. But there are newer versions of gnutls available. What determines what gets added to the apt sources database for download? And when? 

Also - is there a way to check changelogs for a package via the shell instead of having to install synaptic? Isn't that a just a GUI front end for apt?

---

### Post by oldos2er on 2014-08-09
Install *apt-listchanges* which does what you're asking for.

---

### Post by ian-weisser on 2014-08-10
> **project722 said:**
> What determines what gets added to the apt sources database for download? And when?

See [https://wiki.ubuntu.com/TimeBasedReleases](https://wiki.ubuntu.com/TimeBasedReleases) for a thorough explanation of what get added to the Ubuntu repositories and when.

---

### Post by project722 on 2014-08-10
Thanks all!!

---

