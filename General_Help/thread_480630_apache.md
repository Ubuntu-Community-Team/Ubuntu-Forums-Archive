---
title: "apache"
date: 2007-06-21
forum: General Help
---

### Post by Silenus on 2007-06-21
I have two computers on a network, and the windows computer doesn't seem to be able to read the apache server off my ubuntu desktop, when i try to access the site, it just reports page not found, but others outside of the network can read it.

---

### Post by AlexThomson_NZ on 2007-06-21
A bit vague there.  Are you using IE on the winbox?  If so, I think you need the whole http:// prefix.  Can you ping the ubuntu desktop from the winbox?  Can you telnet onto port 80 (or whatever port apache is listening on) from it?

---

### Post by Silenus on 2007-06-21
Sorry for the vagueness I was in a bit of a rush, well it is firefox and msn explorer, I will try the http prefix.

---

### Post by Silenus on 2007-06-21
Thank you for the reply, I was able to connect by using the local address with the port 80 suffix.

---

