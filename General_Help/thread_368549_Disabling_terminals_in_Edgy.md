---
title: "Disabling terminals in Edgy?"
date: 2007-02-23
forum: General Help
---

### Post by pointone on 2007-02-23
I want to disable all but one virtual terminal in Ubuntu 6.10, but am unsure how to accomplish this with the new init system. I renamed all the "ttyX" files in the event.d directory to "ttyX--disabled" (except for tty1, of course), but am still able to use these terminals. What should I be doing here?

Thanks in advance!

---

### Post by dannyboy79 on 2007-02-23
the file you want to edit is your /etc/inittab file. this is what I have done to mine
go down until you find this section. This way init won't launch these for use.
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
#2:23:respawn:/sbin/getty 38400 tty2
#3:23:respawn:/sbin/getty 38400 tty3
#4:23:respawn:/sbin/getty 38400 tty4
#5:23:respawn:/sbin/getty 38400 tty5
#6:23:respawn:/sbin/getty 38400 tty6


I think there is another location you can disable them as well but I forget where. AS you can see I only left 1 other 1 as I never use this feature of switching consoles or terminals.

---

### Post by dannyboy79 on 2007-02-23
here's a great post about how to speed up ubuntu's boot speed as well as free up a lot of resources by stopping things that load by default that you may not even need. [http://doc.gwos.org/index.php/Speed_up_boot](http://doc.gwos.org/index.php/Speed_up_boot)

---

### Post by Nythain on 2007-02-23
ok, you obviously arent catchign on the fact that we in edgy dont have an /etc/inittab... they broke it up into different sections... each tty gets its own file, and there's another main file i cant remember the name of... i to was wondering how to disable half my consoles in edgy, but never could find a helpfull response so i figured id just let sleeping processes lie

---

### Post by gwpritch on 2007-02-23
renaming ttyX in the /etc/event.d directory should do the job for you. Did you reboot after you made the changes?

---

### Post by pointone on 2007-02-23
Indeed, as Nythian says, inittab no longer exists in Edgy Eft. However, I can't really ignore this problem; I'm setting up the system to be used as a public Internet kiosk, and want to disable these unneeded terminals for both security and performance issues.

* Edit * -- gwpritch posted at the same time as me.

I did restart the computer after making the changes, but am still able to view the supposedly disabled terminals with the Control-Alt-FX key combination.

---

### Post by sloggerkhan on 2007-02-23
I renamed mine and ctrl-alt-f key brings up a screen, but it is just a blinking cursor and no input or anything is accepted. (I also deleted the tty4~ file that was created by $sudo mv tty4 disabled.tty4)

I guess if you want it to not switch to a "screen" it is a different question than disabling the tty?

---

### Post by pointone on 2007-02-23
No--what you described is what I want. When I press Control-Alt-FX, I still get a screen with the login prompt. Perhaps I should rename the files to something completely different... I think it may still be finding them with the name I chose.

* Edit *

Turns out that's all it was... I renamed the files to "disabled.ttyX" and it behaves just as sloggerkhan describes. Strange that it would still find "ttyX--disabled", it must only look at the beginning of file names, perhaps?

Now, on a similar topic, but slightly less urgent: is it possible to disable the Control-Alt-FX key combination entirely (i.e., so nothing would happen at all)?

---

### Post by dannyboy79 on 2007-02-23
couldn't you disable the ctl-alt-fnX key by modifying the keymapping? or is it xmodmap or something like that, I forget. yeah, I didn't know they changed this on edgy.

---

### Post by Nythain on 2007-02-23
ok, so im totally sorry for sounding rude... its just i searched for weeks for an answer to that question and all i got was comment out the inittab... one reference i found to renaming and or deleting the files... but it didnt say how safe either ways or if it was the correct way...

i actually tried the rename to, with no success but my files were named similarly to the other poster... thanks for the more info on completely changing the name... totally helpfull

once again, sorry for being rude with that one... its usually not me

---

### Post by kerry_s on 2007-02-24
I just went in to tty3->tty6 and commented out both the start lines. See pic->

---

