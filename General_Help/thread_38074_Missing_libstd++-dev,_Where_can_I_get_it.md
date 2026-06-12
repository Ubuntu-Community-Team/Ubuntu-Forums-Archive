---
title: "Missing libstd++-dev, Where can I get it?"
date: 2005-05-29
forum: General Help
---

### Post by SGC on 2005-05-29
I tried to compile the pre-release of smb4k , ./configure gives me the followiong error:

configure: error: Your Installation isn't able to compile simple C++ programs.
Check config.log for details - if you're using a Linux distribution you might miss
a package named similiar to libstd++-dev.

I didn't find the package that called libstd++-dev, and installing libstdc++6-4.0-dev doeS not helps.

**EDIT:** installing g++ solve the problem.

---

