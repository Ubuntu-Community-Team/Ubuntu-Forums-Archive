---
title: "Mass &quot;open, save as, overwrite existing&quot; of office documents?"
date: 2015-04-27
forum: General Help
---

### Post by Roasted on 2015-04-27
Hello friends. Long story short, I have nearly a thousand doc files that I recovered from a drive on a user's computer. The files open flawlessly in Libre Office but quite a huge portion do not open in Microsoft Office. Oddly enough, if I open a problematic file in Libre Office, File, Save As, keep the existing name, and overwrite the old one, suddenly that file will open in Microsoft Office.

So what I'm looking for is a way to do that on a grand scale. I tried the libreoffice --convert-to option, but oddly enough, it only converts 246 of the files, even if I use a wildcard (*) so it converts ALL of them. I have no explanation for this. It just simply doesn't see the additional few hundred files that are in the same directory that I'm trying to convert.

Can anybody think of any ideas? I'm at a loss in my digging around for how I could further automate this aside from opening each one and getting well acquainted with the CTRL SHIFT S command. :(

---

### Post by steeldriver on 2015-04-27
If convert-to is actually working (for the files that it *does* convert) then I'd be tempted to persevere with that route - perhaps using a loop instead of passing multiple files on a single command line

```

for f in *.docx; do libreoffice --headless --convert-to docx "$f"; done

```

It won't be fast - but perhaps faster than doing it manually...

---

### Post by Roasted on 2015-04-27
Eh, no dice. It acted just like it does on convert-to where some files work but most do not. :(

---

### Post by dragonfly41 on 2015-04-28
I would explore the batch processing (command line) features of AbiWord (in Ubuntu Software Centre).

Get some ideas by google search "abiword batch process"

---

