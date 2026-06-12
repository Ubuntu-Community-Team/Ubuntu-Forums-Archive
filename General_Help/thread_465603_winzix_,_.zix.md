---
title: "winzix , *.zix ???"
date: 2007-06-05
forum: General Help
---

### Post by fdrake on 2007-06-05
hi there i just downloaded a file (633.8MB) in zix format. i did a little research on it , and i found out that it's an archive format (see links: [http://en.wikipedia.org/wiki/Winzix](http://en.wikipedia.org/wiki/Winzix)   , [http://ukpcrepair.com/dlsite/prog.html](http://ukpcrepair.com/dlsite/prog.html))
I wasn't able to find any linux version of a software able to extract the file. But i did find a windows version of it . so i tried it on my vista partition it looks like its working (it doesn't have any loading bar) but suddenly stops working. i can't figure out the problem, file corruption or incompatibility with my vista machine, that's why i'd like to try it on a linux machine.  thanks in advance..

---

### Post by yabbadabbadont on 2007-06-05
You could try running it using WINE since WINE lets you configure which version of Windows API is available.

---

### Post by fdrake on 2007-06-05
i'll give a try

---

### Post by fdrake on 2007-06-05
during the installation i have an error message saying that it's unable to register the DLL/OCX :D||RegisterServer failed; code 0x80070005.(see screenhot) i clicked retry many time but the same message appears so a tried ignore. after the installation i try to lunch the prog. but nothing happens , see below the output :

i'll keep googling around , thanks anyway

---

### Post by mbsullivan on 2008-06-04
Hi All,

Despite the fact that this is an old (archived) thread, for future reference the following may be helpful:

The .zix "compression" is worthless, and "WinZix" as a program is packaged with AdWare. So, little worthwhile content is compressed with a .zix extension.

See [here]("http://www.kennethsorling.se/scams/zix_file_format.htm") and [here]("http://www.kennethsorling.se/scams/zix_2_file_format.htm") for (reverse engineered) details about the file formats.

The author of the previous two pages provides a (Windows) [utility]("http://www.kennethsorling.se/software/unzixwin.htm") for extracting the contents of a zix file. However, I'd just throw it away if I were you.

Mike

---

