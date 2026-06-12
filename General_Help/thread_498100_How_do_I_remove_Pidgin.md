---
title: "How do I remove Pidgin?"
date: 2007-07-10
forum: General Help
---

### Post by jon.carstens on 2007-07-10
I installed Pidgin by compiling it from source [at least I think that's what I did] using this guide:

[http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/](http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/)

Alas, it is not much different from GAIM at all, considering I only use Yahoo Messenger. So how do I get rid of Pidgin? I don't have the icon in my App>Internet menu but I can run the program from terminal by typing ```
pidgin
```

---

### Post by testube_babies on 2007-07-10
Go to the folder where you have the Pidgin source files and do ```
sudo make uninstall
```

If you don't have the source anymore, you'll have to download it again and ```
./configure
make
sudo make uninstall
```

---

### Post by yabbadabbadont on 2007-07-10
If the directory in which you compiled pidgin still exists, open a terminal window and cd into it.  Now try running "sudo make uninstall".  Hopefully, the developers provided an "uninstall" target just like they did an "install" target.

Edit: Doh!  Too slow.  :D

---

### Post by jon.carstens on 2007-07-10
Ok thanks, I can't run it from terminal anymore so I asume it's uninstalled. So can I delete the source files now?

---

### Post by testube_babies on 2007-07-10
Unless you're planning on installing again, you can go ahead and delete the source.

---

