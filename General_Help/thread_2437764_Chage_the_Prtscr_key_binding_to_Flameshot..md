---
title: "Chage the Prtscr key binding to Flameshot."
date: 2020-02-29
forum: General Help
---

### Post by suvam4549 on 2020-02-29
Hello all. Fresh Lubuntu 18.04.4 install here. The OS is fast as light yeah but the screenshot tool is poor. I have been using Flameshot for a long time on KDE. The thing is I can't figure out how to set FlameShot as the default screenshot tool here. I tried **lxhotkey** but it says that it can't change since it's already used by another program. :( What to do, please help. Note that the system is still on LXDE, not LXQt just in case there's some confusion there.

---

### Post by guiverc on 2020-02-29
In preferences "**Setup Hot Keys**" on my system (window will open as *lxhotkey*) I can see in programs that **PRINT** for my system is handled by [B]lxsession-default screenshot

[/B]To view the that option open preferences "**Default Applications for LXSession**" which for my system shows the Screenshot Manager is set for **scrot** for my Lubuntu 18.04 system.

Please note my system may not be default, I can't recall if I've changed anything here, but I very much doubt it.  In your case just change `scrot` to be `flameshot`.

---

### Post by suvam4549 on 2020-02-29
Nah, didn't work. And lubuntu crashed on me in the middle of VLC installation... Well, I think it's time that LXDE is bid a sweet farewell. VLC looks terrifying, literally.. LXDE is unable to handle new qt apps.. And Flameshot somehow got corrupt on its own and nothing works anymore. Time to upgrade to 19.10 to have some sanity back. I'll be here after I'm done upgrading. Thank you for the input.

---

### Post by GhX6GZMB on 2020-02-29
In Lubuntu (LXQt) it's pretty easy. Report back when you're that far.

---

