---
title: "Checkgmail not in system tray"
date: 2006-11-30
forum: General Help
---

### Post by oet on 2006-11-30
Hello all,

I installed Checkgmail using "sudo apt-get install checkgmail". It shows the notifications when I start it (either through console or as a startup program). This happens at the left of the gnome panel. However Checkgmail does not appear in the system tray at all! Does anyone know how to fix this problem and get the red/blue gmail icon in the system tray?

---

### Post by kwaanens on 2006-11-30
I'm using gmail-notify (sudo apt-get install gmail-notify)

Add it to System > Settings > Sessions > Start-up programs

- Ketil

---

### Post by Tikhon on 2006-11-30
> **kwaanens said:**
> I'm using gmail-notify (sudo apt-get install gmail-notify)

Add it to System > Settings > Sessions > Start-up programs

- Ketil

IMO, checkmail is better

---

### Post by oet on 2006-11-30
I have tried Checkgmail and Gmail-notify. However I don't see a system tray icon. Just the notifications (Checkgmail upperleft of gnome, Gmail-notify undermost right). So my questions remains: why don't I see a system tray icon after installation (even using them as startup program).

---

### Post by Tikhon on 2006-11-30
Other applications display own icons in tray?

---

### Post by oet on 2006-11-30
> **Tikhon said:**
> Other applications display own icons in tray?

Yes. After I install and configure Checkgmail I get notifications, but see no tray icon.

[IMG]http://www.akelig.nl/systemtray.jpg[/IMG]

---

### Post by Tikhon on 2006-12-01
Sorry, but i not see system tray applet on screenshot.
Right click on gnome panel -> Add to Panel -> Notification Area

---

### Post by kwaanens on 2006-12-01
> **Tikhon said:**
> IMO, checkmail is better

I have been using gmail-notify for a long time, and didn't even know about checkgmail. Now I know, and trying it out :) Showing up in my notification area.
Thanks!

- Ketil

---

### Post by oet on 2006-12-01
> **Tikhon said:**
> Sorry, but i not see system tray applet on screenshot.
Right click on gnome panel -> Add to Panel -> Notification Area

Seems that was the whole problem. I must have deleted the notifications area some while ago and did not even realize it was gone :D. I guess you noticed it by the missing grey dots or update star?

Anyway, thx.

---

### Post by Tikhon on 2006-12-01
> **oet said:**
> I guess you noticed it by the missing grey dots or update star?

no no :) missing gaim tray icon ;)

---

### Post by strabes on 2006-12-01
PLEASE it's called the "notification area" It's not even (properly) called the system tray in windows.

---

### Post by Tikhon on 2006-12-01
> **strabes said:**
> PLEASE it's called the "notification area" It's not even (properly) called the system tray in windows.

what's the difference?
e.g. in xfce this applet also named System Tray ;)

---

