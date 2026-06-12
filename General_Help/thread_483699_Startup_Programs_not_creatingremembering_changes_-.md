---
title: "Startup Programs not creating/remembering changes -- Wtf?"
date: 2007-06-25
forum: General Help
---

### Post by Septicaemia on 2007-06-25
Okay, this is weird.

I open up System>Preferences>Session>Startup Programs, I remove Beagle Search Tool, and I add Pidgin and Firestarter's GUI to the list. I then hit close. However, when I open up System>Preferences>Session>Startup Programs **again**, Beagle Search Tool is back, and Firestarter and Pidgin are gone. What happened to my changes?

Is there something I'm doing wrong? Is there a permissions error or something?

If anyone can help me solve this, I'd greatly appreciate it. I'm sick of running Pidgin and Firestarter every time I boot/reboot.

Thanks,
Brendan.

---

### Post by Septicaemia on 2007-06-25
I'm still having no luck, does this happen to anyone else? I never had any troubles with Breezy when I used it.

---

### Post by Pat123 on 2007-06-25
Same problem here..Anyone ?

---

### Post by Brucevdk on 2007-07-01
Could you post the output for:
```

ls -al ~/.config/autostart/

```

You could also just *rm-rf ~/.config/autostart* and try again.

---

### Post by Qu4k3R on 2007-07-01
There are 3 tabs.. one let's you disable (or remove) and create (or edit) new startup programs.
The second one lets you change the way those startup programs run (you can disable them here too).
The third one is to save changes.

---

