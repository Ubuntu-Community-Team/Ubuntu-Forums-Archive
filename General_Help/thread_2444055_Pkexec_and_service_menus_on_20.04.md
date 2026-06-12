---
title: "Pkexec and service menus on 20.04"
date: 2020-05-24
forum: General Help
---

### Post by donbcilly on 2020-05-24
I don't believe this has been addressed before - I've searched.

I have a few service menus that use pkexec. They work just fine on neon.

On Kubuntu 20.04, I used one. No pkexec pop-up.
I tried them all. No pkexec pop-up.
If I try pkexec <command> **from konsole**, it works.
As a **Dolphin** service menu, it does **not**.

So: the same exact service menus work on neon and K18 and **not** on K20 (they share the same /home).
I have groogled around extensively and found nothing.

I tried it on K20.04 on the laptop. Practically virgin installation (never use it). They don't work.
I tried it on Kubuntu 18.04. They work just fine.
Now, has nobody really noticed that pkexec **doesn't** work with service menus on Kubuntu 20.04?
Or what's going on?

If anyone would like to try and hasn't got one handy that needs pkexec, here's a simple one to "touch" root-owned files.

```
[Desktop Entry]
Type=Service
X-KDE-ServiceTypes=KonqPopupMenu/Plugin
MimeType=all/all;
Actions=stouch;
Encoding=UTF-8
Icon=application-x-cd-image

[Desktop Action stouch]
Name=Sudo touch
Icon=edit-redo
Exec=pkexec touch %f; kdialog --title="Touch" --passivepopup="Touched";fi

```

---

