---
title: "Battery Life :("
date: 2007-04-21
forum: General Help
---

### Post by FXFman1209 on 2007-04-21
Hi everyone! I've been using Ubuntu Edgy for about a month now, and now I've just upgraded to Feisty. Anyway, every since I put Edgy onto my laptop, I've noticed that the battery life was significantly lower than that of Windows XP. Ubuntu is about an hour shorter than XP's.

Is there anyway to extend the battery life?

---

### Post by madmetal on 2007-04-21
> **FXFman1209 said:**
> Hi everyone! I've been using Ubuntu Edgy for about a month now, and now I've just upgraded to Feisty. Anyway, every since I put Edgy onto my laptop, I've noticed that the battery life was significantly lower than that of Windows XP. Ubuntu is about an hour shorter than XP's.

Is there anyway to extend the battery life?

is ACPI (Advanced Configuration and Power Interface) on?
what laptop do you have? certain laptops have problem with acpi ..

---

### Post by FXFman1209 on 2007-04-21
Err... where do I check to see if ACPI is on? Sorry, I'm a bit new.

I'm also using a Dell Inspiron E1505

---

### Post by madmetal on 2007-04-21
you can add acpi=force to the end of the kernel line in /boot/grub/menu.lst to force acpi on and then see if there is improve at battery life..
well from a little search i think your laptop is ok but has some problems with wireless card?
maybe wireless is always on and drains your battery?

---

### Post by FXFman1209 on 2007-04-21
Lol its funny you say that. I've actually JUST got wireless working for the first time today so I doubt that would have any effect on the battery life, since it hasn't been working. Thanks! I'll try it out and let you know.

---

