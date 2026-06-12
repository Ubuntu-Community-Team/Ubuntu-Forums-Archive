---
title: "Retaining title in Terminal following reboot on Ubuntu 8.0.4"
date: 2008-05-15
forum: General Help
---

### Post by Fortisunto on 2008-05-15
Hello

Have my Ubuntu working nicely now overall. One thing left through...

I have multiple work spaces that have about 8 terminals logged into different servers on each workspace. I am using the default Gnome Terminal 2.22.1. Within the terminal i can click Terminal -> Set Title (and then type in name of server)

Problem is that if i reboot my ubuntu machine even though the session is remembered (ie.it opens correct pre-resized terminals within each workspace) unfortunately it does not remember the title.  Each terminal defaults back to my username@desktop. Does anyone know a way where the title can be saved for each terminal in case of reboot?

(by the way i am not planning to reboot all the time etc but before i set up all my windows again would just like to know a way to possibly set this up with titles to save renaming each window on reboot.

Thanks for all your help by the way on previous questions. This should be it then i hope :D

---

### Post by Vivaldi Gloria on 2008-05-15
You can launch a gnome-terminal with 

```
gnome-terminal --title=TITLE
```

to get the title you want. So try making different launchers for each title you want. Look

```
man gnome-terminal
```

for more options.

---

### Post by Fortisunto on 2008-05-16
Hmmm no clues really from checking man on terminal :(

Is really annoying that after reboot/logoff each terminal comes back up - but without the title. Im sure this used to work under KDE so i might go back to that unless anyone has any ideas about Gnome? I ensure that in Preference->Sessions->Session options that i have "Automatically remember running sessions when logging out" ticked. Any ideas anyone? :(

---

### Post by Fortisunto on 2008-05-23
Can anyone recommend a good terminal emulator under gnome that will hold terminal titles?

I been googling around but none of them seems to confirm this.

---

