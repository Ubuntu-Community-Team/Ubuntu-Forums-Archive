---
title: "want to run a sh-script at login (13.10), but how?"
date: 2014-01-22
forum: General Help
---

### Post by robenroute on 2014-01-22
This is probably a bit of a noob question, but I want to automatically execute the following at every login, using 13.10 with Unity:

```
#!/bin/sh
sleep 1 && feh --bg-fill ~/Pictures/background.jpg &
```

The website this comes from states I should add it to .xinitrc (in my home directory); that file wasn't there, so I created it (and made it executable), but nothing happens. Am I overlooking something or doing something silly? Are there alternatives to get this done?

Many thanks in advance!

---

### Post by mcduck on 2014-01-22
Just open "Startup Applications" and add the script there?

(adding it to ~/.profile probably would work, but it seems pointless to execute that command for CLI logins ;))

...Also keep in mind that the command won't do anything at all unless you have Feh installed, and have made sure NAutilus is not managing your desktop (like it does by default). Otherwise you won't see anything even if the script works.

---

### Post by robenroute on 2014-01-22
Thanks mcduck. feh is installed alright. I've added the script to Startup Applications, but it doesn't seem to work. Running the script manually after login does result in the desired effect (having a Conky pane do the pseude-transparency trick). Can I conclude now that the script is not executed? But that seems odd... Or am I overlooking something else?

---

