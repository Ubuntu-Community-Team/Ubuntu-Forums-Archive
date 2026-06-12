---
title: "i think system boots up but screen is black"
date: 2015-10-14
forum: General Help
---

### Post by righN on 2015-10-14
I went back from school and turned on my computer i see lubuntu logo but after that screen is black. I think system boots up, i waited for some time and monitor go stand-by and when i moved mouse monitor worked again but screen is black.

Lubuntu 15.04

Video AMD Radeon HD 5450

---

### Post by Bashing-om on 2015-10-14
righNrighN; Humm ..

Proprietary graphics driver broke and/or no longer supported ?

What results when booting in 'recovery" mode from grub's boot menu >
or maybe try and boot with the "nomodeset" boot parameter ?

else perhaps boot to terminal and see what we can find out about what is not taking place in the X layer .

[INDENT][INDENT]fault isolation that leads to
[INDENT][INDENT][INDENT][INDENT]restoration
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-10-14
Can you get to any menus on the monitor display? If you can open Settings> Display, you might find the screen is switched off.

You might also try installing arandr and launching it with:

```
arandr
```

... and seeing what's going on. If it was working when you switched off or closed the lid at school, sounds like the machine is simply defaulting to the monitor when it's plugged in. You can change that in Display or using arandr.

---

