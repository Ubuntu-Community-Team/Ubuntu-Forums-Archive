---
title: "Ctrl+Alt+F1  = Black Screen (No prompt)"
date: 2008-01-27
forum: General Help
---

### Post by cperalta1 on 2008-01-27
When I try to access Command Line via Ctrl+Alt+F1 all I get is a black screen with no prompts for username or password.  I think it's a graphics issue because it feels like the command line in that I can type in things then on backspacing when there's no more characters it beeps.  However, I don't see anything at all.  Then I just switch back to the Graphical Interface (Alt+F7) and everything's fine.

Has anyone experienced this?

P.s.  Thinkpad T40, ATI Radeon Mobility 7500, Gutsy.

---

### Post by bodhi.zazen on 2008-01-27
yea, try just hitting the enter key, see if it gives you a log in prompt.

You can also try Ctrl-Alt-F2

---

### Post by sdowney717 on 2008-01-27
I can ctrl - alt - F2 to a login prompt and login to a command prompt.

How do you get back to X Windows?
if you type startx, x windows is already running.
So far all I can do is pull the plug and reboot.

---

### Post by Raccoon1400 on 2008-01-27
ctrl alt f1-f6 are command consoles. To return to the graphical interface, use ctrl alt f7. 8)

---

### Post by cperalta1 on 2008-01-27
Same thing on all Fs.
Please keep the suggestions coming.

---

### Post by Raccoon1400 on 2008-01-27
what happens when you hit enter when in a console?

---

### Post by cperalta1 on 2008-01-27
> **Raccoon1400 said:**
> what happens when you hit enter when in a console?
Nothing

---

### Post by Raccoon1400 on 2008-01-27
does this let you do commands?
applications>accessories>terminal.

---

### Post by sdowney717 on 2008-01-27
yes.

If I ctrl-alt-F7, I get a black screen with a mouse image and it is locked up.
I assume this is due to the ATI driver.
I dont use the radeon driver.

---

### Post by skymera on 2008-01-27
ok this solved it for me

```
sudo modprobe vga16fb
 sudo modprobe fbcon
 
```

---

### Post by cperalta1 on 2008-01-27
> **Raccoon1400 said:**
> does this let you do commands?
applications>accessories>terminal.
It is as if the screen AND the text were black.  I can carry out commands (blind).  Also, App>Acc>Term works as normal.

[QUOTE=skymera]ok this solved it for me[/QUOTE]
Where you having the same issue?

---

### Post by SanskritFritz on 2008-01-28
Are you using wide screen? Maybe this helps:
[http://ubuntuforums.org/showthread.php?t=622018](http://ubuntuforums.org/showthread.php?t=622018)
I know it is talking about Geforce, but the symptoms you are having are very similar tho that I had, and the solution seems to be universal. It is basically the same what **skymera** also suggests.

---

### Post by cperalta1 on 2008-01-30
SOLVED
I removed the "VGA=792" I added earlier in /boot/grub/menu.lst
Thank you all for trying to help.

---

### Post by Satisfied w/o Micro$oft on 2008-02-09
Thanks [cperalta1]("http://ubuntuforums.org/member.php?u=488799") that worked for me!

---

