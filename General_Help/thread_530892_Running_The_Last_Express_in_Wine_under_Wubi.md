---
title: "Running The Last Express in Wine under Wubi"
date: 2007-08-21
forum: General Help
---

### Post by imjustsomeguy72 on 2007-08-21
Hello.

I've been trying to install the game "The Last Express" under wine on a Wubi installation of Feisty Fawn. I'm been using Wubi for sometime, and have had next to no problems with it.

However, I have had a problem here. The game installs fine, no errors. When I try to run the game itself, I come up against an error. Wine itself doesn't error, and I get no output in the terminal, but I get a message from the Last Express saying that it could not find the hard drive cache, and that I should reinstall. Needless to say, reinstalling does nothing.

The little other info I've found on the net regarding TLE in wine has said that it usually runs flawlessly. I have the latest stable release of wine. I'm wondering whether it is something to do with Wubi. The game itself streams most of the data it needs off of the cd. Is it possible that it can't find the cd drive or something?

I don't really know what to do, and it may not be a wubi problem at all, but any help would be appreciated.

Thanks :)

---

### Post by jegHegy on 2007-08-21
Doesn't sound like a Wubi issue, but according to the Wine app DB, the game should run fine. Check your directory permissions and free hard disk space, the game is probably trying to create some temporary files somewhere.

---

### Post by imjustsomeguy72 on 2007-08-21
Well, everything is running in my home directory, so I'm pretty sure I have the right permissions. Is there anything in particular I should look for here? (I am still a relative newcomer to Linux...)

And I have over 600mb free in the my home directory, with several gigs in system. I'm running with 256mb ram, so I think I'm okay on that front. There's probably some stupid little switch somewhere I have to pull....

Incidentally, I succesfully ran this in Windows without a hitch.

Thanks for your help! I hope more wil be forthcoming :)

---

### Post by jegHegy on 2007-08-22
Tried running the game from the console? Skim through wine's output and look for errors or files not found or anything suspicious.

---

### Post by imjustsomeguy72 on 2007-08-22
I get no output from wine at all. The only output I get is from the program itself.

I have since, however, tried running the game from the autorunnin 'setup.exe', which seemed to work better, but I got a DirectDraw error. I managed to trace this to the program requiring 640x480 at 16-bit, so I added an entry to xorg.conf. However, I'm using an intel chipset, so I used apt-get to download a package called xserver-xorg-video-intel, which replaced....- i386. 

So, now I can change resolutions, however, when I apply a new res, X restarts, I get what I assume is Wubi's bootloading code, and I was dumped into the log in screen, with my native 1024x768 resolution. The same happens when I run TLE from native resolution. It tries to change to 640, and restarts x.

The plot thickens....

---

### Post by jegHegy on 2007-08-23
I suggest you get a mod to move this thread into the gaming subforum, or start a new thread there, as these problems sound completely unrelated to Wubi itself. You will probably get more replies from regular wine users.

---

