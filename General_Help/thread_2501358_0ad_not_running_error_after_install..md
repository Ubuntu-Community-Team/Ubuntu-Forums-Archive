---
title: "0ad not running error after install."
date: 2024-10-04
forum: General Help
---

### Post by dosh on 2024-10-04
I am getting an error after loading and the game is not starting. Have tried loading it in varies ways. Have gone back to installing it via Discover to get the error message Then tried running it both via the menu, nothing happens and the via the terminal....the following error

CreateDirectories: failed to mkdir /home/philip/.config/0ad (mode 448)
Unable to open crashlog.txt for writing (please ensure the log directory is writable)
Location: debug.cpp:195 (debug_WriteCrashlog)

Call stack:

(0x59d984ded10e) /snap/0ad/592/binaries/system/pyrogenesis(+0x5ed10e) [0x59d984ded10e]
(0x59d984da18a1) /snap/0ad/592/binaries/system/pyrogenesis(+0x5a18a1) [0x59d984da18a1]
(0x59d984da303b) /snap/0ad/592/binaries/system/pyrogenesis(+0x5a303b) [0x59d984da303b]
(0x59d984da2a29) /snap/0ad/592/binaries/system/pyrogenesis(+0x5a2a29) [0x59d984da2a29]
(0x59d984da3c30) /snap/0ad/592/binaries/system/pyrogenesis(+0x5a3c30) [0x59d984da3c30]
(0x59d984db7fb6) /snap/0ad/592/binaries/system/pyrogenesis(+0x5b7fb6) [0x59d984db7fb6]
(0x59d984db7cdc) /snap/0ad/592/binaries/system/pyrogenesis(+0x5b7cdc) [0x59d984db7cdc]
(0x59d984db7c0d) /snap/0ad/592/binaries/system/pyrogenesis(+0x5b7c0d) [0x59d984db7c0d]
(0x59d984a7ad17) /snap/0ad/592/binaries/system/pyrogenesis(+0x27ad17) [0x59d984a7ad17]
(0x59d98485b927) /snap/0ad/592/binaries/system/pyrogenesis(+0x5b927) [0x59d98485b927]
(0x59d9848486f7) /snap/0ad/592/binaries/system/pyrogenesis(+0x486f7) [0x59d9848486f7]
(0x7072246e2c87) /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xe7) [0x7072246e2c87]
(0x59d984859a6a) /snap/0ad/592/binaries/system/pyrogenesis(+0x59a6a) [0x59d984859a6a]

errno = 30 (?)
OS error = ?


It has been a number of years between me having Linux installed so have forgotten a lot. So please explain as well as possible in easy terms. Thanks

---

### Post by dosh on 2024-10-05
No idea why now working,

---

