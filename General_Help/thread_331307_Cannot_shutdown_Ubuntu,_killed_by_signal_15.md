---
title: "Cannot shutdown Ubuntu, killed by signal 15?"
date: 2007-01-04
forum: General Help
---

### Post by boast on 2007-01-04
Wehn I tried shutting off my computer, the screen would turn black, and after a while, the hard drive would get killed, but my computer would still stay on.

When I did 'shutdown now' I got "init: rc1 process (5373) killed by signal 15. hang up."

it was working fine a few days ago. ](*,)

---

### Post by boast on 2007-01-04
anybody pls?????

---

### Post by boast on 2007-01-04
?????

---

### Post by boast on 2007-01-07
?????????

---

### Post by koenn on 2007-01-07
just turn it of (with the switch) and start again.

---

### Post by Ramses de Norre on 2007-01-07
The "rc1" part makes me think you were in single mode?
Does it happen every time you use shutdown? And if so: does it happen when you use init 6 to reboot? (or init 0 to halt)

---

### Post by boast on 2007-01-15
it always happens when I try to shutdown.

when I use init8. (well, pressing f8 gets me to the screen where I just have the terminal logged in as root, nothing happening because of the hangup)

---

### Post by boast on 2007-01-16
?

---

### Post by boast on 2007-01-18
:confused:

---

### Post by markitect on 2007-01-18
try 'shutdown -h now' definatly sounds like your going into single user mode, does it do this only when you type in shutdown, or when you use the shutdown option in the menu too?

---

### Post by boast on 2007-01-20
> **markitect said:**
> try 'shutdown -h now'  I't shuts it down, but the power is still running, fans spinning...


> **markitect said:**
> does it do this only when you type in shutdown, or when you use the shutdown option in the menu too?

Using terminal, it kicks me out of gui into terminal as root with the error. 


With gnome, it shuts down like doing 'shutdown -h now' leaving the power still running.

i dont even get the ubuntu shutting down screen, just black.

---

### Post by Ramses de Norre on 2007-01-20
You've got a root session on tty8 by default?? (and that isn't init 8 ;)).
Have you tried running init 0? And how does your entry for ubuntu in grub look?

---

### Post by boast on 2007-01-20
I get 
init: rcS-sulogin process (6387) killed by signal 15
hang up

how do run in init0?

'quiet splash acpi=off' ????

---

### Post by cracker on 2007-01-20
Run the following in a terminal:

sudo telinit 0

---

### Post by boast on 2007-01-27
> **cracker said:**
> Run the following in a terminal:

sudo telinit 0

Only my hard drive and mouse shutdown. Everything else stays on.

---

### Post by boast on 2007-01-28
I don't want to reinstall. :(

---

### Post by Happy_Man on 2007-01-28
I'm having the same problem; any help please?

---

### Post by boast on 2007-01-28
???

---

### Post by boast on 2007-01-29
???

---

### Post by boast on 2007-01-31
???

---

### Post by markitect on 2007-01-31
acpi=off is probably the problem.  Back before acpi you shut down your computer and then it told you when to push the power button.  Im guessing you have it off because of a specific acpi problem, if you no what it is(specify your hardware too) let us know, their might be another workaround that maintains functionality.  also updating kernel might work too, 2.6.18 i believe has some new acpi stuff.

---

### Post by eggdeng on 2007-01-31
Just type

```
sudo halt
```

& you're done. 

Or am I missing something?

---

### Post by jeez on 2007-01-31
Hi,

Same kind of problem here.
Shutdown works fine, except the poweroff part : the computer stays on, displaying the ubuntu splash screen & progress bar.  The 3 LEDs on the keyboard blink once, then the keyboard dies.

According to info I found on several forums, I tried this :
[INDENT].removing "splash quiet" from /boot/grub/menu.lst (defoptions).[/INDENT]
[INDENT].adding "apm=off acpi=force".[/INDENT]
[INDENT].adding "noapic" instead.[/INDENT]
[INDENT].shutting down using "halt" or "shutdown -h".[/INDENT]
[INDENT].finding an alternative dsdt table for my gear, couldn't find one.[/INDENT]


None of it made the slightest difference.
I'm a newb, and quite lost now since I don't understand thoroughly what's involved here.
Any help would be appreciated.

Currently dual-booting xp and ubuntu 6.10 kernel 2.6.17-10-386 (same problem with previous 386 & 686 versions) on Asus p5ad2-e.

---

### Post by jeez on 2007-02-03
Up.

---

### Post by boast on 2007-02-05
:(

---

### Post by boast on 2007-02-10
...... didn't fix itself.

---

### Post by boast on 2007-02-18
ummm.

---

### Post by boast on 2007-02-22
Ttt

---

### Post by boast on 2007-03-25
hmm, has only been 4 weeks.

---

### Post by floke on 2007-03-25
It would have been quicker to do that reinstall you didn't want to do :)

---

### Post by boast on 2007-03-26
meh, I'd rather just wait to press the power button then hours of reconfiguring. :p

---

### Post by boast on 2007-07-11
bump.

---

### Post by confused57 on 2007-07-11
May not work, but you can try this:
```
sudo gedit /etc/modules
```

add a new line with the following statement:

apm power_off=1

---

### Post by RawMustard on 2007-12-01
look here, this worked for me, none of the kernel line stuff did squat for me.

[http://ubuntuforums.org/showthread.php?p=3875896#post3875896](http://ubuntuforums.org/showthread.php?p=3875896#post3875896)

---

