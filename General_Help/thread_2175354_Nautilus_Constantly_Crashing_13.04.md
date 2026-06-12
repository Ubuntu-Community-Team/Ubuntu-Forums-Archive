---
title: "Nautilus Constantly Crashing 13.04"
date: 2013-09-18
forum: General Help
---

### Post by JohnAreBee on 2013-09-18
Nautilus (and until prior to removing it Nemo) is constantly crashing, it happens when you go to do any type of action, new, rename, delete, ect. It not any one particular option and sometimes it crashes 2 commands in, sometime 10 commands in, its driving me insane.
Here is the msgs i get when it crashes from gksudo nautilus command in terminal: [http://paste.ubuntu.com/6126074/](http://paste.ubuntu.com/6126074/)
Here is dmesg output that was run right after crash: [http://paste.ubuntu.com/6126073/](http://paste.ubuntu.com/6126073/)
Any help will be greatly appreciated.

---

### Post by QDR06VV9 on 2013-09-18
> **JohnAreBee said:**
> Nautilus (and until prior to removing it Nemo) is constantly crashing, it happens when you go to do any type of action, new, rename, delete, ect. It not any one particular option and sometimes it crashes 2 commands in, sometime 10 commands in, its driving me insane.
Here is the msgs i get when it crashes from gksudo nautilus command in terminal: [http://paste.ubuntu.com/6126074/](http://paste.ubuntu.com/6126074/)
Here is dmesg output that was run right after crash: [http://paste.ubuntu.com/6126073/](http://paste.ubuntu.com/6126073/)
Any help will be greatly appreciated.
Out of curiosity do you have "libnss-myhostname" installed?

---

### Post by JohnAreBee on 2013-09-19
> **runrickus said:**
> Out of curiosity do you have "libnss-myhostname" installed?

No I didn't because it said: please install '[COLOR=#000000]Please install nss-myhostname![/COLOR][COLOR=#000000]' I looked for it and didn't find it, and thought it wasn't[/COLOR][COLOR=#000000] related, I just did install it because you provided the proper package name. So we will see what happens.[/COLOR]

---

### Post by JohnAreBee on 2013-09-19
Unfortunately still crashing here is a newer version of the outputs, 
dmesg: [http://paste.ubuntu.com/6129184/](http://paste.ubuntu.com/6129184/)
Output from 'gksudo nautilus' command in terminal: [http://paste.ubuntu.com/6129185/](http://paste.ubuntu.com/6129185/)
As strange as this may seem but it seems to only crash when in detailed list view, and keep in mind nemo acts the same ways.

---

### Post by stinkeye on 2013-09-19
Have you added any  ppas?

---

