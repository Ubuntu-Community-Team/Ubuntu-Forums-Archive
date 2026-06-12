---
title: "terminal options for pdfpc"
date: 2017-09-06
forum: General Help
---

### Post by psionman on 2017-09-06
I am trying to run pdfpc with some options but I can't understand the documentation
[URL="http://manpages.ubuntu.com/manpages/zesty/man1/pdfpc.1.html"]
http://manpages.ubuntu.com/manpages/zesty/man1/pdfpc.1.html[/URL]

I've tried

pdf_presenter_console path.pdf -d120

pdf_presenter_console path.pdf -d,120

pdf_presenter_console path.pdf -d --120

pdf_presenter_console path.pdf -d, --120

pdf_presenter_console path.pdf -d, 120

nothing works

Help

---

### Post by him610 on 2017-09-06
I was not aware *pdfpc* existed; however I accept this as a challenge.:KS

Try this from the command line...
```
pdfpc -C path.pdf
```
It will show the file with the Time of Day displayed. Not sure if it is displayed on primary monitor or secondary monitor since I only have one.

You can navigate using, *Page Down, Page Up, Home, End *keys while *Esc* key exits. 
A middle-mouse click will fill the screen with a preview of all pages in the document. A left-mouse click on a particular page will load that page.

Note: It would not accept *-d=N* option; however, the longer version, *--duration=N* does work. So, try this....

```
pdfpc --duration=120 path.pdf
```

---

### Post by mc4man on 2017-09-07
> **psionman said:**
> 
I've tried

pdf_presenter_console path.pdf -d120

pdf_presenter_console path.pdf -d,120

pdf_presenter_console path.pdf -d --120

pdf_presenter_console path.pdf -d, --120

pdf_presenter_console path.pdf -d, 120



you almost had it
```
-d 120
```

---

### Post by psionman on 2017-09-07
Doh! Thanks mc4man

---

