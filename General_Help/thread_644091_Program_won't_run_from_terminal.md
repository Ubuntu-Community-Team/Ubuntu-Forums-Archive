---
title: "Program won't run from terminal"
date: 2007-12-18
forum: General Help
---

### Post by DrMega on 2007-12-18
Hi

I have a program which runs perfectly well if navigate to it via the file explorer and double-click it, but it won't run from the terminal.

Any ideas why that might be?

It is actually a game that I compiled from source (my first attempt at doing so, and painful let me tell you). The game runs but with no sound. I want to see if it is leaving any messages on the terminal to give me a clue as to why that is. I cd to the same directory that I was browsing, where the executable lives, then run ...

```
./smc
```

The game tries to start then bombs out.

If I double click the same file in the file explorer, it runs OK (but with no sound).

I can make it run from the terminal with...

```
sudo ./smc
```

but obviously I don't want to have to do that, and when I browse to the file, I am not switching to superuser mode so I can't see why this should happen.

Any ideas anybody?

---

### Post by mbeierl on 2007-12-18
Please post the output of ```
ls -al ./smc
``` as well as what happens when you enter ./smc

Also, what happens if you execute the following from the same terminal: ```
xterm
``` ... just want to make sure it's not a DISPLAY env variable problem.

---

### Post by DrMega on 2007-12-18
If I run xterm, I get a new terminal window.

If I check the rights on the file that I run now, it looks as it should, assigned to me for full rights, HOWEVER, I'm afraid to say that since my original posting on the subject, I've changed quite a few things. I'm still none the wiser as to why it ran from double-click but not from the terminal, but I found a workaround.

My investigations led me to the game's makefile, where it seems some paths were hardcoded to /usr/local/share/. I don't like hardcoded paths and I certainly don't like running anything with sudo unless I have to, so I put all the games files in a subfolder from my home folder, deleted the directory out of usr/local/share, and made a symbolic link to the similarly named folder in my home directory.

While I've solved the problem with a workaround (which I'm quite pleased with, as this is the most complicated Linux thing I've done so far) I've not got enough Linux experience to know if what I've done would be considered good practice or not.

---

