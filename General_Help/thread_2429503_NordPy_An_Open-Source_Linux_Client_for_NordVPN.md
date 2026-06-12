---
title: "NordPy: An Open-Source Linux Client for NordVPN"
date: 2019-10-19
forum: General Help
---

### Post by SUPERFITTER on 2019-10-19
Has anyone used: 
**[SIZE=2]NordPy: An Open-Source Linux Client for NordVPN[/SIZE]**

[SIZE=2]When I run: [SIZE=2]**install.sh**[/SIZE] from the terminal.  I get command not found.  

Thank You[/SIZE]

---

### Post by Holger_Gehrke on 2019-10-19
No, I haven't. But there's just one possible reason for that message if the file exists, AFAIK. The shell looks for executables only in directories that are in the (colon-separated) list stored in the variable PATH. The current working directory (.) is for security reasons intentionally not in that list. So to execute the program you need to give the shell the path to it by calling it as './install.sh' (assuming that the program is in the current working directory) or with whatever relative or absolute path that can be used to find the file.

Holger

---

### Post by SUPERFITTER on 2019-10-20
I tried the path and got this:

 bash: ./install.sh: No such file or directory

---

### Post by Skaperen on 2019-10-20
how did you load the files?  where did you get them from?

---

### Post by SUPERFITTER on 2019-10-20
Terminal

[COLOR=#0000ff]https://www.fossmint.com/nordpy-linux-client-for-nordvpn/[/COLOR]

---

