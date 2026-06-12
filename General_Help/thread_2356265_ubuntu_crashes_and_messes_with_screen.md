---
title: "ubuntu crashes and messes with screen"
date: 2017-03-21
forum: General Help
---

### Post by guidotrucco on 2017-03-21
Hello, I've got a fairly old 32 bit pc with 2GB RAM and sometimes with no apparent reason (I don't think I'm overwhelming the computer with too many tasks), Ubuntu crashes and the screen looks like this: [ATTACH=CONFIG]274257[/ATTACH][ATTACH=CONFIG]274258[/ATTACH].
I have Windows 7 installed in the computer as well and it works without a single fail. I got tired of this problem and changed Ubuntu with LXLE, but it still happens. Did anyone have the same problem?

PS: Sorry for the bad English, it's not my first language.

---

### Post by ajgreeny on 2017-03-21
Hi guidotrucco, and welcome to the forums.

Tell us more about the computer hardware, particularly the graphics it has, as the screenshots look as if it is a graphic card or driver problem.
Use terminal command ```
lspci | grep VGA
```and post back here the output.

---

