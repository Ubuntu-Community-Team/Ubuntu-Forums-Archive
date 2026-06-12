---
title: "Stop a program from starting up (Feisty)"
date: 2007-07-04
forum: General Help
---

### Post by Goombie on 2007-07-04
I have a program (glipper) that I don't need to use anymore, but was set to automatically start up when I logged in. So, I went to Session Manager and unchecked the program from the list of ones to start. But, the program still starts when I log in! What the hey? Is there anywhere else I need to go to disable this program from starting up when I log in?
Thanks!

---

### Post by coldstatue on 2007-07-04
Well, if you definitely don't need it anymore, I would uninstall it. I am not sure what that program is, or how it works with startup, but you can use a program called rcconfig to manage startup scripts.

---

### Post by Goombie on 2007-07-04
Glipper is a clipboard program for gnome. Essentially, I can use it to store more than one item on the clipboard.
Hmm.. I haven't heard of rcconfig, and I can't seem to find it in Synaptic. Where can I find it? I don't want to uninstall glipper because I might need it again.

---

### Post by regomodo on 2007-07-04
rcconf. not rcconfig. it lets you remove startup items but doesn't allow you to add afaict

---

### Post by coldstatue on 2007-07-04
Yup. That's the one. ;)

---

### Post by kevinlyfellow on 2007-07-04
Make sure the program is no long running in session manager (current session) and make sure your not running anything else you wouldn't want to run when you login and go to the third tab and save current session.

---

