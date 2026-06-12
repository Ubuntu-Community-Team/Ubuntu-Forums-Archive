---
title: "default ubuntu clipboard, and command line usage?"
date: 2007-03-25
forum: General Help
---

### Post by mooseydoom on 2007-03-25
Hey, I'm kinda confused about which is the default ubuntu (Edgy / Gnome) clipboard manager.  I guess glipper is supposed to be installed in Feisty, though glipper doesn't seem to be in the repository at the moment.  gcm doesn't seem to be installed, nor is klipper... so what's handling my copying and pasting?

And can I access the clipboard from the command line? (ie to copy text into the clipboard, is there something like ```
echo "hello" | clipboard
```

Thanks in advance :biggrin:

edit: Solution = xsel

---

### Post by os.getlogin on 2007-04-09
did this get resolved?  I'd like to know too.

---

### Post by eexpress on 2007-04-09
i only know xclip can get selected text. i also want fetch the text(web-links and so on) from clipboard, which i want to deal within my bash.

i had read a lot, but no found.

---

### Post by mooseydoom on 2007-04-10
I think Ubuntu (Edgy) uses the X11 clipboard.  This article was useful:
[http://www.pixelbeat.org/docs/xclipboard.html](http://www.pixelbeat.org/docs/xclipboard.html)

as for cutting and pasting, 'xsel --clipboard' does the trick.  :D  (I had to install xsel from the package manager first)

---

### Post by eexpress on 2007-04-10
great. thanks

so many x prefix command, haha.

---

### Post by rogerhc on 2008-02-18
Try Gnome's Glipper clipboard manager.

[https://help.ubuntu.com/community/glipper](https://help.ubuntu.com/community/glipper)

:popcorn:

---

