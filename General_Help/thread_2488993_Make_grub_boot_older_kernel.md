---
title: "Make grub boot older kernel"
date: 2023-07-14
forum: General Help
---

### Post by marc raes on 2023-07-14
I use Ubuntu since 2006. 
I work with the LTS releases. But now and then I check releases in  between, to see how things are evolving.
So, recently I let the installer of 23.04 automatically install this release on a second partition on the sda disk of my old Asus pc next to the 22.04.2 release I am currently using.
As is default, it boots from 23.04.
I want to change this, and make it boot again from 22.04.
Years ago, this was very easy to accomplish. Not so now with grub2.
I read everything I could find on the web to make this work.
As far as I tried all that out, nothing did the trick.

First of all, this is what the grub-window displays:


[B]Ubuntu
Advanced options for Ubuntu
Memory test (memtest86+x64.bin)
Memory test (memtest86+x64.bin, serial console)
Ubuntu 22.04.2 LTS (22.04) (on /dev/sda1)
Advanced options for Ubuntu 22.04.2 LTS (22.04) (on /dev/sda1)[/B]

I installed the latest version of “Grub Customizer”. This tool didn’t even find the sda2 with 23.04 installed!
So I was told to add the following lines to the  etc/default/grub file:

GRUB_DEFAULT="saved"  
GRUB_DISABLE_OS_PROBER=false 
Which I did, and also put  GRUB_SAVEDEFAULT="true"    
 
And after ‘update-grub’, the edited /etc/default/grub file looked like this:

[i]# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="Ubuntu 22.04 (22.04) (on /dev/sda1)"
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_SAVEDEFAULT="true"

GRUB_DISABLE_OS_PROBER="false"

GRUB_DEFAULT="saved"[/i]



And Grub Customizer gave this output:


[IMG]http://blogimages.seniorennet.be/antoniusvanpadua/P4658425-b140890c48cb37ce1642bdba3d6462d4.png[/IMG]


So, I supposed the ‘Ubuntu’ I put on top should  be the  22.04.2 and after saving this ‘constellation’  I expected grub to boot from 22.04. It did not…
I didn’t find out how to solve this issue.
Has anyone succeeded? So tell this unhappy bloke how you did it!

---

### Post by oldfred on 2023-07-14
Do not use Grub Customizer. That is for configuring your grub. And it replaces grub with its own grub proxy files.
Last install is version of grub used to boot by default.

Easy to fix as last install's grub should also have a boot entry for your main working install.
Boot into that and reinstall grub.
sudo grub-install

Alternative is to use Boot-Repair and its advanced mode to choose an install & choose a drive.
Default fix often is just update grub, your want full install.

Another alternative is, if UEFI, to just edit /EFI/Ubuntu/grub.cfg with UUID of preferred install.

---

### Post by guiverc on 2023-07-14
I've not used Ubuntu since 2006, only first used it in 2010, which was about the time of grub 1 changing to grub 2 (or 1.9x). Other than that change (*I'd used Debian and other GNU/Linux awhile so I didn't see that change as anything Ubuntu specific anyway*) I've seen little.

The only other change I recall was introduction of grub 2.06 ([https://lists.ubuntu.com/archives/ubuntu-devel/2021-December/041769.html](https://lists.ubuntu.com/archives/ubuntu-devel/2021-December/041769.html)) and how it handled OS-PROBER & other OSes. For awhile my Ubuntu system (*I use development most of the time*) when it updated no longer detected my other OS (Ubuntu LTS which at that time was 18.04), but that didn't last long, as Ubuntu now carried patches that mean Ubuntu 22.04 LTS & later work as prior releases do (*I see the changed behavior in Debian though*).

I'd not use grub customizer, and agree with what oldfred has said.

The last installed OS usually controls the boot process; as I re-install an OS almost weekly (*on dual boot systems*) that OS takes ownership of the boot which is something I do not actually want, thus I just use `grub-install` like I did a decade+ ago to return boot control back to the OS I want to control the boot process (`grub-install` being run on the OS I want to control booting). I do this and it works on multiple machines (*some using old legacy/BIOS/CSM and others using uEFI*).

FYI:  Not all GNU/Linux have `grub-install`, but Debian/Ubuntu do; but grub-install is just a front-end that simplifies the actual command.

As far as I'm remembering, it was the same process in Ubuntu 10.04, 10.10 & 11.04 (*early days of grub 1.9x which followed grub 2 standards*). FYI: Grub2 was introduced in Ubuntu 9.10 or *Karmic Koala*, thus for me Ubuntu has always used grub2, Grub 1 was what I'd used in Debian before hand.

---

### Post by marc raes on 2023-07-15
Of course I do boot from 22.04 in the grub menu by scrolling down with the down arrow. But you have only 10 seconds to do that. And often I am to late for that.
That's why I want to make it automatically boot into 22.04!
Your suggestion 'sudo grub-instlall' gave me this answer: 
"Installeren voor i386-pc-platform.
grub-install: fout: geen installatie-apparaat opgegeven." (I'm Flemish, I'll try to translate that):
"Install for i386-pc-platform.
grub-install: error: no installation-apparatus set."
Where do I go from there?

---

### Post by marc raes on 2023-07-15
WAW! Boot-repair did the trick!

Thanks a lot 'oldfred'!

---

### Post by oldfred on 2023-07-15
Not sure why grub-install did not work. 
Are both UEFI installs? Of both BIOS?

Glad Boot-Repair worked, you can change to solved, so others can find thread.

---

