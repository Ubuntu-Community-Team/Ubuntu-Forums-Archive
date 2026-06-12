---
title: "Software installed through Software Center won't show up in the menu"
date: 2019-10-24
forum: General Help
---

### Post by frozen-artichoke on 2019-10-24
Hello, I'm using Kubuntu 19.10, I have installed couple of programs from the software center (rambox and slack) but they don't show up in any menu. If I search them through the top bar I can only find the relative folder (/snap/rambox or /snap/slack) but the only way to lunch the actual program is to open the software center, navigate to the program and then click lunch.  Am i missing something? Thanks!

---

### Post by uRock on 2019-10-24
Have you tried restarting the system. I've had to do that in the past to get some newly installed programs to show.

---

### Post by TheFu on 2019-10-24
> **uRock said:**
> Have you tried restarting the system. I've had to do that in the past to get some newly installed programs to show.

Logout and login should be sufficient.  Needing a reboot to rebuild menus would be a complete failure.

---

### Post by uRock on 2019-10-24
> **TheFu said:**
> Logout and login should be sufficient.  Needing a reboot to rebuild menus would be a complete failure.

I don't actually reboot for that purpose. If I install something and it doesn't show up, then it just waits until the next restart, which happens once or twice a week.

---

### Post by cruzer001 on 2019-10-24
If the above will not work, I guess a snaps package can still be open in terminal.

---

### Post by frozen-artichoke on 2019-10-25
Unfortunately rebooting didn't work and I'm not sure how to check if I have snaps packages open in the terminal but even if they were, they wouldn't stay open after a reboot...

---

### Post by frozen-artichoke on 2019-10-25
I have found the problem. After installing zsh no snap program can be found in the menu, that's because zshenv have a bug and doesn't load the /snap/bin path...apparently the bug hasn't been solved yet so I guess I will continue without zsh..!

---

