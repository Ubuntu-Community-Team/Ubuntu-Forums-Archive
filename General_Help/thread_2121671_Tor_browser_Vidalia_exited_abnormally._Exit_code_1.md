---
title: "Tor browser: Vidalia exited abnormally. Exit code: 139 (32 bit)"
date: 2013-03-02
forum: General Help
---

### Post by meraj21 on 2013-03-02
I downloaded Tor Browser Bundle (tor-browser-gnu-linux-i686-2.3.25-4-dev-en-US) for 32-Bit Linux. Whenever I start to run it on my Ubuntu 12.04 OS it shows me;

"Vidalia exited abnormally. Exit code: 139"

And I tried to do following things by reading another post about same problem.

Run tor successfully in debug mode in by opening a terminal in the tor folder and running 
```
./start-tor-browser --debug
```

It shows in terminal like

```
meraj@Meruz:~/Desktop/Upload/tor-browser_en-US$ ./start-tor-browser --debug

Debug enabled.


Starting Vidalia now

Launching Vidalia from: /home/meraj/Desktop/Upload/tor-browser_en-US
Segmentation fault (core dumped)

Vidalia exited with the following return code: 139
meraj@Meruz:~/Desktop/Upload/tor-browser_en-US$ 
```


And this doesnot work.

I dont know what to do. Please help.

---

### Post by caralu74 on 2013-04-05
I have the same problem:
./start-tor-browser --debug
Debug enabled.


Starting Vidalia now

Launching Vidalia from: /home/****/TOR_Bundle/tor-browser_es-ES
Segmentation fault (core dumped)

Vidalia exited with the following return code: 139

---

### Post by caralu74 on 2013-04-05
I`ve been trying Tor X86 running on Ubuntu X64 and run ok, without any trouble. So the problem should be from the X86_64Tor version.

---

