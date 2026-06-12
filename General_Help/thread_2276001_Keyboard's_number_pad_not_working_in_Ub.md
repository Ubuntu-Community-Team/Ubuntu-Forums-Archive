---
title: "Keyboard's number pad not working in Ub"
date: 2015-04-29
forum: General Help
---

### Post by Robbyx on 2015-04-29
I have reinstalled Ubuntu 14.04 today. 

At my login I can enter numbers from the right hand number pad on the keyboard.

Once logged in the number pad no longer works and I can only enter numbers from the number keys above the keyboard. 

I have tested two keyboard layouts and both make no difference to the keypad. The keyboard layouts do match my keyboard. 

What is the likely solution to this?

---

### Post by Bashing-om on 2015-04-29
Robbyx; Ho !

Maybe bios ?

In my bios (Phoenix) I have the setting to enable the num pad . To use the num pad I have to shift+<number> .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by Robbyx on 2015-04-29
Thanks. I am able to use the number pad to login as a user, but it stops working once I have logged in. I therefore doubt if it is the bios.

---

### Post by Bashing-om on 2015-04-29
Robbyx; Maybe;

But consider, Bios looks about and sees what the hardware is, and passes this info off to grub, now grub also has drivers - for the keyboard for 1, it also passes off to the kernel what drivers are available. The kernel drivers that the GUI uses are not loaded until the GUI is started .

So it all goes back to what bios sees and what it passes off .

[INDENT][INDENT]a web of complexity
[/INDENT][/INDENT]

---

### Post by Robbyx on 2015-04-29
I checked the bios and the usb keyboard was on. I then pushed the keyboard usb connection and nothing moved but now the keypad is working! Thanks.

R

---

### Post by Bashing-om on 2015-04-29
Robbyx; Good deal .

Stranger things have been known to happen.

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

### Post by Robbyx on 2015-04-29
Sadly it is even stranger, because the problem is back again. I have even plugged in a serial keyboard and its number pad does not work in the same way as the usb kb. Does this mean I have to do a reinstall or is it possible to just repair the keyboard control area?

---

### Post by Bashing-om on 2015-04-29
Robbyx; well .........

Not at all good.

In your biois is there a setting/option "IOMMU Controller" ? Set it to "Enabled"  for the keyboard to work .
else:
Try:
```

sudo dpkg-reconfigure keyboard-configuration

```

see if you can re-configure the keyboard. At the least, garner a bit more info .

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]but let's not hold our breath
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by QIII on 2015-04-29
Hello!

Forgive me for an obvious question, but this may be due to a session setting.

What happens when you toggle the NumLock?

---

### Post by Robbyx on 2015-04-30
Having reinstalled this morning I still had the problem. I found the solution here:


Numeric keypad no longer works after upgrade
Bug #197589

In my case it was the mouse keys  option in assistive technologies.

I didn't realise that the keypad was acting as a mouse control as I had not switched that option on within GnomeUbuntu.

R

---

### Post by Bashing-om on 2015-04-30
Robbyx; Hey !

You do good work ...Thanks for providing that solution as it does add to the body of knowledge.

[INDENT][INDENT]all in this together
[/INDENT][/INDENT]

---

