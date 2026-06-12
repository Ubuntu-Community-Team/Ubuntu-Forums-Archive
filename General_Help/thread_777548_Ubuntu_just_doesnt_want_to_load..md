---
title: "Ubuntu just doesnt want to load."
date: 2008-05-01
forum: General Help
---

### Post by MrBiggles5 on 2008-05-01
I installed Ubuntu 8.04 with the Wubi installer, it installed fine and I rebooted my computer and selected ubuntu, however it just gets stuck at this screen!

[IMG]http://img175.imageshack.us/img175/5091/photo0029tx9.jpg[/IMG]

I did text mode and this came up:
[IMG]http://img356.imageshack.us/img356/9127/photo0030em9.jpg[/IMG]


I have ran Ubuntu in VMWare before and it worked fine, that was 7.10 though.

Any reasons why its doing this?

---

### Post by ago on 2008-05-01
Probably an ACPI issue (or some other workaround such as irqpoll or all_generic_ide might be needed).

Press esc at boot and select the 3rd option.

---

### Post by MrBiggles5 on 2008-05-04
> **ago said:**
> Probably an ACPI issue (or some other workaround such as irqpoll or all_generic_ide might be needed).

Press esc at boot and select the 3rd option.

I did what you suggested and I got this:
[IMG]http://img376.imageshack.us/img376/6826/photo0035dx2.jpg[/IMG]

I am completly stumped.

---

### Post by ago on 2008-05-04
What is the first item when you press ESC after "ubuntu" at boot?

---

### Post by MrBiggles5 on 2008-05-04
> **ago said:**
> What is the first item when you press ESC after "ubuntu" at boot?

Here is a picture after I press ESC:

[IMG]http://img141.imageshack.us/img141/5931/photo0036vk0.jpg[/IMG]

---

### Post by ago on 2008-05-04
Does booting from the Live CD work?

---

### Post by MrBiggles5 on 2008-05-04
> **ago said:**
> Does booting from the Live CD work?

I ran the installer from my drive not from a Cd, but I havnt tried that yet, ill go try it now and post the result.

---

### Post by MrBiggles5 on 2008-05-04
Here is the result, the two merged together, awsome.

[IMG]http://img393.imageshack.us/img393/414/photo0038ed8.jpg[/IMG]

---

### Post by MrBiggles5 on 2008-05-06
Does anyone know whats wrong?

(Sorry for the triple post here)

---

