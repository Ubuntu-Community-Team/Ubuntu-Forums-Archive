---
title: "Grub2"
date: 2015-12-08
forum: General Help
---

### Post by Darth4212 on 2015-12-08
Is it possible to remove GRUB2 since I am no longer diual-booting with Ubuntu and Windows? I am now only booting Ubuntu and I would like to skip having to use grub it is just an annoyance.

---

### Post by grahammechanical on 2015-12-08
Overwriting Grub with another boot loader will certainly remove it. Ubuntu needs a boot loader and Grub 2 is the default software to load Ubuntu. So, I do not advise removing Grub.

If Ubuntu is now the only OS on the machine and there is only one hard disk (sda) then load into Ubuntu and run this command

```
sudo update-grub
```

That should remove any entries for Windows in the boot loader menu. If you have done that and are still seeing a boot menu then edit /usr/share/grub/default/grub and change

> GRUB_TIMEOUT=10

to

> GRUB_TIMEOUT=1

or even

> GRUB_TIMEOUT=0

And then run

```
sudo update-grub
```
 
This is what the Grub 2 manual says

> ‘GRUB_TIMEOUT’

Boot the default entry this many seconds after the menu is displayed, unless a key is pressed. The default is ‘5’. Set to ‘0’ to boot immediately without displaying the menu, or to ‘-1’ to wait indefinitely.


Regards.

---

### Post by Bucky Ball on 2015-12-08
Not sure about /usr/share/grub/default/grub, that may work exactly the same way, but generally you edit /etc/default/grub followed by 'sudo update-grub'. :)

Once you have made the grub_timeout change (set it to zero if you don't want to see it at all and no delay), if you do need to get to the grub at any time in future, I think it's shift key after boot and that should bring it up. Or tweak the setting in /etc/default/grub to 10 again and reboot. Otherwise, you won't see grub, but, as mentioned, you need it to boot Ubuntu.

---

### Post by Darth4212 on 2015-12-10
How do I edit those? I'm sorry if I sound stupid I am not really that new but I am really still confused.

---

### Post by pfeiffep on 2015-12-10
Copy the line below into a terminal (accessed via ctrl-alt-t simultaneously)
```
sudo gedit /etc/default/grub
```
[INDENT]portions of the code explained
[/INDENT]
[INDENT=2]sudo - opens the command with the privelege necessary to chand the file
gedit - a text editor
/etc/default/grub - file name to be changed
[/INDENT]

As pointed out you need a boot program and it's probably easiest to just change the timeout to zero so you don't notice. If at some time in the future you need to access grub holding the shift key down while booting should then display the grub menu

---

### Post by Darth4212 on 2015-12-10
I changed the timeout to 0 but I still see it what do I do?

---

### Post by pfeiffep on 2015-12-10
As explained in a previous answer you need to have the changes applied by running this line of code
```
sudo update-grub
```
Assuming the file opened and was effectively changed the above line of code will make the grub menu not appear

---

### Post by Bucky Ball on 2015-12-10
Did you close and save the file correctly then run:

> sudo update-grub

???

You hit control+x to close/save the file, press 'y' to confirm then enter. Run the above command once you're back at the terminal. Reboot.

* Ninja-ed by pfeiffep! Yea, what they said. :)

---

### Post by Darth4212 on 2015-12-11
What are some other boot loaders?

I followed the instructions exactly but I still see it.

---

### Post by pfeiffep on 2015-12-11
Perhaps posting the contents of your /etc/default/grub (use code tag please) will help others aid you ... I'm beyond my depths especially about other boot loaders.

---

### Post by Darth4212 on 2015-12-22
I did I ran the update commands and pressed control+x but I still see it excuse my language but it is greatly pissing me off

---

