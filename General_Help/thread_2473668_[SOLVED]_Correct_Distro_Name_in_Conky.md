---
title: "[SOLVED] Correct Distro Name in Conky"
date: 2022-04-09
forum: General Help
---

### Post by richolad-k on 2022-04-09
I'm using Xubuntu 20.04.4 with conky, and this line in my .conkyrc:
Distro: ${alignr}${distribution}
The output in conky is Ubuntu, but I would prefer it to be Xubuntu, which would be more accurate.  Any suggestions would be appreciated.

---

### Post by oldfred on 2022-04-10
I have Kubuntu and do not use conky.
But this is the only place I can find that I have Kubuntu.

[FONT=monospace][COLOR=#008080]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /var/log/installer/media-info [/COLOR]
Kubuntu 20.04.1 LTS "Focal Fossa" - Release amd64 (20200731)

[/FONT][FONT=monospace][COLOR=#008080]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ls /usr/share/xsessions     [/COLOR]
plasma.desktop


[/FONT][FONT=monospace][/FONT]

---

### Post by ActionParsnip on 2022-04-10
Why would you want to monitor that? Isn't the point of conky to monitor resources....?

---

### Post by richolad-k on 2022-04-10
This is a non-response.  The fact is that I do have this specific question.  Conky has whatever uses I want it to have on my machine.

---

### Post by ActionParsnip on 2022-04-10
> **richolad-k said:**
> This is a non-response.  The fact is that I do have this specific question.  Conky has whatever uses I want it to have on my machine.

Indeed but it just seems redundant.

---

### Post by richolad-k on 2022-04-10
Thanks, OldFred.  These locations provide me no help in Xubuntu, however.

---

### Post by deadflowr on 2022-04-10
You can try something like
```
${exec echo $DESKTOP_SESSION}
```
or
Simply put the word Xubuntu in it's place.
```
Distro: ${alignr}Xubuntu
```

---

### Post by richolad-k on 2022-04-11
DeadFlowr: Thanks.  I ended up with:
Distro: ${alignr}${exec lsb_release -ds}
DE: ${alignr}${exec echo $XDG_CURRENT_DESKTOP} (${exec echo $DESKTOP_SESSION})

That yields:
Distro:     Ubuntu 20.04.4 LTS
DE:                  Xfce (xubuntu)

I'll mark this as SOLVED.

---

