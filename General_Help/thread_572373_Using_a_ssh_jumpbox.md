---
title: "Using a ssh jumpbox"
date: 2007-10-10
forum: General Help
---

### Post by phillips321 on 2007-10-10
Hi guys,

I currently connecting to my home pc using ssh then tunnel 5900 over it to give me a gui.

If possible would i be able to put a box in between the connection the accepts ssh connections? then i ssh around my lan to get to the pc with the gui on it.

Current set-up

Work---<----<----<----<----Home PC

Proposed set up

Work---<----<--Jumpbox--<----<----Home PC

What i would like to do is not connectly directly to the Home Pc but instead place a jumpbox on my network at home that i can connect to first

then i connect to the jump box, then from the jump box i connect to the home pc using ssh, then have port 5900 forwarded through the jumpbox so i can get a gui up

P.s. jumpbox will not have a gui itself, it will simply be a terminal box.

---

