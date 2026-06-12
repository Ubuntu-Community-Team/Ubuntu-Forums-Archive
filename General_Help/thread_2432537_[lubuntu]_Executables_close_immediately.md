---
title: "[lubuntu] Executables close immediately"
date: 2019-12-04
forum: General Help
---

### Post by wavebreaker89 on 2019-12-04
New Linux user here. I'm running Lubuntu 19.10 on a HP Compaq Presario CQ57.

I downloaded a Linux version of the game called File://Maniac from BornFrustratedStudio.
When I run the executable (FileManiac.x86_64) a window flashes briefly and then nothing happens.

I've changed the permissions to rwx and ran the file through the terminal. This is the output:
```
cq57@cq57-pc:~/Downloads/FileManiac$ ./FileManiac.x86_64
Set current directory to /home/cq57/Downloads/FileManiac
Found path: /home/cq57/Downloads/FileManiac/FileManiac.x86_64
Mono path[0] = '/home/cq57/Downloads/FileManiac/FileManiac_Data/Managed'
Mono config path = '/home/cq57/Downloads/FileManiac/FileManiac_Data/MonoBleedingEdge/etc'
Preloaded 'ScreenSelector.so'
Preloaded 'libfmod.so'
Preloaded 'libfmodL.so'
Preloaded 'libfmodstudio.so'
Preloaded 'libfmodstudioL.so'
Preloaded 'libgvraudio.so'
Preloaded 'libresonanceaudio.so'
Display 0 '0': 1366x768 (primary device).
Logging to /home/cq57/.config/unity3d/BornFrustrated/FileManiac/Player.log
```
And then nothing happens. I tried another game called The Good Time Garden, and the same thing happens.

The same file runs perfectly on my wife's Linux Mint laptop

---

### Post by cmcanulty on 2019-12-04
You have to install wine in order to run windows executables.  Some work fine with wine some don't.

---

### Post by DuckHook on 2019-12-04
> **cmcanulty said:**
> You have to install wine in order to run windows executables.  Some work fine with wine some don't.
I believe that the OP downloaded the Linux version of the game.

---

### Post by DuckHook on 2019-12-04
> **wavebreaker89 said:**
> New Linux user here. I'm running Lubuntu 19.10 on a HP Compaq Presario CQ57.

I downloaded a Linux version of the game called File://Maniac from BornFrustratedStudio&#8230;
As a self-professed new Linux user, I hope you won't mind a bit of digressive advice: it is not advisable to download third party apps from unknown websites and run them on your machine. That way lies the sort of rampant malware/viral/ransomware plagues that infest the Windows world. You may find the links in my sig useful, especially "Linux is Not Windows" and "Security Basics".

If you must play such games, at least take care to confine them within heavily jailed sandboxes like a VM. Unfortunately, your laptop is rather long in the tooth and may not be sufficient to run a game with the added VM overhead.

Can't help much with what's borking your game. I'm not at all familiar with it and, as per above, I won't be running it even to test. Your output does show that a game log is kept. Perhaps looking in there might give you some further clues.

---

### Post by SeijiSensei on 2019-12-04
It says it is logging to /home/cq57/.config/unity3d/BornFrustrated/FileManiac/Player.log.  Have you looked at that file for clues?

---

