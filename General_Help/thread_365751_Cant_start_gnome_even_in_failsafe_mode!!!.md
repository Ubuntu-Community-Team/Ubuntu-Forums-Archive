---
title: "Cant start gnome even in failsafe mode!!!"
date: 2007-02-20
forum: General Help
---

### Post by ALIENDUDE5300 on 2007-02-20
I have no idea why its not working, but I cant start gnome.

I recently updated from Ubuntu 6.06 to 6.10.

I have managed to login with the session set as terminal and launch Firefox.

Any ideas on what I should do?

Thanks in advance.

---

### Post by bikeboy on 2007-02-20
Firstly, check for errors in your logfiles. They are located in /var/log, try looking at the xorg one (forget the name) and maybe "messages" as well.

---

### Post by ALIENDUDE5300 on 2007-02-20
nothing that looks glaringly unusual except a file called /var/crash/_usr_bin_bug-buddy.1000.crash, would this have anything to do with it?

EDIT: Im gonna try to change the extension to .txt and upload it.

---

### Post by ALIENDUDE5300 on 2007-02-20
Ok I uploaded it to the first host I found so here's a link:
[URL="http://www.freefilehosting.org/pupload/view/26842"]
http://www.freefilehosting.org/pupload/view/26842[/URL]

---

### Post by bikeboy on 2007-02-20
Hmm, nothing in there I can understand lol. I forgot to say, when looking in thexorg log Xorg.0.log, check for lines starting with WW. That is a warning of something wrong.

I had gnome fail a while ago and tracked down the problem, I'll try to find the thread to see which log helped me.

edit: Have a look at .xsession-errors as well, it will be in your home directory. You can use [http://paste.ubuntu-nl.org/](http://paste.ubuntu-nl.org/) for a pastebin too if you want.

---

