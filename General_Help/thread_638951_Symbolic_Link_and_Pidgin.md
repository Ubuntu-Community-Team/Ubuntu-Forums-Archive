---
title: "Symbolic Link and Pidgin"
date: 2007-12-12
forum: General Help
---

### Post by jtw on 2007-12-12
My machine dual-boots Vista and Ubuntu (Gutsy), and I run Pidgin on both.  I wanted to keep the logs synchronized, so I created a symbolic link from ~/.purple  to /media/sda1/Program Files/Pidgin/.purple (where my logs reside on Windows).

Unfortunately, I stupidly created a soft symbolic link for the entire .purple directory instead of just the logs directory, and now I can't launch Pidgin in Ubuntu when the linked-to directory actually exists.

I can get it to launch when I delete the linked-to directory, run "apt-get remove Pidgin" and "apt-get install Pidgin" but it all blows up if the destination directory exists.

Can anyone help me find and remove this symbolic link?  rm and unlink don't seem to work....

thanks,
john

---

### Post by jtw on 2007-12-13
can anyone help me remove this symbolic link?  

it exists from ~/.purple to /media/sda1/Program Files/Pidgin/.purple and I just can't figure out what's going on.

thanks,
john

---

