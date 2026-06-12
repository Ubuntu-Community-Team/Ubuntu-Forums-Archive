---
title: "Nautilus Location Launchers Don't Work (Old ones or Newly-Created)!"
date: 2008-06-25
forum: General Help
---

### Post by OzzyFrank on 2008-06-25
OK, I couldn't help but notice that when I upgraded to Hardy all my launchers to locations were mucked up. And this even includes "Application" launchers with commands like [COLOR="Blue"]nautilus /home/user/Downloads[/COLOR] (as opposed to "Location" launchers where you only need to specify the path - obviously, those don't open either).

So basically I've had to recreate all my launchers again, but now I am making some more Location launchers, directly on the panel (ie: [COLOR="Indigo"]Add to Panel > Custom Application Launcher[/COLOR]), and these are also coming up with the error message:

[COLOR="DarkRed"]The specified location is invalid.[/COLOR]

Can anyone shed some light on why this is happening, and if there is a fix? Or is this just a huge bug in Gnome or Hardy that everyone is aware of and is soon to be addressed?

---

### Post by ryanhaigh on 2008-06-25
I remember reading something about this a while back but the only thread I could find was your old one. If I remember correctly you need to put file:/// infront of the location. So the launcher command would be either 
```
file:///home/user/Downloads
``` or ```
nautilus file:///home/user/Downloads
```. Hope this helps.

---

### Post by duvalx7 on 2008-11-06
It should help, I was having the same problem and tried this and it has solved the problem.

---

