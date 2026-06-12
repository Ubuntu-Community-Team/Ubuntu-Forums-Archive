---
title: "Terminal Output Colours"
date: 2021-03-23
forum: General Help
---

### Post by Geoff_Lane on 2021-03-23
I use the default terminal for commands.

Puzzled why terminal output colours differ if I enter commands directly or via a script.

If I enter the following direct into terminal my GREP search items are highlighted in [COLOR=#ff0000]**RED**[/COLOR]

```
sudo iwlist wlp2s0 scan | grep -E 'ESSID|Signal|Quality'
```

If I enter the command via a script file output same but GREP search items are in black.

Not a major issue but nice the have searched items in [COLOR=#ff0000]**RED**[/COLOR] - Is there a way of doing this via the script?

Geoff

---

### Post by The Cog on 2021-03-23
Interesting. I just learned something. By default, it switches depending on whether it is outputting to a terminal or to a pipe.
This fixes it:
```
sudo iwlist wlp2s0 scan | grep -E --colour=always 'ESSID|Signal|Quality'
```

---

### Post by Impavidus on 2021-03-23
One of the default settings you get as a user on Ubuntu as a small list of aliases. You can view them with the **alias** command. One of these aliases adds the --color=auto option to grep. These aliases aren't used when you run a script.

---

### Post by The Cog on 2021-03-23
Haha - I hadn't realised that. 
Thanks, Impavidus.

---

### Post by TheFu on 2021-03-23
[https://tldp.org/LDP/abs/html/files.html](https://tldp.org/LDP/abs/html/files.html) has some startup files.

At the start of my .bashrc, it checks if it is running as a script or interactive. If a script, it returns immediately. None of my custom bash functions or aliases are available. This prevents lots of script failures and self-inflicted problems.  

Before I added the check, some systems upgrades failed because I don't use the system perl most of the time. My environment configures different perl versions for custom code and some of the more specialized programs expected the system perl and system versions of perl modules. This could happen with other languages like ruby or python too.

---

### Post by Geoff_Lane on 2021-03-26
> **The Cog said:**
> Interesting. I just learned something. By default, it switches depending on whether it is outputting to a terminal or to a pipe.
This fixes it:
```
sudo iwlist wlp2s0 scan | grep -E --colour=always 'ESSID|Signal|Quality'
```

Thanks Cog, that has sorted it 8-)

Geoff

---

