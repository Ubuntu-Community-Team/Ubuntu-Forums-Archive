---
title: "Dual Boot"
date: 2005-10-30
forum: General Help
---

### Post by Drifter on 2005-10-30
How do I dual boot with windows xp, having xp as the first boot listed on the boot order.  I have two seperate harddrives.  Any help please

---

### Post by aysiu on 2005-10-30
1. Put the Ubuntu installer CD in and boot from it.
2. Answer the standard questions.
3. Choose to install Ubuntu on your second hard drive (it may be called /dev/hdb1)
4. When asked if you want to install Grub to the MBR, say "yes."

After that works, then we'll worry about making Windows the default.

---

### Post by Drifter on 2005-10-31
I now have done what you said to do and have grub loaded, how can I change the default to xp for first choice.

---

### Post by aysiu on 2005-10-31
Okay. Let's assume, for the sake of these instructions, that Windows is the fourth item down on the Grub list. You obviously would know better which item it is.

In Ubuntu, open up a terminal and type this in ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo nano /boot/grub/menu.lst
``` Then, change *default 0* to be *default 3*. Then, Control-X (to save), y (to confirm the save), Enter (to exit nano).

That's it. If Windows is the fifth item, default should be 4, and so on.

---

### Post by Drifter on 2005-10-31
[QUOTE=aysiu]Okay. Let's assume, for the sake of these instructions, that Windows is the fourth item down on the Grub list. You obviously would know better which item it is.

In Ubuntu, open up a terminal and type this in ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo nano /boot/grub/menu.lst
``` Then, change *default 0* to be *default 3*. Then, Control-X (to save), y (to confirm the save), Enter (to exit nano).

That's it. If Windows is the fifth item, default should be 4, and so on.[/QUOTE]

Thanks I will give it a try, let u know.

---

### Post by Drifter on 2005-10-31
I tried the terminal, I am very new to linux it did not open to where I could change the default from 0 to 4 how do I type in the sudo etc.

---

### Post by aysiu on 2005-10-31
Go to Programs > Accessories > Terminal
That's where you type commands in. Actually, you don't even have to type them. You can just copy and paste what I put in.

---

### Post by Xian on 2005-10-31
Just copy/paste this command into the terminal.
It may be easier for you to use a GUI text editor.

```
$ sudo gedit /boot/grub/menu.lst
```

---

### Post by Drifter on 2005-10-31
I got it changed ok by copy paste it now boots xp first, however the xp order is still at the bottom is that the way it should be.  It goes there 1st and boots ok.  If you can tell me why I could not type in the command at the terminal it said something like no such file found.  Thanks for the info

---

### Post by aysiu on 2005-10-31
What happened when you tried to type it in the terminal as opposed to copying and pasting?

---

### Post by Drifter on 2005-10-31
[QUOTE=aysiu]What happened when you tried to type it in the terminal as opposed to copying and pasting?[/QUOTE]

It said something like file not found or bad command etc.

---

### Post by Drifter on 2005-10-31
[QUOTE=Drifter]It said something like file not found or bad command etc. [/QUOTE] I could not get the second line do drop down it would ask for password or say file not found.

---

### Post by aysiu on 2005-10-31
Any time you use *sudo* it's going to ask you for a password.
Usually when it says "command not found" it means you've typed it wrong--that's been my experience. I've had to become a good typist to do command-line stuff...

---

### Post by Drifter on 2005-10-31
[QUOTE=aysiu]Any time you use *sudo* it's going to ask you for a password.
Usually when it says "command not found" it means you've typed it wrong--that's been my experience. I've had to become a good typist to do command-line stuff...[/QUOTE]
Aysiu, thanks for all the help on the dual boot, I now have it the way I wanted it for the time being.  I will try my best to use windows less and less as time goes by.  I really love breezy badger but I need to know the commands better before I really get into it.

---

### Post by Halbert on 2005-11-01
[QUOTE=aysiu]Okay. Let's assume, for the sake of these instructions, that Windows is the fourth item down on the Grub list. You obviously would know better which item it is.

In Ubuntu, open up a terminal and type this in ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo nano /boot/grub/menu.lst
``` Then, change *default 0* to be *default 3*. Then, Control-X (to save), y (to confirm the save), Enter (to exit nano).

That's it. If Windows is the fifth item, default should be 4, and so on.[/QUOTE]
Hi, I have the same prob as Drifter.  This is as far as I got - no sign of the next lines for me to change default. I tried using text editor but just created a couple of files in the grub folder.
From the beginning then...
I open a Terminal window, then paste the code, hit enter? Then the next lines should appear for me to change? Or did I miss something?

---

### Post by RAOF on 2005-11-01
You should open a terminal window, paste the first line of code, and press enter.  It should ask for your password.  Type it in.

Now, paste the second line of code and press enter.  It shouldn't ask for a password this time (because you're recently typed it in).

Now you can do the editing.

---

### Post by Halbert on 2005-11-01
Hi RAOF,

Thanks for the advice. 

I got to a screen headed GNU nano 1.3.8  file: /boot/grub/menu.1st  modified.

No mention of defaults only the ctrl stuff at the bottom to play with.

Any suggestions?

---

### Post by hesee on 2005-11-01
[QUOTE=Halbert]Hi RAOF,

Thanks for the advice. 

I got to a screen headed GNU nano 1.3.8  file: /boot/grub/menu.1st  modified.

No mention of defaults only the ctrl stuff at the bottom to play with.

Any suggestions?[/QUOTE]

File is: /boot/grub/menu.lst, NOT /boot/grub/menu.1st. :)

---

### Post by Halbert on 2005-11-01
Har har har, so it is, he said wiping the finger prints off the screen.  I need new glasses (or fewer)
Thanks for all your help.:cool:

---

