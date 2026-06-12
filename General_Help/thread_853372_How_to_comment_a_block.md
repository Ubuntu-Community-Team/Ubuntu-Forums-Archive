---
title: "How to comment a block?"
date: 2008-07-08
forum: General Help
---

### Post by I_can_see_the_light on 2008-07-08
This is related to a solution to [[COLOR="Red"]my problems[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5307093#post5307093") in [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=805570")

It was suggested that I tried the workaround in the Ubuntu Wiki, [https://wiki.ubuntu.com/PowerManagement]("https://wiki.ubuntu.com/PowerManagement")

But when I came to *'Comment the four $HDPARM blocks in /etc/acpi/power.sh'* I got stuck. How do I comment a whole block? Just put # in front of every line?

Like this?```

    #for x in /sys/bus/ide/devices/*/block*; do 
	#drive=$(basename $(readlink $x));
	#$HDPARM -S $SPINDOWN_TIME /dev/$drive 2>/dev/null
	#$HDPARM -B 1 /dev/$drive 2>/dev/null
    #done
```

Or do I just comment the lines between *for* and *done*?

Grateful for any help

---

### Post by apmcd47 on 2008-07-08
How you have done it is correct. From a personal point of view I would have put the #s at the beginning of the lines, not against the statements, but that is fine.

---

### Post by I_can_see_the_light on 2008-07-09
Ok, thanks.

The workaround in the Ubuntu Wiki seem to have solved my problems. All well now.

---

