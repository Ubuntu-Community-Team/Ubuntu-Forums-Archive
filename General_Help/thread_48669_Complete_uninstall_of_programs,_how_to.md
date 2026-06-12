---
title: "Complete uninstall of programs, how to?"
date: 2005-07-13
forum: General Help
---

### Post by Battery on 2005-07-13
In a hurry I accidently installed xmms and mplayer before installing any codecs, atleast the ubuntu guide does it in this order...

Now both simply crash when I try to open a file with em.

So I guess I need to uninstall the programs. I know the apt-get remove command doesn`t remove all of the files, and I dont think it did enogh cause the programs still crash.

So how should I proceed?

---

### Post by BigCdaAnswer3 on 2005-07-13
[QUOTE=Battery]In a hurry I accidently installed xmms and mplayer before installing any codecs, atleast the ubuntu guide does it in this order...

Now both simply crash when I try to open a file with em.

So I guess I need to uninstall the programs. I know the apt-get remove command doesn`t remove all of the files, and I dont think it did enogh cause the programs still crash.

So how should I proceed?[/QUOTE]


dpkg -L <packagename> should tell you what files (if any) are installed for any package

---

