---
title: "boot up sound file"
date: 2024-06-08
forum: General Help
---

### Post by billywyatt2 on 2024-06-08
I am running Ubuntu 24.04 and think it is brilliant! The only thing i'd like to add is the ability to play a sound file when my laptop boots up. So could someone help me please.

---

### Post by Rubi1200 on 2024-06-08
During the actual boot process or after login?

There are two different ways to go about it so more info on what you want would help.

---

### Post by billywyatt2 on 2024-06-09
Hi Rubi1200 and thanks for taking the time out to reply.
I'd like the system to play a sound file after the login if possible.

I've been using Ubuntu for so long now and i can't remember how long lol.

---

### Post by Rubi1200 on 2024-06-09
This is what I did:

1. create a script to play the file
```
nano ~/play_sound_on_startup.sh
```
by default it will save to the home folder but you can place it where you want

2.
add these lines to the script
```
#!/bin/bash
paplay /usr/share/sounds/Yaru/stereo/system-ready.oga
```

obviously, you can choose whichever sound file you want

3. make the script executable
```
chmod +x ~/play_sound_on_startup.sh
```

4.
hold down Alt+F2 to open the dialog box and type gnome-session-properties

this opens the startup applications preferences.

Click add New and give it a name e.g. Startup Sound

Enter the path e.g. if you leave it in the home folder then enter
```
~/play_sound_on_startup.sh
```

Click Add and then close.

5. reboot and test. After you login with your username and password it should play the sound file

Let me know if it works.

---

