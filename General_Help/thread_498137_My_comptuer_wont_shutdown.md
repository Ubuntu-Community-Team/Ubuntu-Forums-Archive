---
title: "My comptuer wont shutdown"
date: 2007-07-11
forum: General Help
---

### Post by jon.carstens on 2007-07-11
When I select either Restart or Shutdown my desktop closes and I guess it would proceed to a shutdown splash screen, but instead the sound starts to loop a .5 second sample and my monitor turns off but the computer's power remains on [fans and such]. I'm guessing that its a problem with the splash screen because I had a problem starting my computer last week when I installed Ubuntu. When I would try to boot my monitor would turn off when the splash screen was supposed to come up. I solved the problem by removing the "quiet splash" entry from my /boot/grub/menu.lst.

So I assume the problem will be resolved by tweaking my shutdown splash screen, I just don't know how or where to start.

---

### Post by Uncle Spellbinder on 2007-07-11
I had this issue in Breezy, Dapper, Edgy and now Feisty.  Never found a way to fix it.   I just wait until what I think is a long enough time and hold the power button on the computer until it shuts down.

---

### Post by jon.carstens on 2007-07-11
Well that sucks, nobody was able to give you a solution?

---

### Post by Uncle Spellbinder on 2007-07-11
> **jon.carstens said:**
> Well that sucks, nobody was able to give you a solution?

Nope. Quite a few threads exist on this issue on the forums.  They pop up every now and again, and I've yet to see *any* solution.

---

### Post by confused57 on 2007-07-11
> **jon.carstens said:**
> When I select either Restart or Shutdown my desktop closes and I guess it would proceed to a shutdown splash screen, but instead the sound starts to loop a .5 second sample and my monitor turns off but the computer's power remains on [fans and such]. I'm guessing that its a problem with the splash screen because I had a problem starting my computer last week when I installed Ubuntu. When I would try to boot my monitor would turn off when the splash screen was supposed to come up. I solved the problem by removing the "quiet splash" entry from my /boot/grub/menu.lst.

So I assume the problem will be resolved by tweaking my shutdown splash screen, I just don't know how or where to start.
I've seen this method work for some people:
```
sudo gedit /etc/modules
```

add a new line with the following statement:

apm power_off=1

---

### Post by ajgreeny on 2007-07-15
Just to add to the confusion, I have tried all the suggestions shown in the various posting here and other places and I think it may be something to do with the java jre version 6.  I have downgraded this to version 5 as someone found that worked, though I now can't find that reference, and although this forces the removal of ubuntu-restricted-extras metapackage, it still leaves the flash plugin etc so no harm done.

Perhaps worth giving this a try to see if it makes any difference to your system.  If not we can always go back to jre v6 again.

EDIT  OK, it's a day later and there's still no change to the shutdown problem so it seems nothing to do with the version of java, at least, and I can't manage without java so will have to keep searching for the answer.

---

### Post by jon.carstens on 2007-07-17
Nothing I have tried for the last week has helped me at all. I've been searching through threads and linux google to no avail.

---

### Post by mommebu on 2007-07-18
Looks like the kernel option 'reboot=b' might help.
Have a look here:

[http://ubuntuforums.org/showthread.php?p=3038421&posted=1#post3038421](http://ubuntuforums.org/showthread.php?p=3038421&posted=1#post3038421)

---

### Post by jon.carstens on 2007-07-18
That hasn't solved the problem.

To clarify my computer hangs before the shutdown splash screen apears, but after I push the shutdown / restart button.

---

