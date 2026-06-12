---
title: "Grub menuentry (3 entries rather then 2)"
date: 2015-02-13
forum: General Help
---

### Post by heyup on 2015-02-13
I'm using Precise on a multiboot hard drive. I've just installed Trusty. After updating grub on Precise I notice that there are 3 entries in the boot menu for the Trusty install rather than the usual 2 entries. 

These are the entries:
> 7	menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 
     8	menuentry "Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 
     9	menuentry "Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 


Do I boot into menuentry 7 or 8? Why the extra menuentry?

---

### Post by ajgreeny on 2015-02-13
I am pretty sure that 7 and 8 do the same thing and boot the most recent kernel installed.

I never see the grub menu at boot but to keep up with the kernels I have installed, and to be able to remove them I have an alias
```
alias menu='grep "menuentry " /boot/grub/grub.cfg | cut -c 1-82'
```so the command menu tells me what kernels I have, which at present is
```
ajgreeny@XubuntuTrusty:~$ menu
menuentry 'Xubuntu-14.04 GNU/Linux' --class xubuntu_14_04 --class gnu-linux --clas
    menuentry 'Xubuntu-14.04 GNU/Linux, with Linux 3.13.0-45-generic' --class xubuntu
    menuentry 'Xubuntu-14.04 GNU/Linux, with Linux 3.13.0-45-generic (recovery mode)'
    menuentry 'Xubuntu-14.04 GNU/Linux, with Linux 3.13.0-44-generic' --class xubuntu
    menuentry 'Xubuntu-14.04 GNU/Linux, with Linux 3.13.0-44-generic (recovery mode)'
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
menuentry "Reboot" {
menuentry "Halt" {
```
The Reboot and Halt entries are historical and added in the 40_custom file in /etc/grub.d but I keep them in case they ever become useful again.  File contents are
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Reboot" {
    reboot
}
menuentry "Halt" {
    halt
}

```

---

### Post by grahammechanical on 2015-02-13
It is a long time since I have used Precise. Does the Precise Grub give Advanced Options sub-menus? I would guess that

Item 7 is the normal or standard boot entry for that install of Ubuntu.
Item 8 is with added ram disc parameter.
Item 9 is with recovery parameter.

Item 7 is there so that we can do a normal boot without backing out of the Advanced Options submenu. You can choose either item 7 or 8 the boot parameters are the same. The only difference I have noticed is that what you label as item 8 will show a "loading initial ram disc" message which we do not see with item 7.

Regards.

---

### Post by heyup on 2015-02-14
I don't see an Advanced Options submenu.

I still cannot work out why there are 3 entries for the Trusty install. There are normally 2 entries for each kernel. 

Trusty:
> menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-24c94cb2-2e4b-4348-8fd8-909601c31714 (on /dev/sdc12)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-24c94cb2-2e4b-4348-8fd8-909601c31714 (on /dev/sdc12)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-24c94cb2-2e4b-4348-8fd8-909601c31714 (on /dev/sdc12)" --class gnu-linux --class gnu --class os {

Precise:
> menuentry 'Ubuntu, with Linux 3.2.0-76-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-76-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-75-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-75-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {


---

### Post by ajgreeny on 2015-02-14
This is probably simply because the versions of grub in precise and trusty are different.

If the output you show is from my grep command, you will not see the Advanced section shown separate from anything else; the command does not show the actual grub menu but simply the list of kernels installed.  Other config files for grub set out the arrangement and how you will see them listed.

---

