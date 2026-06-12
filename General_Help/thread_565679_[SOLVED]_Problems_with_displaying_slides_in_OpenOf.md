---
title: "[SOLVED] Problems with displaying slides in OpenOffice.org Spreadsheet"
date: 2007-10-02
forum: General Help
---

### Post by Baby Boy on 2007-10-02
Hi, my college has started and I need to view some presentations as slide shows made in PowerPoint. Everything works fine under PowerPoint, but in OpenOffice.org Spreadsheet, letters are out of the slide background frame and they sometimes mix. It's like the slide frame is too small, so when I try to do a slide show, I can't see half of the words. Can someone help me?

---

### Post by peabody on 2007-10-02
It's probably a font issue.  A way to tell would be to view the same presentation on a windows machine using OpenOffice.org for Windows.

---

### Post by Baby Boy on 2007-10-02
However, I would like to do it in Ubuntu. If I wanted to log to Windows I would use the PowerPoint ;).

---

### Post by peabody on 2007-10-02
I know that, what I'm saying is, try it and see if it's related to the fonts.  If it is, then we can work on that, like installing the relevant fonts on your Ubuntu system.

---

### Post by Baby Boy on 2007-10-05
Sorry it took me two days to reply, but better late than never.

I've tried to open the presentation in WinXP using the OpenOffice.org for Windows. There was no  program like OpenOffice.org Presentation in the Windows version but OpenOffice.org Impress, but I suppose that's the same thing. And the presentation works just fine, no errors. 

Why doesn't it work in Ubuntu?

---

### Post by vanadium on 2007-10-05
Very likely a font issue. The font used might be for example Arial, while that one might not be installed on your Ubuntu system. The font that Ubuntu uses instead is wider than the Arial font. The Microsoft core fonts can be easily installed in Ubuntu using Synaptic.

---

### Post by stchman on 2007-10-05
> **Baby Boy said:**
> Hi, my college has started and I need to view some presentations as slide shows made in PowerPoint. Everything works fine under PowerPoint, but in OpenOffice.org Spreadsheet, letters are out of the slide background frame and they sometimes mix. It's like the slide frame is too small, so when I try to do a slide show, I can't see half of the words. Can someone help me?

You would not use the spreadsheet program to view Powerpoint stuff, use Impress.  If it is a font issue install the Microsoft core fonts.

```
sudo apt-get install msttcorefonts
```

---

### Post by Baby Boy on 2007-10-05
Yep, that was it. After installing those fonts, everything looks like it should. 

Thanks :D

---

