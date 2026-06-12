---
title: "[SOLVED] Insane Loading time :("
date: 2008-01-31
forum: General Help
---

### Post by on4c1d on 2008-01-31
Hi there
This problem has been posted before in Absolute begginers talk but I didnt manage to solve it.
I installed ubuntu for the first time like 2 months ago. This is also my first attempt to use any linux release.
Everything worked perfect till yesterday. For some reason Ubuntu takes ages to load after i choose which operating system to use in grub. I tried ctrl+alt+f1 and notice it stops at "Loading... Please wait..." message for 3-4 minutes. At that time i notice full disk activity (at least the hdd led is on). After that pause, everything seems to load normally.
I have to mention i can se the loading bar, so i guess it's not a usplash.conf broblem.
I can definately re-install since there is nothing i am gonna lose if i format the disk but i would prefer to take my chances in working around this problem
I can't remember of doing installing anything or changing some option before the problem occured

Any ideas ?
Thanx alot

---

### Post by Fraktyl on 2008-01-31
The big problem is by default, Ubuntu makes the loading of the kernel silent.

You have two choices.  You can edit the /boot/grub/menu.lst file and remove the quiet option so you can always see what's going on.  Or you can modify it on the fly.  Without knowing where it's hanging, there's nothing we can do to help.

So, here's how to do both...

First way is to do it on the fly.  When you boot, you'll come to the grub menu.  Move the cursor to your boot option.  Then hit 'e'.  This will pop up with another menu.  Highlight the line that says something like the following:

```

kernel         /boot/vmlinuz-2.6.22-14-generic root=UUID=db16284b-baa7-4817-8951-a0c3f7e80e18 ro quiet splash

```Your display may look different.  The main key is to make sure you select the "kernel" line.  Hit 'e' again.

Remove the words quiet and splash.  Hit enter.  Then hit 'b' to boot.

Watch everything you've been missing before.  Take note of where it hangs.  This is what we need to know to help you.  Post back if you need help.

edit:
I know I said, two ways.  It's easier and less intrusive to do it this way.  If you want help modifying the menu.lst file so it'll always do this, feel free to ask.  The way I posted won't be permanent, which means once you fix your problem you never have to look at the boot sequence unless you want to.

---

### Post by forestpixie on 2008-01-31
try booting in recovery mode - you won't get a gui but it should let you see what it is that is holding the boot up

---

### Post by Fraktyl on 2008-01-31
The only problem with booting in Recovery is it won't run all the init scripts.  It may be an init script that's hanging the system.  Lack of DNS, Missing config file, etc.

I'm still learning Ubuntu's nuances, so I may be completely off base though.  If I am, please let me know, I'd hate to be passing on bad information to people.

---

### Post by forestpixie on 2008-01-31
nop you're right I think - :)

---

### Post by flamelab on 2008-01-31
Remove 

```
ro quiet splash 
```

from menu.lst

---

### Post by Fraktyl on 2008-01-31
Won't removing the RO from the kernel options throw up even more problems?

I wouldn't even think of trying to load the kernel off of a r/w partition.  So, if you want to edit your menu.lst file.  Just remove the "quiet splash"

---

### Post by on4c1d on 2008-01-31
ok i removed the quiet option and booted :)
there is no specific line when the system hangs.
there are many lines where it stops for 3 or 4 seconds like:
.attached scsi generic sg0 type0
.hdb: dma_timer_expiry: dma status == 0x61
.ide0: reset: success

the dma timer expiry message comes up many times

is there a way to keep a log file of the whole boot procedure ? too many lines to manage to write em down in time :(

---

### Post by on4c1d on 2008-02-07
Ok, problem solved :)
Insanely stupid of me but the ide cable was not fully plugged into the mobo causing the disk to be semi-operational. Strange though, i always thought that in that case the hd would not work at all :P

---

