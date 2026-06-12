---
title: "How to setup Gnokii to use IrDA ??"
date: 2007-04-29
forum: General Help
---

### Post by bazant on 2007-04-29
Hello!

I'm trying to use Gnokii to manage my phone via IrDA. The prolem is I cannot find in Google any information how to set up gnokii for that.
IrDA seems to work fine:

[FONT="Courier New"]brzoskwinia@brzoskwinia-ubuntu:~$ cat /proc/net/irda/discovery 
IrLMP: Discovery log:

nickname: Nokia 6310i, hint: 0xb125, saddr: 0xb240085d, daddr: 0x000092c8[/FONT]

But if I configure .gnokiirc in home dir to use port = /dev/ircomm0
I get only:
[FONT="Courier New"]brzoskwinia@brzoskwinia-ubuntu:~$ gnokii --monitor
GNOKII wersja 0.6.13
Gnokii serial_open: open: No such file or directory
Nie mog&#322;em otworzy&#263; urz&#261;dzenia FBUS: No such file or directory
Gnokii serial_open: open: No such file or directory
Nie mog&#322;em otworzy&#263; urz&#261;dzenia FBUS: No such file or directory
Gnokii serial_open: open: No such file or directory
Nie mog&#322;em otworzy&#263; urz&#261;dzenia FBUS: No such file or directory
Nieudana inicjalizacja interfejsu telefonu: Command failed. Koniec.
[/FONT]

This means that I specified wrong port, am I right?? What should I do to use IrDA i gnokii/xgnokii ??

---

### Post by bazant on 2007-04-29
OK, right - I just had some error in .gnokiirc hnow it works fine. Sorry for unnecessary post.

---

