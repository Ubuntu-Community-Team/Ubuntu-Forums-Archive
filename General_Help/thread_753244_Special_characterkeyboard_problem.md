---
title: "Special character/keyboard problem"
date: 2008-04-12
forum: General Help
---

### Post by maxdom on 2008-04-12
Today I discovered that when I remote login to my Ubuntu 7.10 server from either of my two WinXP PC's I get a funny character problem in the shell.
I tried from both Cygwin and Putty (SSH), but the same thing happened.

When I try to write special characters like æ, ø, å, ä, ö, â, ô and so forth, the character is delayed until the next key is punched. Only when I press a "normal" key twice will it catch up.

If I start a new xterm and display it on the PC (through cygwin) there is no problem.

I should mention I have a problem with the norwegian special characters also in the cygwin local shell, but that behaves differently, and involves not showing the characters at all... And besides, the same happens from Putty, so I think this is unrelated.

The Ubuntu install is not tweaked but has been upgraded to 7.10 from earlier versions.

Although I just discovered this today, I can't say for sure it hasn't been there for a while.
I usually just start a couple of xterm's straight away, and then there is no problem.

---

