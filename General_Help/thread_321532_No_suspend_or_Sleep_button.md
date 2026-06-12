---
title: "No suspend or Sleep button"
date: 2006-12-19
forum: General Help
---

### Post by hadiriazi on 2006-12-19
Hi all

I have no suspend or sleep button for my PC.
I have beryl installed and I don't know exactly if I had those options before installing beryl.

Here is the result after I issue the command:

```
cat /sys/power/state
**standby disk **
```

I also have done this:

```
gdm-signal -s
```

It just sleeps the monitor and the system is still in normal power mode!! and I try to bring the monitor or the system out of suspend after that command but no use.

How could I add suspend ability to my PC??
Please help

p.s I have done lots of searching on this forum but they were all for laptops

---

### Post by 23meg on 2006-12-19
Assuming you're using GNOME, when you hit System / Quit, do you get a suspend option?

---

### Post by hadiriazi on 2006-12-19
> **23meg said:**
> Assuming you're using GNOME, when you hit System / Quit, do you get a suspend option?

no suspend option and yes using gnome.

---

### Post by 23meg on 2006-12-19
Are you sure your computer supports suspend? Anyway, try enabling the button by checking the /apps/gnome-power-manager/can_suspend key in gconf-editor.

---

### Post by hadiriazi on 2006-12-19
> **23meg said:**
> Are you sure your computer supports suspend? Anyway, try enabling the button by checking the /apps/gnome-power-manager/can_suspend key in gconf-editor.

Well I'm sure that I could suspend or sleep the PC in windows so...
how do I enable the button? no /apps/...

Please direct by command detail.

Thnx

---

### Post by yopnono on 2006-12-19
> **hadiriazi said:**
> Well I'm sure that I could suspend or sleep the PC in windows so...
how do I enable the button? no /apps/...

Please direct by command detail.

Thnx

Open login manager ```
system > administration > login window
```
 Then check the ```
menu bar
``` boxes it's 2 of them

---

### Post by hadiriazi on 2006-12-19
Hi there;

Thanks for the reply. The menu is already checked!! Any other solutions. Maybe this issue is cuz of beryl?! Any ideas?

---

### Post by 23meg on 2006-12-19
Hit Alt+F2, type "gconf-editor", and locate the key I mentioned.

---

### Post by hadiriazi on 2006-12-19
> **23meg said:**
> Hit Alt+F2, type "gconf-editor", and locate the key I mentioned.
Thanks for the replies. Here is a screen of what I have. The key that you mentioned was checked from before!!

---

