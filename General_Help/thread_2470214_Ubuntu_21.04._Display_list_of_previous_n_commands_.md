---
title: "Ubuntu 21.04. Display list of previous n commands displayed as a selectable list?"
date: 2021-12-22
forum: General Help
---

### Post by Advait on 2021-12-22
[COLOR=#000000][FONT=Arial]I’m a Linux newbie. Here’s what I want. I want to type a simple command in my terminal that displays a numbered list of n previous commands. For example, I type “prevcom 20” (enter) and it displays a numbered list of my previous 20 commands. Then I type in 15 (enter) to execute the 15th command in the list.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Which app(s) adds this functionality to my terminal?[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]It appears that this is not possible with the “history” command.[/FONT][/COLOR]

---

### Post by Holger_Gehrke on 2021-12-22
If you enter 'history 20' you'll get a list of the last twenty commands prefixed with their line numbers in the history file. You can then enter '!' followed by a line number with no space in between the exclamation mark and the number to repeat that command. At least that's the way it works in bash, the default shell on all flavours of Ubuntu. Not exactly what you want, but no need to install anything additional.

Holger

---

### Post by Advait on 2021-12-22
> **Holger_Gehrke said:**
> If you enter 'history 20' you'll get a list of the last twenty commands prefixed with their line numbers in the history file. You can then enter '!' followed by a line number with no space in between the exclamation mark and the number to repeat that command. At least that's the way it works in bash, the default shell on all flavours of Ubuntu. Not exactly what you want, but no need to install anything additional.

Holger

Worked perfect. Thanks!

---

