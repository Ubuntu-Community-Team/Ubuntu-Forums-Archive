---
title: "Launcher problem with gnome and wine"
date: 2007-05-08
forum: General Help
---

### Post by forchessonly on 2007-05-08
I'm trying make a launcher for a game, Homeworld, by right-clicking on my gnome panel, selecting "add to panel" -> "custom application launcher". In the command section of the launcher properties I wrote "wine /home/username/Homeworld/homeworld.exe", without the quotes. When I click the launcher it says "Unable to open file: Homeworld.big".

However, if I boot up the terminal and cd into the homeworld directory, and then type "wine homeworld.exe" it runs like a charm. 

How can I set it up so that it will run from a launcher on my gnome panel?

Thanks

---

### Post by z0phi3l on 2007-05-08
Only thing I see after checking my shortcut for WoW on my launcher is this:
"wine /home/username/Homeworld/homeworld/exe"

Should be:
"wine /home/username/Homeworld/homeworld.exe"

If the / and . were just a typo while writing the post then I don't know why it doesn't work. I'm also assuming that you are replacing "username" with your actual username :P

---

### Post by forchessonly on 2007-05-08
yeah, sorry, that was a typo. I fixed it to what the launcher has, "wine /home/username/Homeworld/homeworld.exe"

---

