---
title: "sudo - gedit fails to open GUI window"
date: 2006-12-09
forum: General Help
---

### Post by dregnus on 2006-12-09
I do most of my Ubuntu configuration with gedit and sudo. However, after installing Edgy from Dapper (and keeping my home directory), sudo gedit whatever no longer works. It basically sits there for a while, appearing to do nothing, but then eventually opens the file inside the terminal itself. I installed gvim and it does the same thing. Both programs work as expected (spawning a GUI) when sudo is not used.

---

### Post by taurus on 2006-12-09
```
gksudo gedit **filename**
-or-
sudo nano -w **filename**
```

---

### Post by rioghal on 2006-12-09
> **dregnus said:**
> I do most of my Ubuntu configuration with gedit and sudo. However, after installing Edgy from Dapper (and keeping my home directory), sudo gedit whatever no longer works. It basically sits there for a while, appearing to do nothing, but then eventually opens the file inside the terminal itself. I installed gvim and it does the same thing. Both programs work as expected (spawning a GUI) when sudo is not used.

You're not supposed to use sudo with gui apps.. sudo is for comman-line apps only. Use gksu or gksudo with gui apps.

For more info, see this page:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by dregnus on 2006-12-09
I see. I have just gotten used to always being able to do that in the past though. Thanks a lot :)

---

### Post by Malakia on 2006-12-09
I use Edgy and I still use sudo with Gui apps. I did have the same problem you were having until I restarted my computer and it seemed to go away. Also did you finish the updates after you upgrade to Edgy?

---

### Post by dregnus on 2006-12-09
Yeah...gksudo doesn't work either, it still won't load gedit. I'm trying to edit my sources.list

Anyways...running the updates now so I'll report back on the status once that is done.

---

### Post by dregnus on 2006-12-09
Installing the updates seems to have fixed it. Thanks for the help everyone.

---

