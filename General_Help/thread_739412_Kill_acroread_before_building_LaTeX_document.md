---
title: "Kill acroread before building LaTeX document"
date: 2008-03-29
forum: General Help
---

### Post by owains on 2008-03-29
I'm finding it rather annoying to have to close the pdf I'm working on every time I want to update with pdflatex. Is there a command that will close a specific acroread window that I can run before pdflatex? I couldn't find an argument for acroread itself...

I know there's a way of [matching windows]("http://wiki.compiz-fusion.org/WindowMatching") that is used by Compiz Fusion, I'm not sure if that can be used at all.


Thanks for any help.

---

### Post by gaussian on 2008-03-29
> **owains said:**
> I'm finding it rather annoying to have to close the pdf I'm working on every time I want to update with pdflatex. Is there a command that will close a specific acroread window that I can run before pdflatex? I couldn't find an argument for acroread itself...

I know there's a way of [matching windows]("http://wiki.compiz-fusion.org/WindowMatching") that is used by Compiz Fusion, I'm not sure if that can be used at all.


Thanks for any help.

This is really annoying thing with acroread and my proposed solution is to install kpdf (KDE PDF reader). With that you can leave the pdf-document open and when you compile your document the KPDF window will autorefresh.

---

### Post by owains on 2008-03-30
Thanks for your suggestion regarding kpdf. It reminded my that ubuntu has its own pdf viewer evince. This has the same ability to refresh an open pdf, so I'm using that rather than acroread. It seems to render pages more quickly too, which is a bonus, though text does look slightly blurry.

Thanks again :D

---

