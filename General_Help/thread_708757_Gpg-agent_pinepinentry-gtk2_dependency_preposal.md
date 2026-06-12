---
title: "Gpg-agent pinepinentry-gtk2 dependency preposal"
date: 2008-02-26
forum: General Help
---

### Post by dmitrijledkov on 2008-02-26
gnupg-agent package does not work after install. Gpg sais problem with agent - disabling gpg agent. After reading wiki the upgrade problems from feisty (unrelated I have clean first time install gutsy). I made ~/.gnupg/gpg-agent.conf as shown in the [wiki]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto#head-93b1444c654a06e95ca451ab5375207566e0a708").
And I realised that I need pinepinentry-gtk2 to be installed.

Suggestion since use-agent in ~/.gnupg/gpg.conf by default is uncommented in gutsy maybe pinepinentry-gtk2 should be installed as dependency with appropriate ~/.gnupg/gpg-agent.conf being created.
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.6 (GNU/Linux)

iD4DBQFHxLk0IfDtEE/1weQRAoAtAJ47pGWffoJDpDrUNXzy2SrRTdEmBQCY0+mD
J32zwlk8Q659jhBV4wXnsg==
=hsX3
-----END PGP SIGNATURE-----

---

### Post by dermoth on 2008-04-28
Had same problem after upgrade from Gutsy to Hardy. I'm not sure what changed but it stopped working.

The exact steps outlined fixed the problem, and it's quite critical for anyone using encryption in emails.

---

### Post by mattack on 2008-05-06
That didn't actually fix it for me.
The problem is Seahorse not recognizing that gnupg-agent is a valid gpg passphrase caching agent.
See this bug: [https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/217270]("https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/217270")

---

