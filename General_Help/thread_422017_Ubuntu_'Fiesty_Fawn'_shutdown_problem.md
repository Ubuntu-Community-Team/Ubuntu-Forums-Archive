---
title: "Ubuntu 'Fiesty Fawn' shutdown problem"
date: 2007-04-24
forum: General Help
---

### Post by Darko-TheRaven on 2007-04-24
Hello, when i go to shut down my ubuntu installation everything goes fine until the end. In the last steps of shutdown it stops. Normally it should turn off the hard disks and power off, on mine I hear it shut off the hard disks but it never powers off and will continue to sit there until i push+hold the power button to turn it off manually. Any ideas on what might be causing this problem?

---

### Post by strabes on 2007-04-24
does using the command "sudo halt" work?

---

### Post by VileTimes on 2007-04-24
Maybe this will help?

[http://www.understated.co.uk/blog/2004/automatic-shutdown-in-ubuntu/](http://www.understated.co.uk/blog/2004/automatic-shutdown-in-ubuntu/)

---

### Post by Darko-TheRaven on 2007-04-25
In verbose mode i see the message that says this:
```

*Will now halt!
[xxxxx.xxx] System Halted.

```

but it never powers off

---

### Post by Dayylin on 2007-04-27
Shamelessly stolen from the reply of atari130xe  at [http://ubuntuforums.org/showthread.php?t=290713&highlight=shutdown]("http://ubuntuforums.org/showthread.php?t=290713&highlight=shutdown")

This worked for me on Fawn and Eft

---

### Post by Darko-TheRaven on 2007-04-27
I think i figured it out, when booting up this morning i happened to see this message:
```
BIOS Age(1999) 2000: fails cut-off use acpi=force to force acpi.
```

i dunno exactly what it means but i'm sure this has something to do with it. i just dont know where to put acpi=force.

---

### Post by blazercist on 2007-04-27
sudo gedit /etc/boot/grub/menu.lst

add that to the end of the line with the kernel you use, although you probably shouldn't be messing with the grub menu unless you know what you're doing so be careful.

---

### Post by Darko-TheRaven on 2007-04-29
ahahaha, it worked. I manually entered the boot commands:
```

1: root		(hd0,0)
2: kernel		/boot/vmlinuz-2.6.20-15-generic root=... ro quiet splash
3: initrd		/boot/initrd.img-2.6.20-15-generic
4: quiet
5: savedefault

```

but replaced line 2 with the following:
```

kernel		/boot/vmlinuz-2.6.20-15-generic root=... ro quiet splash **acpi=force**

```

and when i shut it down it worked yay :)

and apperently this must be done to all computers whose BIOS dates are before the year 2000

thank yo all for your help.

---

### Post by jerrylamos on 2007-04-29
There's another fix in my posting "Workarounds" in "installation and Upgrades" if anyone needs an alternative.

Cheers, Jerry

---

### Post by sonu27 on 2007-05-06
Any way of fixing this for live cd users?

---

### Post by Darko-TheRaven on 2007-05-07
Push F6 for advanced and add **acpi=force** to the end

---

### Post by 4ndrew on 2007-05-08
> **Darko-TheRaven said:**
> ahahaha, it worked. I manually entered the boot commands:
```

1: root		(hd0,0)
2: kernel		/boot/vmlinuz-2.6.20-15-generic root=... ro quiet splash
3: initrd		/boot/initrd.img-2.6.20-15-generic
4: quiet
5: savedefault

```

but replaced line 2 with the following:
```

kernel		/boot/vmlinuz-2.6.20-15-generic root=... ro quiet splash **acpi=force**

```

and when i shut it down it worked yay :)

and apperently this must be done to all computers whose BIOS dates are before the year 2000

thank yo all for your help.

Do you still get the same error message on boot-up?

I did when I tried the above, although the computer seemed to shut down after adding this in the grub boot kernel....  However when editing the grub program on boot up and pressing "tab" for commands that are valid, acpi is not listed....  So I wonder what the system is doing, and how this works.

Anyone got any ideas?!  Or if this is the correct way to solve it, or using Jerry's Workaround solution (which also works)... Or is it a case of there is not one correct method in Ubuntu/Linux?

Incidentally this is my first post, and my first foray into Ubuntu - quite proud so far, and love the simplicity of the interface, and the fact that my creaking 7 yo computer can still run it!

---

### Post by sonu27 on 2007-06-15
Thanks, I will try that.

Peace

---

