---
title: "Multiple instances of totem possible?"
date: 2005-07-15
forum: General Help
---

### Post by smack on 2005-07-15
I like to watch multiple adult movies at the same time. In windows I can open up multiple instances of a movie player. I could have 6-7 movies open and playing smoothly at the same time. In ubuntu I can only open up one instance of totem. When I open a new movie it just starts playing it in the same totem window and kills my other movie.

Is there a way to get multiple instances of them going?

FYI I felt it necessary to specify that they were adult movies so people don't say "why would you want to watch more than one more at a time". I mean it's not like there's much of a plot that I'll be missing. :|

---

### Post by prankstar008 on 2008-02-07
Use VLC.  Its probably under add remove programs.

---

### Post by everettattebury on 2008-06-18
For anyone else who stumbles across this thread, I have found a solution to this problem.  I have also been very annoyed when a movie I had paused in a specific location was REPLACED when I went to open another movie.  

In December 2007 a new option was added to totem, "--no-existing-session", which forces it to open the movie in a new instance.  

That's fine if you use the command line to open movies, but if you're like me, you want to be able to click an icon in nautilus and have it just work.  I couldn't find any setting in totem or gconf-editor to make this the default behavior, so I wrote this script:

```

#!/bin/bash
#  Force totem to open new instance for each movie opened, 
#  rather than replacing the movie in the existing instance.
/usr/bin/totem-gstreamer --no-existing-session "$@"
```

Just delete /usr/bin/totem and replace it with the script.

---

### Post by pjbgravely on 2008-07-20
Thanks, Now that totem-xine seems to be the best player out there you showed me how fixed the feature/bug that was driving me mad. It is no fun trying to find a minimized video on 3 screens with 4 desktops each.

A little safer method, that won't get wiped out in an update and to use totem-xine. 


sudo mv /etc/alternatives/totem /etc/alternatives/totem.old

sudo gedit /etc/alternatives/totem

copy this into the editor

```
#!/bin/bash
#  Force totem to open new instance for each movie opened, 
#  rather than replacing the movie in the existing instance.
/usr/bin/totem-xine --no-existing-session "$@"

```

Save, then:

sudo chmod +x /etc/alternatives/totem


If this still doesn't work then you may have switched to totem-xine the wrong way like I did. To fix do this:

Right click properties/open with/ click Movie Player instead of Movie Player (Xine) For each type of video file.

This will redirect to the new script.

Paul

---

