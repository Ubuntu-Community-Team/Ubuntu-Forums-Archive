---
title: "Obtain permission while in nautilus"
date: 2007-08-11
forum: General Help
---

### Post by jonlemur on 2007-08-11
Is there a way to get root privileges while you are in Nautilus?  As in, not run the command sudo nautilus, but get permissions after you have already opened an "underprivileged" nautilus?

Thanks

---

### Post by ramjet_1953 on 2007-08-12
If you install [COLOR="Blue"]nautilus-script-manager[/COLOR] and [COLOR="Blue"]nautilus-script-collection-svn[/COLOR] , I think it will do what you want. 

Just right-click on the file in Nautilus and a drop-down menu will appear. 

Run the mouse pointer over the [COLOR="Blue"]Scripts[/COLOR] option and another menu will open, with several options.

[COLOR="Red"]sudo apt get install nautilus-script-manager
[/COLOR]
[COLOR="Red"]sudo apt-get install nautilus-script-collection-svn
[/COLOR]
Regards,
Roger 8)

---

### Post by jonlemur on 2007-08-12
Thank you, I'll start work on that soon.

---

### Post by jonlemur on 2007-08-12
Well, I installed both of those as you said, and I even rebooted after that.  But I don't get any "Scripts" option when I right-click on a file.  Is there something else I need to enable?  I'm running Gnome under Feisty Fox.

---

### Post by aysiu on 2007-08-12
> **jonlemur said:**
> Is there a way to get root privileges while you are in Nautilus?  As in, not run the command sudo nautilus, but get permissions after you have already opened an "underprivileged" nautilus? You wouldn't run the command *sudo nautilus* anyway. It should be ```
gksudo nautilus
```

---

### Post by ramjet_1953 on 2007-08-12
That's odd!

It is working perfectly on my system.

Admittedly, I installed it a long time ago and may have gotten the scripts from somewhere else.
I'm not really sure.

Regards,
Roger 8)

---

### Post by jonlemur on 2007-08-13
Thanks for trying.  I'll do some more research on the applications you suggested and see if there is something else I need to do.

As for the sudo/gksudo, I've been using sudo nautilus for some time without any issues.  But I don't know much about gksudo and the differences.  Should I be using gksudo instead?

One final thing, why did the title of this thread turn bold?  I've wondered for some time why some are bold and others are not, but I've never had one that's turned bold.

---

