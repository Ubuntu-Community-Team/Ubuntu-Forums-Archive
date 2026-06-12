---
title: "how to start ubuntu via ssh ?"
date: 2014-05-04
forum: General Help
---

### Post by devi2 on 2014-05-04
[COLOR=#000000]Hi all,[/COLOR]

[COLOR=#000000]([/COLOR][I]excuse me for my bad english)

[/I]I am connecting via ssh to my server named guess :

[B][COLOR=#000000]devi@devi-ThinkPad-T60:~$ ssh root@guess[/COLOR]
[COLOR=#000000]root@guess's password: [/COLOR]
[/B][COLOR=#000000][B]Welcome to Ubuntu 13.10 (GNU/Linux 3.11.0-18-generic x86_64)

(...)[/B]




But since I did a "reboot now", I can no longer connect to it :
[/COLOR][COLOR=#000000]
**root@guess:~# reboot now**[/COLOR][B]


[COLOR=#000000]Message de diffusion de root@guess[/COLOR]
[COLOR=#000000](/dev/pts/0) à 7:53...[/COLOR]


[COLOR=#000000]L'ordinateur va s'arrêter pour maintenance MAINTENANT ![/COLOR]
[COLOR=#000000]root@guess:~# Connection to guess closed by remote host.[/COLOR]
[COLOR=#000000]Connection to guess closed.
[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]devi@devi-ThinkPad-T60:~$ ssh root@guess[/COLOR]
[COLOR=#000000]ssh: connect to host guess port 22: Connection refused
[/COLOR][/B][COLOR=#000000][B]
(...)
[/B]


I've searched on several forums and find out that reboot now command act like stop the server and not like reboot it.
[/COLOR][COLOR=#000000]I don't know how to start the server via ssh.
I am a beginner and I need some help please.
[/COLOR][COLOR=#000000]
Regards,
Devi


[/COLOR]

---

### Post by ian-weisser on 2014-05-04
If you really halted your server, then there is no way that I know of to start it again using ssh. Your ssh server isn't running to connect to.
A human at the server should reboot the the system by pushing the power button.

---

### Post by radwanski-michal-a on 2014-05-04
Now, act like ian-weisser told, but for future, there is a helpful util named Wake On Lan: [http://en.m.wikipedia.org/wiki/Wake-on-LAN](http://en.m.wikipedia.org/wiki/Wake-on-LAN)

---

