---
title: "Only Root Can Use Webcam"
date: 2007-09-09
forum: General Help
---

### Post by Incarnadine on 2007-09-09
For some reason only the root user can use the webcam connected to my computer. I normally log into my own admin account that has all the  privileges as the root user, but yet my admin account still can't use the webcam:-k It's only detected in Ekiga Softphone when I'm on my root side. If anyone has any advice or help that would be greatly appreciated:popcorn:

---

### Post by prodigal on 2007-09-09
Try going into the programs properties on your login and telling it to run as root instead. I have the same problem with a couple of programs on my Kubuntu Desktop where they have to be run as root and I don't want to launch them from the command line.

---

### Post by Incarnadine on 2007-09-09
You mean change the properties to allow me to log on as the root user? I don't fully understand. Could you be more descriptive.

---

### Post by prodigal on 2007-09-09
Well if you find the software in the programs list, right click it and edit the program, you should have an option to run as a different user, once you enable that property you should be able to run it as root. I'm afraid I only know exactly how to do this in Kubuntu Desktop, I don't use Gnome so I have no idea how different the situation is. Sorry.

---

### Post by Incarnadine on 2007-09-09
Oh ok I understand. Unfortunately right clicking my program icons brings up no option for properties. I guess GNOME is really different then what you have. That's cool though. Thanks for the effort.

---

### Post by bettlebrox on 2007-09-09
Your user probably needs to be added to the right group for you to use the webcam. Try adding the user to the "video" group.

---

### Post by Incarnadine on 2007-09-11
Right now the account that I use is added to the "root" group so it should work right? I don't see any "video" group.

---

### Post by kiderjones on 2007-12-04
I just created a new "video" group, and it worked like a charm.

---

