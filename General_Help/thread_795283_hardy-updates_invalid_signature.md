---
title: "hardy-updates invalid signature"
date: 2008-05-15
forum: General Help
---

### Post by karlatsaic on 2008-05-15
My update manage (Hardy 8.04) asked me to update my configuration this a.m. Today (and yesterday) most of these updates had to do with openssh and openssl. Today, during the update, it said I had a security vulnerability in a signature file so I let the update fix it. After that, the update could not finish. I get the error:

W: GPG error:[http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Am I the only one experiencing this? [edit: I get the same error off the US archive]
Thanks in advance for any help

---

### Post by mogwai on 2008-05-15
From reading other posts, I have checked out: [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.2.2 (GNU/Linux)

iD8DBQBIK0HGQJdur0N9BbURAkl0AJwNww9uh/aLSBurS+tpbq9Xos6OkgCgkZ5Z
Nxgur6MV5ecXJ7pEhxF6/Qo=
=0Xal
-----END PGP SIGNATURE-----


This file seems truncated and/or corrupted. I have seen several other GPG keys that are about 10 full lines.
Is this file corrupted? Is this the source of my BADSIG error? :confused:

PS: I have tried ALL the other fixes mentioned in the forums and none have worked.

This appears (to my eyes) to be an error on canonical's end. I might be wrong, but that is the way I am seeing it at the moment.

AND I am not behind a proxy. Have tried this at 2 different sites with direct connections.

Hope this helps someone solve this annoying problem ASAP.


Update: 
Tried  'wget -q [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg) -O- | sudo apt-key add - && sudo apt-get update'
but got 'gpg: no valid OpenPGP data found.'

---

### Post by karlatsaic on 2008-05-15
Well - I do believe someone at canonical fixed the corrupt gpg file (THANKS)  for hardy-updates as I now can check all packages for updates (I have 48 packages in my sources list) and the error is gone.

---

