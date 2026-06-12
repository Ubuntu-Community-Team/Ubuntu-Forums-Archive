---
title: "Startup command/script help"
date: 2006-11-27
forum: General Help
---

### Post by raul_ on 2006-11-27
I have this little problem. I run the command "adesklets --nautilus" at startup and it works fine. The thing is that I can see the desklets on the brown/whatever colour i have, but when the system "draws" my background image, it's like the desklets get stuck beneath it, and i need to run the command again manually.

My doubt is, can i make this command run automatically, but only after a period of time? (so that it draws over the background)

---

### Post by kerry_s on 2006-11-27
I find a lot of programs do that. You can use "sleep" to give it time for the background to load first. Just make a script and point to that at startup, don't forget to make it executable.
Example:

```
#!/bin/sh
sleep 5
adesklets --nautilus &

```

That will make it wait 5 seconds before it runs the command, adjust time according to your start speed.

---

