---
title: "Ubuntu 7.10 integrate s2ram ?"
date: 2008-02-18
forum: General Help
---

### Post by samuraiche on 2008-02-18
Hi guys,

it's been a long time since ive been trying to get suspend working on my laptop.And finally i got it working with s2ram.I have an Intel Chipset and my baby goes to sleep after sudo s2ram -f -a3.

Now the question is, how can this command be integrated with my ubuntu.So that if i do System>Quit>Suspend it uses sudo s2ram -f -a3 instead of it's own commands?

I've tried to do some hack in /etc/acpi/sleep.sh but it won't help.

Thanks

---

### Post by plucky on 2008-02-18
I don't know if this would work as I can't test it.

But you can change the **Suspend** command by **System > Administration > Login Window > Edit Commands** Then select **Suspend** and add your command so the suspend button runs your suspend command.


Hope this helps.

---

### Post by samuraiche on 2008-02-19
> **plucky said:**
> I don't know if this would work as I can't test it.

But you can change the **Suspend** command by **System > Administration > Login Window > Edit Commands** Then select **Suspend** and add your command so the suspend button runs your suspend command.


Hope this helps.

No this didn't help,but  thanks anyway

Maybe there are some files I could edit like /etc/acpi/sleep.sh?
May I replace hole sleep.sh with my line of code like s2ram -f -a3?

---

### Post by msully725 on 2008-03-01
Did you try the script at:
/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux

This script contains an if statement with a couple if elses. If you go down to the else, it contains another if statement with a couple if elses. Change the top if to look for s2ram, and then call s2ram.

```

...

#Other distros just need to have *any* tools installed
else
        if [ -x "/sbin/s2ram" ] ; then
            /sbin/s2ram -f -a 1
           RET=$?

...

```

NOTE: Change the arguments for s2ram to what works for your system.

---

