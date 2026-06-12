---
title: "Security Warning About Debian/Ubuntu"
date: 2008-05-13
forum: General Help
---

### Post by OrcaWave on 2008-05-13
I got this from another Ubuntu Board this AM.



Ubuntu Security Notice USN-612-1               May 13, 2008
openssl vulnerability
CVE-2008-0166
===========================================================

A weakness has been discovered in the random number generator used
by OpenSSL on Debian and Ubuntu systems.  As a result of this
weakness, certain encryption keys are much more common than they
should be, such that an attacker could guess the key through a
brute-force attack given minimal knowledge of the system.  This
particularly affects the use of encryption keys in OpenSSH, OpenVPN
and SSL certificates.

This vulnerability only affects operating systems which (like
Ubuntu) are based on Debian.  However, other systems can be
indirectly affected if weak keys are imported into them.

We consider this an extremely serious vulnerability, and urge all
users to act immediately to secure their systems. (CVE-2008-0166)

This advisory also applies to the corresponding versions of
Kubuntu, Edubuntu, and Xubuntu.

== Who is affected ==

Systems which are running any of the following releases:

 * Ubuntu 7.04 (Feisty)
 * Ubuntu 7.10 (Gutsy)
 * Ubuntu 8.04 LTS (Hardy)
 * Ubuntu "Intrepid Ibex" (development): libssl <= 0.9.8g-8
 * Debian 4.0 (etch) (see corresponding Debian security advisory)

and have openssh-server installed or have been used to create an
OpenSSH key or X.509 (SSL) certificate.

All OpenSSH and X.509 keys generated on such systems must be
considered untrustworthy, regardless of the system on which they
are used, even after the update has been applied.

This includes the automatically generated host keys used by OpenSSH,
which are the basis for its server spoofing and man-in-the-middle
protection.

The problem can be corrected by upgrading your system to the
following package versions:

Ubuntu 7.04:
  libssl0.9.8                     0.9.8c-4ubuntu0.3

Ubuntu 7.10:
  libssl0.9.8                     0.9.8e-5ubuntu3.2

Ubuntu 8.04 LTS:
  libssl0.9.8                     0.9.8g-4ubuntu3.1

---

### Post by Monicker on 2008-05-13
More details here:

[http://www.ubuntu.com/usn/usn-612-2]("http://www.ubuntu.com/usn/usn-612-2")
[http://ubuntuforums.org/showthread.php?t=792881]("http://ubuntuforums.org/showthread.php?t=792881")

---

### Post by Kevbert on 2008-05-13
Thanks Orcawave. 4 updated files downloaded from repositories.

---

### Post by thomasaaron on 2008-05-13
Thanks, OrcaWave.

I'm betting this one gets patched from on high in a matter of days.

---

