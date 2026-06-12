---
title: "limits.conf not being read when logging in"
date: 2014-07-16
forum: General Help
---

### Post by gabriel403 on 2014-07-16
[COLOR=#000000][FONT=proxima-nova]I have 2 entries in my limits.conf,[/FONT][/COLOR]
*       hard        nofile      10240
*       soft        nofile      4096
[COLOR=#000000][FONT=proxima-nova]but running ulimit -Sn or ulimit -Hn only displays the default values.

gabriel@server:~$ ulimit -Sn
1024
gabriel@server:~$ ulimit -Hn
4096
[/FONT][/COLOR]
[COLOR=#000000][FONT=proxima-nova]It works fine on one server but on another it's as if they're being ignored.
I did have a problem with apt-get autoremove for some old kernels on this one server which I didn't have on the other, I didn't note it down but I'm quite able to reboot.[/FONT][/COLOR]

---

