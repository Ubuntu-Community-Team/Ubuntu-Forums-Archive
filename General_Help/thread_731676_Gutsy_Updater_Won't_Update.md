---
title: "Gutsy Updater Won't Update"
date: 2008-03-22
forum: General Help
---

### Post by CD27 on 2008-03-22
My updater just sits there. It won't update at all. It just keeps looping, checking for updates, when i tell it to install, it'll go through the motion like it is, but it'll just loop back around to checking the updates again and what do ya know, they're still there, not updated at all. What's going on?

---

### Post by CD27 on 2008-03-22
anyone?

---

### Post by fela on 2008-03-22
i've never heard of that before...do you think that manually installing the updates with apt-get would be a good idea? it might be a bug with update-manager...

---

### Post by danwood76 on 2008-03-22
Do:
```

sudo apt-get upgrade

```

if it fails to update post the errors.

---

### Post by CD27 on 2008-03-22
nani? wtc that's crazy. I typed the same code before and it didn't work. It would update, but then when i checked the manager it would still require updating. It's fine now. It seems everything in gutsy relies on the terminal commands, b/c just about any kind of instillation or update i do via the gui is completely nullified unless i do it through the terminal. Like, i couldn't for the life of me add vlc to my comp via add apps or synaptic, but when i typed the command and pressed enter it loaded right up.

thanks guys, it worked.

---

