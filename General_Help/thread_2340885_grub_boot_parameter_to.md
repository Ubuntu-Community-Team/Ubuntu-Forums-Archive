---
title: "grub boot parameter to"
date: 2016-10-22
forum: General Help
---

### Post by Bashing-om on 2016-10-22
Hello people; I have a good one .

Where is the boot parameter reset ?
And what is the meaning of 'to' ?
The kernel boot line from /var/log/Xorg.0.log:
> 
[    54.546] Kernel command line: BOOT_IMAGE=(hd0,msdos1)/vmlinuz root=/dev/sda1 [color=red]to[/color]

confirmed to be 'to' "
> 
sysop@1404mini:~$ cat /proc/cmdline
BOOT_IMAGE=(hd0,msdos1)/vmlinuz root=/dev/sda1 [color=red]to[/color]

Whereas the boot directives have 'ro' set:
/etc/fstab:
> 
UUID=3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 /               ext4    errors=remount-[color=green]ro[/color] 0     1

 And in /boot/grub/grub.cfg
> 
linux	/boot/vmlinuz-3.13.0-100-generic root=UUID=3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 [color=green]ro[/color]  text


My google-fu is failing me in this respect .

when all else fails
[INDENT][INDENT]ask on the forum
[/INDENT][/INDENT]

---

### Post by yetimon_64 on 2016-10-22
Hi Bashing-om, 
I would suggest you check the file **/etc/default/grub** and check the line GRUB_CMDLINE_LINUX_DEFAULT or the line GRUB_CMDLINE_LINUX doesn't have a typo in it. I suspect there may be a typo somewhere as "r" and "t" are beside each other on the keyboard. I too have never seen "to" as a boot parameter. 

If there is a typo in /etc/default/grub the xorg log you see "to" in may be picking it up as an error.  
Regards, yeti

**Edit:** I would also suggest you double check any files in /etc/grub.d you may have at any time altered (if you have ever done so, that is)

---

### Post by &amp;KyT$0P# on 2016-10-22
Normally the [FONT=Courier New]ro[/FONT] parameter comes from [FONT=Courier New]/etc/grub.d/10_linux[/FONT] so you might check there as well.

---

### Post by Bashing-om on 2016-10-22
yetimon_64; halogen2; Thanks guys.

This has really got me . And spurs on my thirst for knowledge.
:)
I Find no faults in /etc/default/grub :
> 
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR="My-Work-14.04"
GRUB_CMDLINE_LINUX_DEFAULT="text"
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
GRUB_GFXMODE=1600x900

This configuration has worked well for a long period of time - huuuummm come to think of it -
I did not notice the 'to' until the new -100 kernel install . Will boot an older kernel and see .

Nor have I messed with the config files in /etc/grub.d/ in a very long while . But will take the time to look through them .. but, as the file /boot/grub/grub.cfg is clean I do not expect to find any errors .

This is on a 14.04 minimal solid/stable install with xfce as the DE. Be also aware that I have a too new graphics card that has no support in 14.04 and loading the vesa driver .

[color=red]to[/color] Who is this masked man ?

[INDENT][INDENT]an itch
[INDENT][INDENT]I just gotta scratch
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by yetimon_64 on 2016-10-22
> **Bashing-om said:**
> [COLOR=#000000]...[/COLOR][COLOR=red]to[/COLOR] Who is this masked man ?[INDENT][INDENT]an itch[INDENT][INDENT]I just gotta scratch
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


That has got me "scratching" my head as well :).

I just looked at the kernel parameters available on kernel.org [[COLOR=#0000ff]--here--[/COLOR]]("https://www.kernel.org/doc/Documentation/kernel-parameters.txt"), and no mention of any "to" parameter. "ro" is listed though.

> But will take the time to look through themI suggest you go straight to the file /etc/grub.d/10_linux for checking as I think halogen2 is correct about that being where that kernel parameter is set from. That may quicken your search up a bit, hopefully.

**Edit:** I just noted the "text" setting in the GRUB_CMDLINE_LINUX_DEFAULT line and am wondering if it means "text only". It may be related to that in some way ?

---

### Post by Bashing-om on 2016-10-22
@ yetimon_64;

Yeah ; I have spent several hours on this and have expended my google-fu. I have yet to find any hint what 'to' is.

And yes too on to= (t)ext (o)nly . I look over this system quite a lot and this is the 1st time this boot parameter has come to my attention.

Will continue to investigate, see what I can find out .
Will reboot with older kernel and will look through grub's config files ; and then report my findings.

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-10-23
Huuummmmm .

Graphics related:
> 
sysop@1404mini:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-100-generic root=UUID=3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 [color=green]ro[/color] nomodeset text
sysop@1404mini:~$

As the only change I make is to boot with the 'nomodeset' boot parameter from grub's boot menu .
I do note that in grub's kernel boot line the boot parameter in all installed kernels is set to 'ro' .

I have a updated bios chip on the way . When the new chip is is in place I bet we see a difference.

Still, where does 'to' originate from ?

[INDENT][INDENT]still look'n
[INDENT][INDENT][INDENT]even after all this time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

