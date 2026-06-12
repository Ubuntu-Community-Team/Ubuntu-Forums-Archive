---
title: "being verbose while running shell scripts"
date: 2008-04-10
forum: General Help
---

### Post by ShirishAg75 on 2008-04-10
Hi all, 
 Is there anyway that when shell scripts are run, they give  verbose output while running? Either a flag or some other way?

---

### Post by Jussi Kukkonen on 2008-04-10
There's no generic --verbose flag, but this may be handy:
*sh -x <script>*
see *man sh*.

---

