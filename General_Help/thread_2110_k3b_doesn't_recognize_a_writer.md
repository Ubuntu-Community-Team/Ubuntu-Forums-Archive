---
title: "k3b doesn't recognize a writer?"
date: 2004-10-25
forum: General Help
---

### Post by syNapse on 2004-10-25
I cant seem to get k3b to see my burner, it will see it as a reader but not a writer, and therefore I cannot burn anything.
Anyone no of a solution?

Thanks

---

### Post by jdong on 2004-10-25
:-k  :-k dumb guess, but try running K3b as root...

---

### Post by sfw5000 on 2004-10-26
You do have to run k3b as root, but do not do it with sudo. You need to open the root terminal and launch k3b from there. If you launch it as sudo, it will screw up the permissions on your /.ICEauthority file and you won't be able to log back into gnome. Strange bug that several people have posted about.

Sam

---

