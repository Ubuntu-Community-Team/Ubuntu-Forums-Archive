---
title: "No keyboard no mouse"
date: 2007-04-21
forum: General Help
---

### Post by urdrwho on 2007-04-21
When I try the live CD it will not recgonize the keyboard or mouse.  I am trying it on an older desktop (1999).  There is a message at startup about bios and the year 2000 and that it will be using something like ACPI?

Anyhow I've  re-burned the CD, I've tried several times but it isn't working for me.  :(  

I really wanted to get to play with open source.  Maybe this is what all the detractors mean when they say open source isn't ready for prime time.

---

### Post by Compyx on 2007-04-21
Since the BIOS is a pre-2000 one, I think ACPI will be disabled. You can force ACPI by using kernel-parameters, check the info the function keys (something like F3 or F4) give you. I don't have a Live-CD handy right now so I can't check.
You'll probably have to enter something like 'linux acpi=force'.

---

### Post by catalytic on 2007-04-21
I am having similar problem, I managed to get it to install using the just the keyboard. But now I find it doesn't want to register mouse clicks, it sort of randomly selects when the mouse wants to work. The keyboard now appears to be fine. 

I have a gigabyte motherboard, one of those all in ones. Not sure what exactly to do, anyone got any ideas?

EDIT: Ok a little more info, I just went to install updates, and I got an error message that went something like this

"Could not grab your mouse!
A malicious introuder could be eavesdropping on your conversations....or or an application could be trying to get focus....

---

### Post by urdrwho on 2007-04-21
Babeldisk will load, launch and find my mouse and keyboard.  From what I read babeldisk is a ubunto distro except there is a $ charge.

> **Compyx said:**
> Since the BIOS is a pre-2000 one, I think ACPI will be disabled. You can force ACPI by using kernel-parameters, check the info the function keys (something like F3 or F4) give you. I don't have a Live-CD handy right now so I can't check.
You'll probably have to enter something like 'linux acpi=force'.

---

