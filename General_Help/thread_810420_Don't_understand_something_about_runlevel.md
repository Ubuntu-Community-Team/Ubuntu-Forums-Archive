---
title: "Don't understand something about runlevel"
date: 2008-05-28
forum: General Help
---

### Post by RonInKY on 2008-05-28
here is something that i think that I understand, except for the fact that what I think should happen doesn't happen.  It has to do with runlevels:

I would llike my system to boot into single user mode, immediately execute a program (written in Mono/C#) and then reboot.  The only possible user interaction is with prompts from my program.

I wanted to go the whole route of init scripts, using **update-rc.d** to register the script that would kick off my program.  Where I'm getting stuck is this: when I boot to the 'recovery mode' prompt that is automatically included by GRUB and issue the command **runlevel** it responds with "N S".  Why is that S there?  Shouldn't it be 1?

To make matters more confusing: if I replace "single" on the GRUB line with "1" (thinking this would drop me in runlevel 1, single-user) I end up in the gui!  Is this a single-user GUI?  I thought that single-user=command line interface and multi-user=GUI.  Is this not right?

Thanks for any and ALL help!

---

### Post by pointone on 2008-05-28
S = single user

When you enter "1" on the boot prompt, does "runlevel" show you in runlevel 1/S? If not, try booting with the "RL=1" option instead.

Traditionally I don't think there was any distinction between runlevels 1 and S, but Ubuntu's new init system appears to change that. Runlevel S is strictly intended to be run for "recovery mode". You should not switch into runlevel S from another runlevel--only boot straight into it.

Runlevel 1, on the other hand, is intended for switching from another runlevel into single-user mode. Take a look at the scripts in /etc/rcS.d and /etc/rc1.d to see the difference. Switching into runlevel 1 first kills all services/processes, then switches into runlevel S.

---

### Post by cdenley on 2008-05-28
> **RonInKY said:**
> here is something that i think that I understand, except for the fact that what I think should happen doesn't happen.  It has to do with runlevels:

I would llike my system to boot into single user mode, immediately execute a program (written in Mono/C#) and then reboot.  The only possible user interaction is with prompts from my program.

I wanted to go the whole route of init scripts, using **update-rc.d** to register the script that would kick off my program.  Where I'm getting stuck is this: when I boot to the 'recovery mode' prompt that is automatically included by GRUB and issue the command **runlevel** it responds with "N S".  Why is that S there?  Shouldn't it be 1?

To make matters more confusing: if I replace "single" on the GRUB line with "1" (thinking this would drop me in runlevel 1, single-user) I end up in the gui!  Is this a single-user GUI?  I thought that single-user=command line interface and multi-user=GUI.  Is this not right?

Thanks for any and ALL help!

I don't think you need to do anything special with runlevels. You just need to change a getty to your script. Make the last line of /etc/event.d/tty1 look like
```

exec /path/to/myscript

```
instead of something like
```

exec /sbin/getty 38400 tty1

```

Of course, if you're using ubuntu desktop, you have to disable gdm. I configured POS's to work this way using edgy.

---

