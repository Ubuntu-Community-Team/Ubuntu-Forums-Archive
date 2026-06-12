---
title: "Command to send text packet?"
date: 2007-11-07
forum: General Help
---

### Post by Dudsmacka2 on 2007-11-07
I've written a simple listen server to receive a string, and take a action based upon the contents of that string.

I was wondering if there is any linux util that I can send a blurb of text to an ip address / port of a host machine?

Thanks in advance.

---

### Post by PaulFr on 2007-11-07
Have you tried ```
telnet <hostname> <port>
```You can then type the string and press Enter to send it (if in line mode). **man telnet** for details.

---

