---
title: "[SOLVED] Open app using terminal w/o app taking over terminal"
date: 2007-09-19
forum: General Help
---

### Post by Kenchu on 2007-09-19
If I open a graphical program using the terminal, the app will "take over" the terminal with output data. I know theres a command "gksu" to open programs w/o this happening, though that will also grant root authority. Is there a similar command but that doesnt give root? Thanks

---

### Post by Lord Illidan on 2007-09-19
Ok, what you can do is type the name of the application, and add an & sign at the end.

Then add the word disown.

So for example, I could launch totem like this :

```
totem& disown
```

You can even close the terminal window then, and the app will remain running.

---

### Post by olejorgen on 2007-09-19
If you don't mind the program being "attached"* to the terminal, just do <program> &

* if you close the terminal the program wil also terminate.

EDIT: Note to self: stop posting in unaswered threads on the first page :P

---

### Post by Lord Illidan on 2007-09-19
> **olejorgen said:**
> If you don't mind the program being "attached"* to the terminal, just do <program> &

* if you close the terminal the program wil also terminate.

For that reason, there is disown..isn't life cool in *nix?

---

### Post by kellemes on 2007-09-19
> **Lord Illidan said:**
> For that reason, there is disown..isn't life cool in *nix?

Didn't actually know this one..
Man, I never stop learning! :guitar:

---

### Post by Kenchu on 2007-09-19
Thx. :D

---

### Post by olejorgen on 2007-09-19
> **Lord Illidan said:**
> For that reason, there is disown..isn't life cool in *nix?

yay, thanks :)

---

### Post by olejorgen on 2007-09-19
While I'm here, is there a command to start a job unattached? (disown works on running jobs)

I could of course make a quick script, but built-in is always better

---

