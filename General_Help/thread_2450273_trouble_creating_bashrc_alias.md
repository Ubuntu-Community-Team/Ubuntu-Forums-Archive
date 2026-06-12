---
title: "trouble creating bashrc alias"
date: 2020-09-10
forum: General Help
---

### Post by marchello_lippi2 on 2020-09-10
Hi all, 

I'd like to create alias for below command: 
```
[FONT=monospace][COLOR=#000000]/usr/bin/flatpak run com.rafaelmardojai.Blanket[/COLOR][/FONT]
```

The command works perfectly fine from yakuake console, though whenever I try to add alias like below 
```
[FONT=monospace][COLOR=#000000]alias blanket=/usr/bin/flatpak run com.rafaelmardojai.Blanket[/COLOR][/FONT]
```
I receive error: 
> 
[FONT=monospace][COLOR=#000000]$ . ~/.bashrc[/COLOR]
bash: alias: run: not found
bash: alias: com.rafaelmardojai.Blanket: not found
[/FONT]
Please advise.

---

### Post by Dennis N on 2020-09-10
Enclose the alias definition in single quotes:

```
alias blanket='/usr/bin/flatpak run com.rafaelmardojai.Blanket'
```

(Note: I doubt you would need the path to the flatpak command)

---

### Post by marchello_lippi2 on 2020-09-10
Thanks Dennis N.

---

