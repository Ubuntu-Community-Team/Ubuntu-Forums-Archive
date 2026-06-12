---
title: "Please help me make an alias/command, it's racking my brains"
date: 2007-06-23
forum: General Help
---

### Post by herbster on 2007-06-23
Okay, my scenario is that I play a game which is run using ./etsound (a script). I would like to have exactly the following happen when I play the game: Conky shuts down, Beryl reverts to Metacity as window manager, the game starts, and when the game exits conky restarts and Beryl reloads as window manager.

Is this even possible? With it being linux I assume it is and I would guess it is with some of the brains on this forum that are so helpful, so I'm seeking help, please! This would so freakin' make my day :)

P.S. Someone previously gave me a command like "pkill conky && ./etsound & conky" or something that worked to shutdown and restart conky before/after game, but only when I typed it in the shell, couldn't make a launcher with it.

Thanks for any help, this has been stumpin' me noggin!

---

### Post by thelinuxguy on 2007-06-23
> **herbster said:**
> P.S. Someone previously gave me a command like "pkill conky && ./etsound & conky" or something that worked to shutdown and restart conky before/after game, but only when I typed it in the shell, couldn't make a launcher with it.


For a launcher, this command should work:
```

bash -c "pkill conky && ./etsound & conky"

```

Is that really a single & after ./etsound which works?

---

### Post by herbster on 2007-06-24
> **thelinuxguy said:**
> For a launcher, this command should work:
```

bash -c "pkill conky && ./etsound & conky"

```

Is that really a single & after ./etsound which works?

I don't know, can't recall. What does the "-c" do?

Also, I am using XQF and when I do this, it kills conky and runs the game, but the game doesn't connect to the server I double-clicked on, just loads to default menu. Any ideas?

---

### Post by thelinuxguy on 2007-06-24
> **herbster said:**
> I don't know, can't recall. What does the "-c" do?

Also, I am using XQF and when I do this, it kills conky and runs the game, but the game doesn't connect to the server I double-clicked on, just loads to default menu. Any ideas?

A launcher seems to be able to execute only one command. So the command I posted above just launches a shell and the shell, in turn, launches the actual commands you want executed. The -c switch tells bash to read the commands from the string following it.  I can't tell you anything about the game itself. You had mentioned that the command works when you launch it from the terminal. I just happened to know how to run those multiple commands from a launcher.

---

### Post by eggdeng on 2007-06-24
This script stops beryl (replacing it with metacity) and starts torcs when you click on the launcher, if torcs is not running already. If torcs is running when you click on the launcher, the script kills it and starts beryl. You would need to hack it around for your environment but I think the principle is the same.

```
#!/bin/sh
game='torcs'
if ps ax | grep -v grep | grep $game > /dev/null #checks if torcs is running
then
pkill torcs & #single ampersand to chain commands in sequence
beryl-manager
else
pkill beryl &
metacity &
/usr/games/torcs
fi
```

---

