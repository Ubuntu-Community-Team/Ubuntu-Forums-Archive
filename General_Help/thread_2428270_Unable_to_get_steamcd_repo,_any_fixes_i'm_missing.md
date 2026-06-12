---
title: "Unable to get steamcd repo, any fixes i'm missing?"
date: 2019-10-01
forum: General Help
---

### Post by blckassn on 2019-10-01
I'm running Ubuntu 18.04 and trying to get the steamcd repo but it's not working.  I added multiverse rep and i386 architecture but it's still not working.  These are the only fixes I've found and they're not working for me.  Anything I'm missing to get steamcd repo to download?

---

### Post by deadflowr on 2019-10-02
What's steamcd?
What installation instructions are you following?

---

### Post by blckassn on 2019-10-02
Sorry I meant steamcmd.

Instructions from [here]("https://developer.valvesoftware.com/wiki/SteamCMD").

> **Package from repositories**

[FONT=sans-serif]1. It's recommended to install the SteamCMD package from your distribution repositories, if available:[/FONT]
[FONT=sans-serif]Ubuntu/Debian[/FONT]
sudo apt install steamcmd
[FONT=sans-serif]**[IMG]https://developer.valvesoftware.com/w/images/c/cc/Note.png[/IMG] Note:**If you are using a 64 bit machine you will need to add multiverse sudo add-apt-repository multiverse
 sudo dpkg --add-architecture i386
 sudo apt update
 sudo apt install lib32gcc1 steamcmd 


[/FONT]

---

### Post by deadflowr on 2019-10-02
So what were the outputs when you ran all that.
please post them.
More specifically post the output for
the last two commands
```
sudo apt update
sudo apt install lib32gcc1 steamcmd
```

---

### Post by blckassn on 2019-10-02
omg i feel like an idiot, i kept mistyping it like i did in the title no wonder it wasn't downloading.

Solved: make sure you double check what youre spelling lol.

---

