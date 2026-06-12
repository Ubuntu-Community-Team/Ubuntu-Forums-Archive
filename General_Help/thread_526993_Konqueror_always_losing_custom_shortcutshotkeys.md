---
title: "Konqueror always losing custom shortcuts/hotkeys"
date: 2007-08-16
forum: General Help
---

### Post by jimisdead on 2007-08-16
I've had this problem since at least Dapper and it hasn't been fixed so maybe I'm the one doing something wrong.

I like the firefox type hot keys, so I want to be able to cycle through tabs in konqueror using ctrl-tab... so in konqueror I go to 'Settings' then to 'Configure Shortcuts' and I change the hotkeys to the ones I want... and they work - but only for that window. Any new windows I open always have the default hotkeys, as well as all the other konqueror windows I had open at the time I changed the hotkey bindings.

Does anyone know what's going on? All I want to do is change the hotkeys.:confused:

---

### Post by davidjmayo on 2007-08-16
did you ever try
alt F2 then type in 
konqueror --profile filemanagement

do your changes and here I'm not sure as I only did it for file management not web browser
save them by
Settings==>save view profile web browser (or something similar)

next time  open Konq the same way with alt F2
konqueror --profile filemanagement

maybe you better try one or 2 of your shortcuts first to see if this works

if this works and you need to do as root then it has to be
kdesu 'konqueror --profile filemanagement'

note the single quotes ARE NEEDED

---

### Post by jimisdead on 2007-08-16
I'm not sure how but that worked.

I have done the 'saving profile' thing before and it didn't work - maybe it has something to do with running the konqueror --profile filemanagement command.

now it retains the hotkeys if I either open with alt-f2 and run the command with parameters, or if I open konqueror normally then load the filemanagent profile.

But surely this is not the way it's intended to work? There has to be a way to set the hotkeys  as default - as it stands this is just insane.

---

### Post by davidjmayo on 2007-08-16
glad it worked

I don't remember how I found this one but konq annoyed me as everytime it defaulted to icon view and I wanted list view. somehow I found this parameter for the command (like you I tried the save profile to no effect)

possibilities/tests:

1 does the --profile management save in /home? (until today I haven't used konq for a long time so if I searched it would not show a recent change)

2 what happens if you log in as another user? does it still stick?

agreed - it's insane

---

