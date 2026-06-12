---
title: "Automatic show &quot;information&quot;"
date: 2013-12-11
forum: General Help
---

### Post by Mark de J on 2013-12-11
Hello,

Can I show information when my computer starts up or shut down shown. Now I must press delete first, but I want it default. Can this?

---

### Post by ajgreeny on 2013-12-11
Do you mean you want to see the scrolling text when you boot up and shutdown?

If so, simply edit the **/etc/default/grub** file and remove quiet splash from the line that looks similar to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Your line may be slightly different to this but the words quiet splash should still be there.  Leave the quote marks alone and do not remove them, leaving ```
GRUB_CMDLINE_LINUX_DEFAULT=""
```
Now run command ```
sudo update-grub
``` and you should see all the text (information) at every boot and shutdown

---

### Post by Mark de J on 2013-12-11
I did, but it isn't working, must I run that command in terminal as root maybe?

EDIT: I need logged in as root to edit it, how?

EDIT2: I solved it, thanks for the edits I must do! :)

---

