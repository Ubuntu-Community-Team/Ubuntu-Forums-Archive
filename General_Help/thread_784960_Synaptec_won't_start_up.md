---
title: "Synaptec won't start up"
date: 2008-05-06
forum: General Help
---

### Post by wreisin on 2008-05-06
I'm running Hardy (32 bit) with the latest updates on a Dell d630.  Tonight I went to fire up Synaptec (for the first time since downloading a slew of updates earlier today) and it doesn't start up.  When I click on the menu icon in the System menu, I get the loading spinner for a few seconds, but Synaptec never appears.  

Does anyone have any ideas about this, or can anyone point me to where I can find a log file to look at to see why it's crashing?

---

### Post by urbushey on 2008-05-06
Try running it from the terminal?

(Press <Ctrl>+<Alt>+<R>, and at the command prompt, type: ```
synaptic
```

There might be some error information there.

Notice that it's synaptIc not synaptEc...

---

### Post by wreisin on 2008-05-07
Weird, running it from the terminal worked.  And thanks for the spelling correction :-)

---

### Post by Andy_C on 2008-05-23
I have the same problem, and its fixed for me by running synaptic via the console using sudo.

I've noticed that when I try and start synaptic from the menu, and when I try and install anything from the "add/remove programs" a box appears in the menu bar at the bottom which says "Starting Administrati..."

I think this is what should appear and prompt for my admin password, but it doesnt. It appears in the menu bar from a few seconds and then just dissapears. Synaptic wont start and Add/Remove programs just freezes.

Anyone any ideas??

---

