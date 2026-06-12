---
title: "can't get into my BIOS"
date: 2007-10-13
forum: General Help
---

### Post by amithaba on 2007-10-13
Hi 
I'm quit new to Ubuntu, and not that good with computers,
I have an acer aspire 9100 (if that matters) and I wanted to go into my bios, but I can't.
I have Ubuntu Feisty fawn now. Wenever I normally rebooted the Acer screen commes up, and tells me that if I push F2 I'd go into Bios or something (the place where you can change the boot-options....)
But now there's no instruction left, and if I push F2 the screen stays like it is for as long as I keep pushing the button, but there seems to be no way to get into my bios.

I seem to remember that I did something in the startup of Ubuntu

you guys have any idea's?
thanx allready

---

### Post by Pumalite on 2007-10-13
Your computer would not function without BIOS, so is in there, hiding someplace. Try other keys: Esc. Del, F12, etc

---

### Post by PmDematagoda on 2007-10-13
An issue with the BIOS cannot be linked to any OS as the BIOS is in charge of only the I/O, core and peripheral devices and not of the OS. In any case it should be a hardware issue that is causing the BIOS malfunction, but if the BIOS does not function, how can you get to the OS at all, or can't you access the OS?

---

### Post by Daveth on 2007-10-13
the most common bios entry keystrokes seem to be the delete key or the spacebar- you need to do it just as the PC is powering up, and keep on tapping one or the other.  As PmDematagoda notes this is at a very basic operation level, hence the need to get in early.

---

### Post by amithaba on 2007-10-13
my bios does work, and I'm sure of that, I just can't get into my Bios

But whenn I wait a bit longer (if I've pressed esc) is redirects me to a page that gives me the possibility to go in recovery mode.
Besides that it gives me the ability to edit the boot order (e) make a new boot line, edit an existing one, etc...
and to go in a terminal ( to type commands and stuff)

Is it possible that I have to make a new boot line? but how would I have to call it??
==> I really dont know alot about this stuff.
thanks verry much

---

### Post by coffeecat on 2007-10-13
> **amithaba said:**
> my bios does work, and I'm sure of that, I just can't get into my Bios

I'm sure of that too. As others have said, if your BIOS wasn't working, you wouldn't get anything at all. :wink:

> **amithaba said:**
> But whenn I wait a bit longer (if I've pressed esc) is redirects me to somme Ubuntu page wich gives me the possibility to go in revery mode.
Besides that it gives me the ability to edit the boot options (e)
and to go in a terminal ( to type commands and stuff)

What you're describing is the GRUB menu which appears **after** the BIOS has done it's stuff. A word of explanation - Grub is a boot manager quite independent of the operating system. It's not part of Linux at all - just the most usual choice of boot manager for Linux. When you see the grub menu, the bios has already passed control of the machine to grub. Once you choose an option, then grub hands over control to the Linux kernel and the bootup sequence starts.

From what you say, it's obvious that esc does not take you to your bios screen. I should imagine that for whatever reason, the bios is no longer showing the splash screen or scrolling text, or whatever it was that it used to, but it is still working. Try some of the other keys that other posters have suggested. The BIOS on my machines responds to the del key. Try that. **Don't** tap the key repeatedly - I don't think that works. Choose a key and hold it down as soon as you switch on and certainly before the grub screen appears.

Good luck.

---

### Post by amithaba on 2007-10-13
Thanks!, I'll post later to tell how it worked out

---

### Post by ronmarley1 on 2007-10-13
I just a quick search for Acer BIOS and it gave three suggestions:
F1, F2, CTRL+ALT+ESC

---

### Post by amithaba on 2007-10-14
there seems to be no key that works :s

---

### Post by runemaste644 on 2007-10-14
If your internal battery went dry, you would be redirected to the BIOS to set it. 
Making it run dry on purpose would be stupid though...

---

### Post by PmDematagoda on 2007-10-14
Did you press F2 about 3-6 seconds after the computer starts up?

And do not keep pressing it, just one press will suffice.

---

### Post by amithaba on 2007-10-14
seems like an interessting idea....
how could I do that?

---

### Post by PmDematagoda on 2007-10-14
Ok, now when you just start up your computer, wait for about 3 seconds, and then press the key that usually brings up the BIOS menu(In your case it is Alt+F2), do not press it more than once, once will be enough.

---

### Post by amithaba on 2007-10-15
no sorry guys, none of your tips seem to work

---

