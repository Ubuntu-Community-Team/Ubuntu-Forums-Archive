---
title: "Add New User - settings in /etc/adduser.conf don't work?"
date: 2021-04-17
forum: General Help
---

### Post by GhX6GZMB on 2021-04-17
As a follow-up to my thread about banning "other" from the $HOME directories:
[https://ubuntuforums.org/showthread.php?t=2460569](https://ubuntuforums.org/showthread.php?t=2460569)
and the announcement from discourse.ubuntu.com in the same thread:
[https://discourse.ubuntu.com/t/private-home-directories-for-ubuntu-21-04-onwards/19533](https://discourse.ubuntu.com/t/private-home-directories-for-ubuntu-21-04-onwards/19533)

I've modified my /etc/adduser.conf file to have the line: [COLOR=#434343][FONT=Consolas]DIR_MODE=0750 instead of the default [/FONT][/COLOR][COLOR=#434343][FONT=Consolas]DIR_MODE=0755[/FONT][/COLOR][COLOR=#434343][FONT=Consolas]

This has no effect, unfortunately. Attached the result of adding a new user ("testing_ab"):

[/FONT][/COLOR]```
macro@macro-pc:/home$ la -la
total 40
drwxr-xr-x  7 root       root        4096 Apr 17 23:06 .
drwxr-xr-x 20 root       root        4096 May  5  2020 ..
drwxr-x--x 15 abguest    abguest     4096 Apr 14 23:45 abguest
drwx------  2 root       root       16384 May  4  2020 lost+found
drwxr-x--x 17 macro      macro       4096 Apr 17 23:05 macro
drwxr-xr-x  2 testing_ab testing_ab  4096 Apr 17 23:06 testing_ab
drwxr-xr-x  9 root       root        4096 Apr 15 00:18 timeshift
macro@macro-pc:/home$ 

```

What's wrong here? Why does "testing_ab" still have the "r" for "other" set?

EDIT: I've tried DIR_MODE=0751 instead. No change.

---

### Post by HermanAB on 2021-04-18
The answer may be in here:
[https://linuxdigest.com/howto/useradd-vs-adduser/](https://linuxdigest.com/howto/useradd-vs-adduser/)

I think you need to read the script to see how it works.

---

### Post by ActionParsnip on 2021-04-18
Watch the umask too

---

