---
title: "Openoffice Crashes When Opening Document"
date: 2007-11-18
forum: General Help
---

### Post by lordsunland on 2007-11-18
Hi, I'm using Ubuntu 7.10 and I meet a problem. My openoffice always crashes whenever I try to first run the openoffice application then open a document from the "open" button.
However, I can open a document by double-clicking on a document and edit it normally.
Also, it also crashes if only I click the Quickstarter system tray icon.

It used to run Ok before I fixed the problem of font rendering follow the instructions in this post:
[http://ubuntuforums.org/showthread.php?t=406273&highlight=openoffice+font](http://ubuntuforums.org/showthread.php?t=406273&highlight=openoffice+font)

Can anyone help me? Thanks!

---

### Post by yabbadabbadont on 2007-11-18
Open a terminal window and run openoffice from there.  Then try to use the open button to open a document.  If it crashes, hopefully an error message will be printed in the terminal window.  If so, please post the message.

---

### Post by lordsunland on 2007-11-18
> **yabbadabbadont said:**
> Open a terminal window and run openoffice from there.  Then try to use the open button to open a document.  If it crashes, hopefully an error message will be printed in the terminal window.  If so, please post the message.

Hi, thanks for the quick reply!
This is the error message:


/usr/lib/openoffice/program/soffice.bin: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: FT_Library_SetLcdFilter

---

### Post by yabbadabbadont on 2007-11-18
It looks very similar to this bug that was reported in libXft:

[https://bugs.launchpad.net/ubuntu/+source/xft/+bug/145244](https://bugs.launchpad.net/ubuntu/+source/xft/+bug/145244)

---

### Post by lordsunland on 2007-11-18
> **yabbadabbadont said:**
> It looks very similar to this bug that was reported in libXft:

[https://bugs.launchpad.net/ubuntu/+source/xft/+bug/145244](https://bugs.launchpad.net/ubuntu/+source/xft/+bug/145244)

I have read it...
So does this mean I can possibly fix this problem by install libxft from Feisty?
Till now I only find this problem in Openoffice. 

Thanks. :)

---

### Post by yabbadabbadont on 2007-11-18
I doubt it.  You should file a bug about it yourself.  Yours would be filed against either openoffice or libcairo.  I would file it against libcairo.

---

