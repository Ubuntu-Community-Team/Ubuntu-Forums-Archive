---
title: "Tor on Samsung Series 3 Chromebook running Chrubuntu 12.04"
date: 2013-01-21
forum: General Help
---

### Post by ssavoia1 on 2013-01-21
I operate a Samsung Series 3 Chromebook running Chrubuntu 12.04.  I have tried to run the tor browser bundle (32-bit) to no current success and would appreciate any help I can find.  When I launch the start-tor-browser file I receive the following error message: "vidalia exited abnormally.  exit code 2."

When run in the terminal I receive the following log:
Launching Tor Browser Bundle for Linux in /home/user/Downloads/tor-browser_en-US
./App/vidalia: 1: ./App/vidalia: ELF&#65533;: not found
./App/vidalia: 2: ./App/vidalia: Syntax error: "(" unexpected
Vidalia exited abnormally.  Exit code: 2

Thanks in advance for any input.

---

### Post by E411 on 2013-02-05
bumping this thread as I get the exact same error message when running ./start-tor-browser  (lubuntu 12.10)


```
Launching Tor Browser Bundle for Linux in home/myfolder/tor-browser_en-US
./App/vidalia: 1: ./App/vidalia: ELF&#65533;: not found
./App/vidalia: 2: ./App/vidalia: Syntax error: "(" unexpected
Vidalia exited abnormally.  Exit code: 2
```

---

### Post by phr0stbyt3 on 2013-06-07
Bump. Did you ever get an answer on this? I am running crouton on samsung ARM chromebook and the EXACT same thing happens to me:
```
./App/vidalia: 1: ./App/vidalia: ELF&#65533;: not found
./App/vidalia: 2: ./App/vidalia: Syntax error: "(" unexpected
Vidalia exited abnormally.  Exit code: 2
```

I haven't used linux very long, but I have a hunch this has something to do with this binary being compiled for x86 processors. Unfortunately I do not possess the skills to recompile for ARM. Also, the link is broken to the latest source code from torproject.

---

### Post by greatsirkain on 2013-06-07
I got this after I'd downloaded the browser bundle and extracted it to a folder then tried to run it from there instead of using the package manager to get tor...Or vice versa

(I just use a live version of Tails now it's easier)

---

