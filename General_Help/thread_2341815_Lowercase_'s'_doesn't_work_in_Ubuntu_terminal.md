---
title: "Lowercase 's' doesn't work in Ubuntu terminal"
date: 2016-10-31
forum: General Help
---

### Post by Salil_Surendran on 2016-10-31
Anyone else had this very infuriating problem that has been bugging me for the past hour. The lowercase 's' and only that key alone doesn't ever get printed on my terminal or xterm. Every other key works fine and the 's' key words fine in any other application but not in terminal. Googling just says a custom keyboard shortcut has been set to s but looking at all the keyboard shortcuts in System -> Keyboard -> Custom Shortcuts shows no such shortcut and I cleared the few that had 's' in it. Rebooting etc. didn't help. Another interesting thing is that if I press Ctrl + Shift + V which was the key for paste then it lets me type 's' but after that I can't enter s anymore. I have used gconf-editor and dconf-editor and have reset all CCSM settings and restarted unit but nothing is working. Any help is very much appreciated!!!

---

### Post by Salil_Surendran on 2016-11-01
Ok with more investigation I found out that the problem occurs only in a bash shell. If I run csh the issue doesn't happen. So something happened that remapped the bash keys. Also along with Ctrl + Shift + V if I press Ctrl + V it lets me type s once in bash.

---

### Post by Impavidus on 2016-11-01
ctrl-v means in a terminal that [the next character must be used literally](https://en.wikipedia.org/wiki/Control-V) and not get interpreted by the terminal. So the terminal must be interpreting the s character. I've got no idea what may cause the problem.

---

### Post by vasa1 on 2016-11-01
You were pointed to [a duplicate question]("http://askubuntu.com/questions/844027/lowercase-s-doesnt-work-in-ubuntu-terminal#comment1293658_844027"): [http://askubuntu.com/questions/616525/i-cant-type-a-b-when-im-in-the-command-line](http://askubuntu.com/questions/616525/i-cant-type-a-b-when-im-in-the-command-line). The [accepted answer there]("http://askubuntu.com/a/617646") suggested looking at 
> readline's configuration files: ~/.inputrc, /etc/inputrc, or the one referred by $INPUTRC.Did that help?

---

### Post by Salil_Surendran on 2016-11-01
> **vasa1 said:**
> You were pointed to [a duplicate question]("http://askubuntu.com/questions/844027/lowercase-s-doesnt-work-in-ubuntu-terminal#comment1293658_844027"): [http://askubuntu.com/questions/616525/i-cant-type-a-b-when-im-in-the-command-line](http://askubuntu.com/questions/616525/i-cant-type-a-b-when-im-in-the-command-line). The [accepted answer there]("http://askubuntu.com/a/617646") suggested looking at 
Did that help?

[COLOR=#111111][FONT=Ubuntu]It was a duplicate of the link you had posted.[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu] I had added this line in my /etc/inputrc "stty ....." . That was making 's' misbehave.[/FONT][/COLOR]

---

### Post by vasa1 on 2016-11-01
So you can mark this thread [SOLVED]. Thanks!

---

