---
title: "how to add a graphical login again"
date: 2024-03-11
forum: General Help
---

### Post by ValentynPrumers on 2024-03-11
I recently removed a graphic login:

[FONT=Arial]1. uncomment grub_terminal=console in /etc/default/grub
2. sudo update-grub
3. sudo systemctl enable multi-user.target --force
4. sudo systemctl set-default multi-user.target

Say i want my graphic login (SDDM) back.  Just put a comment in the grub file and run update-grub. But how do i reverse step 3 and 4?[/FONT]
[FONT=Arial]

[/FONT]

---

### Post by MAFoElffen on 2024-03-11
Change multi-user target to graphical.target as the default in line #4. 

You don't need to execute line #3. multi-user.target and graphical.target are both by default "active"...
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo systemctl status {multi-user.target,graphical.target}
&#9679; multi-user.target - Multi-User System
     Loaded: loaded (/lib/systemd/system/multi-user.target; static)
     Active: active since Mon 2024-03-04 18:30:41 PST; 6 days ago
       Docs: man:systemd.special(7)

Mar 04 18:30:41 Mikes-ThinkPad-T520 systemd[1]: Reached target Multi-User System.

&#9679; graphical.target - Graphical Interface
     Loaded: loaded (/lib/systemd/system/graphical.target; static)
     Active: active since Mon 2024-03-04 18:30:41 PST; 6 days ago
       Docs: man:systemd.special(7)

Mar 04 18:30:41 Mikes-ThinkPad-T520 systemd[1]: Reached target Graphical Interface.

```

---

### Post by ValentynPrumers on 2024-03-12
Thanks :)

---

