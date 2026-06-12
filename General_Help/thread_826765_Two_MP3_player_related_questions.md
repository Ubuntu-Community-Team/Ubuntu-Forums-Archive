---
title: "Two MP3 player related questions"
date: 2008-06-12
forum: General Help
---

### Post by avishorp on 2008-06-12
Hello everyone,
I own a Sansa C250 music player. When I connect it to the computer, Rhythmbox  opens up. My first question is how to change this behaviour, so that the computer will automatically ran a script whenever this player (or prefferably any kind of player) is connected.
The second question is also related to this player. It has two kind of Flash memories - internal and SD card. Theses memories are mounted as two separate drives. I want to know how can I relate them to the player. When the forementioned script runs, I want to be able to list all the mounts related to the device and then do something with them.

Thanks,
Avishay

---

### Post by HalPomeranz on 2008-06-12
> **avishorp said:**
> 
I own a Sansa C250 music player. When I connect it to the computer, Rhythmbox  opens up. My first question is how to change this behaviour, so that the computer will automatically ran a script whenever this player (or prefferably any kind of player) is connected.

On my Hardy system, you can choose an alternate media player app using "System -> Preferences -> Preferred Applications".  Select the "Multimedia" tab and choose "Custom" from the list of choices.  Enter your script name into the "Command" box.

> **avishorp said:**
> 
The second question is also related to this player. It has two kind of Flash memories - internal and SD card. Theses memories are mounted as two separate drives. I want to know how can I relate them to the player. When the forementioned script runs, I want to be able to list all the mounts related to the device and then do something with them.


When I hook up my iPod, it's always mounted at the same mount point under /media.  The name of the directories under /media should be based on the volume names of your device and should be consistent.  Can't you just hard-code the mount point names into your script?

---

### Post by Tom--d on 2008-06-12
Natulius > edit > Pref > Media

:)

---

