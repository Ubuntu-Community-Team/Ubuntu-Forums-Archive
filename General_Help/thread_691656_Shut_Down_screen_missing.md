---
title: "Shut Down screen missing"
date: 2008-02-08
forum: General Help
---

### Post by Bölvaður on 2008-02-08
When I want to shut down the computer I have three ways of doing it:


1. Shut Down Button

When I push it I will no longer be able to click nor give keyboard inputs to the computer, I can still see animation like gifs on my screen moving, but what I cannot see is the Shut Down Menu.


2. Control + Alt + Delete

I will no longer be able to use keyboard or mouse successfully (but the mouse cursor will still move, but clicking will not)


3. Terminal - "shutdown 0"

Text only mode will start and after a bit it shuts down, but I think only if I push Control + Alt + Delete.


What I would like is be able to use number 1 and 2 again :)

---

### Post by archimedes1981 on 2008-02-09
i had a similar problem with mandriva 2008.
it didn't display the shutdown options.
i just turned off any 3d desktops like compiz fusion and the options came back after restart.
also you might try looking up about adding one of the following to the grub menu.lst
acpi=off 
noapic 
nolapic 
apm=power-off
but if your problem is similar to mine these above are another story.

---

### Post by Bölvaður on 2008-02-09
No luck, I had no desktop effects to begin with, so it wasn't a surplice to still having the same problem when I turned them on.
I installed a program called Geyes, which are eyes that follow the cursor around the screen. This program does what it is supposed to do after I push Control + Alt + Delete, and it still only gives me the impression that pushing that or the red shutdown button in the upper right corner will immune my mouse and keyboard to have influence on the computer.

Except that when I move the mouse the Geyes program moves it eyes according to the mouse movements.



(this is what I do not get but am trying to figure out how to show up)
 [IMG]http://www.debianadmin.com/images/rds/7.png[/IMG] 
if I can get this instead of nothing I wouldnt have to use Control + Alt + Backspace and then from the login go to shutdown, then I'd be happy.

---

### Post by happyhamster on 2008-02-09
When you click the red shutdown button, does it help to wait a long time (~ 10 minutes), to see if the shutdown menu appears?

Also, did you perhaps disable the powermanager? (System --> Preferences --> Sessions --> Powermanager.)

---

### Post by Bölvaður on 2008-02-09
> **happyhamster said:**
> When you click the red shutdown button, does it help to wait a long time (~ 10 minutes), to see if the shutdown menu appears?

Also, did you perhaps disable the powermanager? (System --> Preferences --> Sessions --> Powermanager.)

Oh my non existing god, thank you very much :)
I would never have remembered to check if pownermanager was there to begin with. Of course I foolishly disabled it somehow :lolflag:

---

