---
title: "terminal flashing box gone"
date: 2021-06-13
forum: General Help
---

### Post by ijr9005 on 2021-06-13
the flashing white box is missing from the terminal so i cant enter any commands,have a usb issue that i cant address till this is working.thanks for all help

---

### Post by corradoventu on 2021-06-13
Ubuntu? Xubuntu? Lubuntu? ... Version?

---

### Post by ijr9005 on 2021-06-13
ubuntu 20.10,been using for 6 months, it was there when i first started with linux

---

### Post by Impavidus on 2021-06-13
That box (a cursor) is bright red and not flashing on my box, but I get what you mean. Maybe there's a problem starting your shell, but even then, I expect a cursor, just no prompt, which has the same effect. Other than that, it could be a problem with the colour settings of your terminal, making the cursor (and maybe the text as well) invisible.

Have you tried typing commands anyway? Can you get any output? Do you get a scrollbar when enough output should have been generated? Do you see a prompt? Have you tried a different terminal application?

Can you use ctrl+alt+F3 or so to get to the text interface, login and do things there? There's a number of interfaces available on F1-F7, one of them should be the GUI, the others text, but different versions and flavours put the GUI on different numbers. On mine it's F7, but could be different on your box. Just try.

---

### Post by ijr9005 on 2021-06-16
yes checked colours,tried entering commandsall over screen, have got to text interfacee, thankyou,is thiss the terminal as well?

---

### Post by deadflowr on 2021-06-16
Perhaps it's an odd wayland display server issue.
Try logging out, and at the log in screen after you select your user, look down into the bottom right corner of the screen and click on the icon the shows.
This is the session selection menu.
Ubuntu's default option on [s]21.10[/s] 20.10 is wayland, a secondary option should show as Ubuntu on Xorg.
Select the Ubuntu on Xorg option then try entering your password to log in.
See if that helps.
> have got to text interfacee, thankyou,is thiss the terminal as well?
Without a better description I have no clue. What do they look like?

Edit: Sorry, I confuse 20.10 with 21.04.
I forget if wayland is the default on 20.10 or not.
But try switching sessions anyway. Can't hurt.
If it fails you can switch them back again.

Double Edit: You should really consider upgrading to a newer release, as 20.10 will be end of life soon.

---

### Post by ajgreeny on 2021-06-16
But this is 20.10, not 21.10 so wayland was not, I think, the default display manager for that version.
However, it's worth double-checking what you're really using.

Have you made any changes to your hidden ~/.bashrc file that might affect the behaviour of the terminal?

---

### Post by deadflowr on 2021-06-16
> But this is 20.10, not 21.10 
Yeah, I realized that as soon as I hit Post reply.

---

### Post by ActionParsnip on 2021-06-17
If you log in as guest is it the same?

---

