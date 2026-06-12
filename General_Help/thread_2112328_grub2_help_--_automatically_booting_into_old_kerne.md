---
title: "grub2 help -- automatically booting into old kernel?"
date: 2013-02-04
forum: General Help
---

### Post by Dopaque on 2013-02-04
okay so when my grub2 screen pops up I get 4 different options

- Ubuntu
- Advanced options for Ubuntu
- memtest
- another memtest

I want to automatically boot into an older kernel that is contained under "advanced options for ubuntu". However, whenever I change "GRUB_DEFAULT=0" in etc/default/grub, it goes down to one of the memtest options rather than the different kernels...

how can I find out what number to use in order to boot into the right kernel? Do I just keep putting numbers in there until one works?

---

### Post by grahammechanical on 2013-02-04
> how can I find out what number to use in order to boot into the right kernel? Do I just keep putting numbers in there until one works?

That is one way. A lots of us learn through experimentation. You can also see what the developers say.

[http://www.gnu.org/software/grub/manual/]("http://www.gnu.org/software/grub/manual/")

I have downloaded a copy to study.

Regards.

---

### Post by Dopaque on 2013-02-09
well, I put in random numbers up to 6 and nothing seemed to work, so what I did was just uninstall the newer kernel altogether so that grub has no choice but to boot me automatically into the next-newest one.

This is good enough for my purposes; I may need the newer kernel later for testing-things reasons, but for now it's fine to uninstall it. When I need it again later I'll study the manual...

---

### Post by schragge on 2013-02-09
From the GNU GRUB manual:
> 
   Valid keys in `/etc/default/grub' are as follows:

`GRUB_DEFAULT'
     The default menu entry.  This may be a number, in which case it
     identifies the Nth entry in the generated menu counted from zero,
     or the title of a menu entry, or the special string `saved'.
     Using the title may be useful if you want to set a menu entry as
     the default even though there may be a variable number of entries
     before it.

     For example, if you have:

     menuentry 'Example GNU/Linux distribution' --class gnu-linux {
        ...
     }

     then you can make this the default using:

          GRUB_DEFAULT='Example GNU/Linux distribution'

     If you set this to `saved', then the default menu entry will be
     that saved by `GRUB_SAVEDEFAULT', `grub-set-default', or
     `grub-reboot'.

     The default is `0'.

`GRUB_SAVEDEFAULT'
     If this option is set to `true', then, when an entry is selected,
     save it as a new default entry for use by future runs of GRUB.
     This is only useful if `GRUB_DEFAULT=saved'; it is a separate
     option because `GRUB_DEFAULT=saved' is useful without this option,
     in conjunction with `grub-set-default' or `grub-reboot'.  Unset by
     default.  This option relies on the environment block, which may
     not be available in all situations (*note Environment block::).
...


---

### Post by oldfred on 2013-02-10
If grub 1.99 with submenus it is a bit different - drs305
[http://ubuntuforums.org/showthread.php?p=10720316](http://ubuntuforums.org/showthread.php?p=10720316)

change to comment # or delete old and add new :
With grub 1.99 and submenus, like this but title has to be exact. Best to copy & paste from grub.cfg
GRUB_DEFAULT="2>Ubuntu, with Linux 2.6.38-7-generic"
#GRUB_DEFAULT=0

---

