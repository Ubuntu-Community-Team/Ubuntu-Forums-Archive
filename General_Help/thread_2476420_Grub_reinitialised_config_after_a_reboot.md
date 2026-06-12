---
title: "Grub reinitialised config after a reboot"
date: 2022-06-25
forum: General Help
---

### Post by a2-koray on 2022-06-25
I've got custom kernel parameters that I want to be passed on by grub.

Last time the system updated I've remarked that the parameters have been changed back to default, so I've updated the parameters in `/etc/default/grub` and run `sudo update-grub` & rebooted. I could check and see that my custom parameters have been passed (I'm also removing the splash screen so that's pretty clear that the config has been updated).

But then if I reboot again the config is back to the default config, the custom parameters have been removed. I've been trying to search for this but I only get results about the standard procedure (what I've just described).

Is this a new feature of grub that you can reset the parameters automatically? How I can make sure that my custom parameters are not erased?

Note: there is only Ubuntu installed on my computer.

---

### Post by #&amp;thj^% on 2022-06-25
How are you editing grub, can you show us that command?

---

### Post by a2-koray on 2022-06-25
after having edited /etc/default/grub i just run

update-grub

---

### Post by #&amp;thj^% on 2022-06-25
Ok maybe I wasn't clear>>> what edit command did you run EG
```
sudo nano /etc/default/grub
sudo -H gedit /etc/default/grub
vi /etc/default/grub
```
or different,

---

### Post by a2-koray on 2022-06-26
First time I think i used nano (1st one) but other times:
```

sudo gedit /etc/default/grub

```
does it matter?

For information the output of update-grub
```

$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-40-generic
Found initrd image: /boot/initrd.img-5.15.0-40-generic
Found linux image: /boot/vmlinuz-5.15.0-39-generic
Found initrd image: /boot/initrd.img-5.15.0-39-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done

```

---

### Post by Impavidus on 2022-06-26
What 1fallen is hinting at, is that there are multiple ways to edit root-owned files and not all methods listen on the web work (reliably). The best way is to use the sudoedit command, which will copy the file to some temporary location, start your favourite text editor to edit the file, wait for the text editor to terminate and copy the edited file back. By default it uses nano, but it can be configured to use other text editors.```
sudoedit /etc/default/grub
```

But your observation that it worked the first time after editing /etc/default/grub and running update-grub indicates that you successfully changed /etc/default/grub. Something changed it back.

What does your /etc/default/grub look like exactly? Do you use any tools that may affect grub configuration, like grub-customizer? Could there be interference from some backup routine?

---

### Post by a2-koray on 2022-06-26
The content I try to set:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=10
#GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="i8042.reset i8042.nomux i8042.nopnp i8042.noloop rcutree.rcu_idle_gp_delay=1 acpi_osi=! acpi_osi='Linux'"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
I don't I use anything that may affect grub configuration (as far as I know). "apt info grub-customizer" says the package is not found (so i guess not installed). No backup routine I know of. I've checked the journal there seems to be some errors with some (manufacturer specific/bespoke) package but not sure it's related. I'm going to try to solve this first see if this would solve the grub issue.

---

### Post by grahammechanical on 2022-06-26
I want to understand what you have done. You have added this line to /etc/default/grub

> GRUB_CMDLINE_LINUX_DEFAULT="i8042.reset i8042.nomux i8042.nopnp i8042.noloop rcutree.rcu_idle_gp_delay=1 acpi_osi=! acpi_osi='Linux'"

Should it not be added to GRUB_CMDLINE_LINUX=   " "  ?

I quote the Grub2 manual

> ‘GRUB_CMDLINE_LINUX’Command-line arguments to add to menu entries for the Linux kernel. 

 ‘GRUB_CMDLINE_LINUX_DEFAULT’
Unless ‘GRUB_DISABLE_RECOVERY’ is set to ‘true’, two menu entries will be generated for each Linux kernel: one default entry and one entry for recovery mode.  This option lists command-line arguments to add only to the default menu entry, after those listed in ‘GRUB_CMDLINE_LINUX’.


[https://www.gnu.org/software/grub/manual/grub/grub.html#Simple-configuration](https://www.gnu.org/software/grub/manual/grub/grub.html#Simple-configuration)

Regards

---

### Post by #&amp;thj^% on 2022-06-26
> **a2-koray said:**
> First time I think i used nano (1st one) but other times:
```

[COLOR="#FF0000"]**sudo gedit /etc/default/grub**[/COLOR]

```
does it matter?



Yes it matter's, problem with using plain sudo is that you are running the program as the root user (elevated privileges) inside the calling directory; this can, in worst case, change the ownership of your important files to root, and, depending on what files got changed, prevent you from booting up the system. 
I would look at grahammechanical suggestion for the right line placement, and Impavidus suggestion to use "sudoedit" to keep ownership as they should be.
Nano is Ok as well>>>But **sudo gedit** is not safe to use.
If you must have/use gedit at least use "sudo -H gedit"

---

### Post by coffeecat on 2022-06-26
> **1fallen said:**
> Yes it matter's 

Not any more, it doesn't. :) Or at least in the context you are describing.

[https://askubuntu.com/questions/1186999/how-does-sudo-handle-home-differently-since-19-10](https://askubuntu.com/questions/1186999/how-does-sudo-handle-home-differently-since-19-10)

From that link:

> As of Ubuntu 19.10, sudo command does what sudo -H command does in previous releases.

Even so, I feel I need to take a shower each time I see "sudo gedit" even though it's been safe since 19.10.

---

### Post by #&amp;thj^% on 2022-06-26
> **coffeecat said:**
> Not any more, it doesn't. :) Or at least in the context you are describing.

[https://askubuntu.com/questions/1186999/how-does-sudo-handle-home-differently-since-19-10](https://askubuntu.com/questions/1186999/how-does-sudo-handle-home-differently-since-19-10)

From that link:





Thanks coffeecat, new info for me, that will be a hard one for me to adjust to. :)
> **coffeecat said:**
> 

Even so, _I feel I need to take a shower each time I see "sudo gedit"_ even though it's been safe since 19.10.
Exactly:popcorn:

---

