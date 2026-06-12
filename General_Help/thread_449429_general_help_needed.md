---
title: "general help needed"
date: 2007-05-20
forum: General Help
---

### Post by nate_nightroad on 2007-05-20
hi, using 7.04 here and i found out tat everytime i mount a hdd, the hdd will appear at the desktop,so is there anyway i can mount a hdd without having the mounted hdd appearing at the desktop?

---

### Post by mikewhatever on 2007-05-20
Yes, mount it in the directory other then /media. You can also remove the desktop icons by Alt+F2, then type gconf-editor, navigate to apps/nautilus/desktop and uncheck 'volumes visible' box.

---

### Post by nate_nightroad on 2007-05-20
thanks for the reply.....how do i mount it to diff directory besides /media......
also i tried to type gconfig-editor, it says could not open location......

please help.....thanks

---

### Post by mikewhatever on 2007-05-20
Who said 'gconfig, the command is as follows
> gconf-editor

---

### Post by nate_nightroad on 2007-05-21
anyway my mistake..thanks and the prob is solved...
but there is another prob,hope u guys can help
i have 2 hdd...the 1st hdd have 2 partition with windows and ubuntu and the 2nd hdd is for my data storage...now i want the 2nd hdd to not show up in the places>computer area coz i dont wanna mess it up and there are important files in there...
any advice?

---

### Post by mikewhatever on 2007-05-21
You do not mess anything up by removing the icons from the desktop. Look under Places, you should still have the links to your partitions there.

---

