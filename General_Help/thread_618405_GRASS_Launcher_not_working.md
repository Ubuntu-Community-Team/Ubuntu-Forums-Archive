---
title: "GRASS Launcher not working"
date: 2007-11-20
forum: General Help
---

### Post by Joshgray on 2007-11-20
Hey folks, I have a slight issue. I have successfully installed GRASS (GIS program) on ubuntu 7.10. I can run it from a terminal by commanding: 'grass' This works great, however the launcher that I created for the app doesn't work. The intro screen comes up (where you select a location/mapset), but then when after I make the selections and hit 'Enter Grass' all the windows just go away. Like I said, it works fine from the command line. I don't know what the difference would be?

Josh

---

### Post by malfist on 2007-11-20
Perhaps you should make sure it's using the right binary on the launcher. Are you giving it root access (sudo) when you run it from the command line?

---

### Post by Joshgray on 2007-11-20
I have entered the command on the launcher exactly how I launch it from a terminal: grass

I don't know, perhaps it is an xterm deal?

---

### Post by malfist on 2007-11-20
I don't know, I'm not familiar with grass

---

### Post by malfist on 2007-11-20
Are you launching grass from a specific directory from the command line? If so, you need to change your PATH to point to that location, or else the grass launcher wont know where to look.

---

### Post by Joshgray on 2007-11-20
I figured it out, I guess it was an xterm issue (or something... n00b here). In any case, I just changed the launcher type from "application" to "application in terminal"

Thanks,

josh

---

