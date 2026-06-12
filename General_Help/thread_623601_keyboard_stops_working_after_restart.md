---
title: "keyboard stops working after restart"
date: 2007-11-26
forum: General Help
---

### Post by illbashu on 2007-11-26
when ever i restart my computer my keyboard stops working, i have to restart my comp like 50 times to get it to work! i don't want to break my pc, is there a fix for this? :confused: :confused:

---

### Post by illbashu on 2007-11-27
Can someone plz help! i cant restart my comp because ubuntu keeps shuting off the keybourd! someone or anyone?

---

### Post by -grubby on 2007-11-27
have you considered this as a keyboard problem instead of a software problem?

---

### Post by illbashu on 2007-11-27
noo.. this keyboard works all the time on madriva which i switched to, then i dulebooted the comp and put a new copy of ubuntu back onto the comp and its having the same prob....:mad: :(

---

### Post by aashay on 2007-11-27
try adding acpi=off while booting the kernel in grub.

---

### Post by illbashu on 2007-11-27
i dont know how to boot from grub :/ :( how do i add acpi=off

---

### Post by aashay on 2007-11-28
in grub, while booting, highlight Ubuntu, press 'e' . Select the second line and 'e' again. Now add acpi=off to the end of the line. Press enter and finally 'b'

---

### Post by illbashu on 2007-11-29
> **aashay said:**
> in grub, while booting, highlight Ubuntu, press 'e' . Select the second line and 'e' again. Now add acpi=off to the end of the line. Press enter and finally 'b'

how do i get into grub?

---

### Post by -grubby on 2007-11-29
> **illbashu said:**
> how do i get into grub?

it's what shows up when you boot. If you're not dual-booting then press F10(I think) to get to the menu

---

### Post by illbashu on 2007-11-29
> **aashay said:**
> in grub, while booting, highlight Ubuntu, press 'e' . Select the second line and 'e' again. Now add acpi=off to the end of the line. Press enter and finally 'b'

it didn't work..... :(

---

### Post by illbashu on 2007-11-29
can someon plz help me!!!!!!!1:(

---

### Post by illbashu on 2007-12-10
i reformated ubuntu and it still didn't fix my problem! :'( can someone plz help me!

---

### Post by aashay on 2008-01-27
try adding ```
i8042.reset
``` just as you tried acpi=off in the kernel parameters

---

### Post by BuffaloX on 2008-01-27
Enter CMOS and enable legacy keyboard.

Try turning power off (on psu or wall) to your computer for 10-20 seconds.
If the keyboard works after complete power off, the above should do the trick.

---

### Post by illbashu on 2008-01-27
idk how, but it stoped happaning now... thx for your suggestions!

---

### Post by illbashu on 2008-05-24
> **BuffaloX said:**
> Enter CMOS and enable legacy keyboard.

Try turning power off (on psu or wall) to your computer for 10-20 seconds.
If the keyboard works after complete power off, the above should do the trick.
it startecd happening again and this time even restarting 5 times it wont work! how do i do what is in the quote? 

btw i upgraded to hardy and everything was fine and now it started up again :(

---

### Post by nadjavox on 2008-05-25
If it's a usb keyboard, you can try adding usb-handoff in grub.

So turn off your computer then go to the grub menu, then hit e to edit and add "usb-handoff" without the quotes. Then hit b to boot.

---

### Post by illbashu on 2008-05-25
^ its not usb :(

---

### Post by nadjavox on 2008-05-25
> **aashay said:**
> try adding ```
i8042.reset
``` just as you tried acpi=off in the kernel parameters

This is probably what fixed your problem before. The thing is, though, that you have to do it every time you boot or the issue will recur.

If you boot without quiet and splash do you get an error?

i8042 is probably the issue. The error message might be something like this:

i8042.c: Can't read CTR while initializing i8042

Could you post the specific error that you're getting?

---

