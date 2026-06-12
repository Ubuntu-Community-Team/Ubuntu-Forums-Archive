---
title: "Cannot login after mistyped password"
date: 2013-01-25
forum: General Help
---

### Post by Spiralagnus on 2013-01-25
I'm using Ubuntu 12.10 with Xfce 4.10 and GDM.  If I try to log in and get my password right, it logs me in just fine.  If I accidentally mistype my password, I get "Authentication failure", which is expected.  However, if I mistype my password and then go back and type my password in correctly, a green check mark appears next to my name in the login screen with the words "currently logged in", and it doesn't log me in.  I have to restart my computer before I can log in.

Any help would be appreciated.  Please let me know if you require more information.

---

### Post by Spiralagnus on 2013-01-31
Anybody?  This is still a persistent problem, and I would appreciate any insight anybody has.  Thanks in advance.

---

### Post by wiebeest on 2013-02-01
> **Spiralagnus said:**
> If I accidentally mistype my password, I get "Authentication failure", which is expected.  However, if I mistype my password and then go back and type my password in correctly, a green check mark appears next to my name in the login screen with the words "currently logged in", and it doesn't log me in.  

I just checked under regular Ubuntu 64-bit by typing the wrong password on purpose, which obviously resulted in "Authentication failure" message but after re-typing my password correctly afterwards it logged me in just fine. 

So to narrow it down, could this obvious bug be a Xfce-specifical?
Also, are you on 32 or 64-bit?

---

### Post by Spiralagnus on 2013-02-01
I suppose it could be XFCE-specific.  I started with a minimal Ubuntu install and slowly built it up using XFCE, so it could be something unique to my setup.  I'm using 64-bit.

Any thoughts or advice?

---

### Post by sudodus on 2013-02-01
> **Spiralagnus said:**
> I suppose it could be XFCE-specific.  I started with a minimal Ubuntu install and slowly built it up using XFCE, so it could be something unique to my setup.  I'm using 64-bit.

Any thoughts or advice?
I run Lubuntu 12.04 non-pae on an old IBM Thinkpad. I have installed xubuntu-desktop into it. So I tried to log in to an XFCE-session by first typing a bad password, and then typing it correctly. It works for me, I get logged in (without reboot).

What log in screen are you using?

---

### Post by Spiralagnus on 2013-02-01
> **sudodus said:**
> I run Lubuntu 12.04 non-pae on an old IBM Thinkpad. I have installed xubuntu-desktop into it. So I tried to log in to an XFCE-session by first typing a bad password, and then typing it correctly. It works for me, I get logged in (without reboot).

Interesting.  Any ideas what could be causing the problem on my end?  I'm not sure where to look.

---

### Post by sudodus on 2013-02-01
- What log in screen are you using?

- Can you log in to a text screen with this hotkey combination?

***ctrl + alt + F3***

[... F1 -- F6] gives you text screens and

***ctrl + alt + F7*** turns you back to the graphics screen.

---

### Post by Spiralagnus on 2013-02-01
> **sudodus said:**
> - What log in screen are you using?

- Can you log in to a text screen with this hotkey combination?

***ctrl + alt + F3***

[... F1 -- F6] gives you text screens and

***ctrl + alt + F7*** turns you back to the graphics screen.

I'm using GDM for my login.  I can log into the text screen just fine.  In fact, in the text screen, I can log in with the wrong password, then try the right one, and it works.  So it sounds like it's a GDM problem.  Any thoughts?

---

### Post by sudodus on 2013-02-01
Try ***lightdm*** (that is what I use).

---

### Post by Spiralagnus on 2013-02-04
> **sudodus said:**
> Try ***lightdm*** (that is what I use).

Good call.  Not only does lightdm work perfectly, but one look tells me that it's much more robust than gdm ever was.  I'm sticking with lightdm from here on out.

---

