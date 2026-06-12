---
title: "okular doesn't not fit pdfs correct on paper"
date: 2013-02-06
forum: General Help
---

### Post by linuxcss on 2013-02-06
When printing okular does not expand the pdf to whole page correctly the  image is small and centered in the printed paper page, using evince it prints correctly.

Any fix for this for okular or a setting I am missing?

ps: unfortunately using evince in other cases has bugs:
[http://ubuntuforums.org/showthread.php?t=2104574 ]("http://ubuntuforums.org/showthread.php?t=2104574")

I like okular, would like to get the above mentioned issue resolved.

using okular 0.15.4 under xubuntu 12.10

---

### Post by SeijiSensei on 2013-02-06
Have you checked the settings for your printer in CUPS?  An easy way to manage printing in CUPS is to navigate to [http://localhost:631/](http://localhost:631/) and proceed from there.  If you need to do something that requires administrative ("root") privileges, enter your password when prompted.  It's the equivalent of running something with "sudo".

I've never had problems printing from Okular, but I've only used it with KDE.  A quick review of Okular's settings does not show much about printing.  I think it expects CUPS and the printer drivers to handle formatting.

---

### Post by orb9220 on 2013-02-06
>  I think it expects CUPS and the printer drivers to handle formatting.

Yep any margin errors where looks fine in Okular but prints out wrong is printer settings. Two places Printer internal settings override printing application settings or printing handler margins and specifically turning off header & footers,Check margins settings,etc.. can lead to these kind of issues.
.

---

