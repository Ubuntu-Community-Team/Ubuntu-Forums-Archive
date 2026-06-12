---
title: "Computer will not boot after apt-get upgrade (or apt full-upgrade), etc."
date: 2015-08-07
forum: General Help
---

### Post by raequin on 2015-08-07
**Update:** The computer will boot with an old kernel version (3.13.0-35).  Versions 36 and 37 do not work, though.  (Nor does 61 as seen below.)  So what now, try to fix the problems using the working kernel version or just use that one and don't worry about it?


----- Original thread follows -----


Today I made several changes to my system using apt-get.  After restarting the computer it now won't boot into Ubuntu (have not tried Windows).  I will write the information I'm able to see, but first let me write what I can remember of the commands I issued.

[LIST]
[*]Added PPA for playonlinux
[*]sudo apt-get update
[*]sudo apt-get -f install
[*]sudo apt-get upgrade (this took a fair amount of time)
[*]sudo apt full-upgrade
[*]sudo apt-get autoremove
[*]sudo apt-get install playonlinux (the Windows application did not install so then)
[*]sudo apt-get purge playonlinux
[*]sudo apt-get purge wine
[*]Added PPA for openshot
[*]sudo apt-get update
[*]sudo apt-get install openshot
[/LIST]

Only then did I notice a restart was required to complete the upgrades or whatever so I restarted and ... Here's what my laptop now shows at start (I might not be able to see all of it, don't know how to scroll up).  This is not verbatim because I don't want to type it all.  I left out some numbers but kept all the english.
```

wn-block(0,0)
[ 1.234500] CPU: 3 PID: 1 Comm: swapper/0 Not tainted 3.13.0-61-generic #100-Ubuntu
[ 1.234523] Hardware name: LENOVO 2392APU/2392APU, BIOS G4ET93WW (2.53 ) 02/22/2013
[ 1.234550] 0000000000008001 ffff880212c03df0 ... two more groups of hex
[ 1.234631] bunch of hex
[ 1.234714] bunch of hex
[ 1.234795] Call Trace:
I'm going to stop copying the numbers in brackets (NIB)
NIB [<ffffffff81723700>] dump_stack+0x45/0x56
NIB [<hex numbers>] panic+0xc8/0x1d7
NIB hex ? printk+0x67/0x69
NIB hex mount_block_root+0x255/0x2b0
NIB hex mount_root+0x53/0x56
NIB hex prepare_namespace+0x16c/0x1a4
NIB hex kernel_init_freeable+0x1f3/0x200
NIB hex ? do_early_param+0x88/0x88
NIB hex ? rest_init+0x80/0x80
NIB hex kernel_init+0xe/0x130
NIB hex ret_from_fork+0x58/0x90
NIB hex ? rest_init+0x80/0x80

```

---

### Post by monkeybrain20122 on 2015-08-07
What does "sudo apt-get full-upgrade" do and why "sudo apt-get -f install (what)"???  Not sure what your problem is but you seem to be running a bunch of apt-get commands randomly.

---

### Post by raequin on 2015-08-07
```
sudo apt full-upgrade
```
Upgrades all installed packages except add the "smart upgrade" checkbox. It tells APT to use "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary.

```
sudo apt-get -f install
```
"This command does the same thing as Edit->Fix Broken Packages in Synaptic. Do this if you get complaints about packages with 'unmet dependencies'."

The commands were issued haphazardly, but not randomly.

Oh, I do hope someone can help.

---

