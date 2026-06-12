---
title: "Windows Fonts Broke My OpenOffice"
date: 2006-09-06
forum: General Help
---

### Post by tonyr1988 on 2006-09-06
I installed WinFonts per a HowTo on these forums (forgot exactly where). It was working fine, then I realized my OO.o wasn't working. I've opened a few .doc files (that worked before), and all I see is a blank OO.o document. I noticed that the font says Times New Roman (it does the same thing in AbiWord).

I went through and deleted all the fonts that were Windows-ey. It still doesn't work. And it still says Times New Roman. Changing the font doesn't help - it just changes back.

What should I do?

---

### Post by tonyr1988 on 2006-09-06
I randomnly plugged in:

>  sudo dpkg-reconfigure fontconfig

And it worked. I opened my /usr/share/fonts folder and can't find Times New Roman anywhere, but it's still saying that it's using it.

Oh well, it's working great - I'm not complaining.

---

