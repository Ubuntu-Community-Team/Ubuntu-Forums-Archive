---
title: "Terminal Failure"
date: 2007-11-26
forum: General Help
---

### Post by Dynar on 2007-11-26
I've encountered something strange during the use of Ubuntu 7.10. All of a sudden my Terminal won't work properly. I get the following error message upon start up of the Terminal.

"There was a problem with the command for this terminal: Text was empty (or contained only whitespace)"

At first I could still use it. However upon a hang up on my system displaying there was no keyboard present, I only could see this in the Terminal window "$" where you usually see [email]usr@usr.desk[/email]top: $ or something like that.. I also couldn't see what I was extracting or where I was on my system. (which directory such as usr/home/etc.. )

I tried reinstalling it through the Synaptic Package Manager. I don't dare to uninstall it, since it's dependant on ubuntu desktop.

Any help is appreciated.
Thanks

Dynar

---

### Post by TidusBlade on 2007-11-26
I dont know if this will help, but I have seen other terminal programs in the official ubuntu repos, when using Feisty, not sure if they are still there, but worth a try ;)

---

### Post by Dynar on 2007-11-26
Didn't really help me much. There may be alternatives. Is there anything I can grab from the Synaptic Package Manager? I'd actually like to use the standard terminal though. I don't like broken things.. 

I bet it's something silly..

I really need this resolved, because I can hardly anything without it.

Thanks though. :)

---

### Post by mali2297 on 2007-11-26
Try xterm, press Alt-F2 and type
```

xterm

```

---

### Post by Dynar on 2007-11-26
Thanks, that helped a lot really.. 

But is there anyway I can fix the current Terminal?

---

### Post by mali2297 on 2007-11-26
What happens if you run 
```

gnome-terminal

```
from xterm?

Any error messages?

---

### Post by smartboyathome on 2007-11-26
Also, it is ok to uninstall ubuntu-desktop, as it is only a metapackage. Just re-install it when you go to upgrade.

---

### Post by Dynar on 2007-11-26
> **mali2297 said:**
> What happens if you run 
```

gnome-terminal

```
from xterm?

Any error messages?

I get the same error.

---

### Post by Dynar on 2007-11-26
> **smartboyathome said:**
> Also, it is ok to uninstall ubuntu-desktop, as it is only a metapackage. Just re-install it when you go to upgrade.

I reinstalled it and it didn't change anything, unfortunately.

---

