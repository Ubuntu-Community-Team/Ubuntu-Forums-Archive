---
title: "Onboard keyboard application running, but not visible"
date: 2022-08-02
forum: General Help
---

### Post by efrio on 2022-08-02
Hi all,

The Onboard keyboard application (1.4.1-2ubuntu7) is running, but not visible - not when Alt-Tabbing or after switching to view all programs running screen mode.

onboard  &

from terminal also results in the same behavior. 

Uninstalled and installed again, still the same.

It used to work fine (last month).

Ubuntu 20.04.4 LTS


Any ideas? Thanks!

---

### Post by sudodus on 2022-08-03
I ran [FONT=Courier New]**sudo apt update && sudo apt full-upgrade**[/FONT] in my Ubuntu 20.04.4 LTS and started **[FONT=Courier New]onboard[/FONT]**. It works for me.

Try to remember what [special things] have happened during the time since onboard worked.

- Have you installed some new program package?
-  Have you changed between Xorg and Wayland?
- Are you running the default desktop environment or something you installed later?
- Is there a problem with some other program too?
- Did you check if onboard is not starting at all, or if it starts, but does not show anything on the desktop?

- What is the output of the following command?
```

ps -ef|grep onboard

```

Edit: Have you clicked on the onboard icon near the top right corner of the screen? You can toggle 'hiding' it that way.

---

