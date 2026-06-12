---
title: "EDITOR variable?"
date: 2008-01-27
forum: General Help
---

### Post by stdPikachu on 2008-01-27
Does anyone know where the EDITOR environment variable is defined? At the moment it's set to the (as a vim user) disgusting nano. How can I change this system-wide without resorting to changing a load of .bashrc's? I can't see it defined in any of the usual places (/etc/skel, /etc/bash, /etc/profile, /etc/environment or /etc/login.defs).

---

### Post by stdPikachu on 2008-01-27
Solved, sort of. Used the tried'n'tested Debain Way and used `sudo update-alternatives --config editor` to change it globally. I still have no idea where it's defined though.

---

