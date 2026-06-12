---
title: "Ubuntu Pro question"
date: 2024-06-04
forum: General Help
---

### Post by DigiAngel on 2024-06-04
Hey all.

I "backup" my ubuntu server by rsyncing pretty much the entire file system to a duplicate machine, minus a few excludes. I'm guessing ubuntu pro ties the license to the machine in some way...and I'm guessing it's stored as a file somewhere. I'd rather not sync that file to a different machine since I'm thinking it will break. Any idea what that file is so I can exclude it? Thank you.

---

### Post by Holger_Gehrke on 2024-06-04
The configuration for pro is stored in /etc/ubuntu-advantage/ and in /var/lib/ubuntu-advantage/. AFAIK the machine-id is stored in /var/lib/ubuntu-advantage/status.json. Take that information with a grain of salt since I don't use pro and gathered it from 'man pro' and a look at the file created by 'pro collect-logs' and the places the contents of this archive reference.

Holger

---

