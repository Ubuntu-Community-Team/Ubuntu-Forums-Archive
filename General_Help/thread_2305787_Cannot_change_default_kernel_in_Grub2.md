---
title: "Cannot change default kernel in Grub2"
date: 2015-12-09
forum: General Help
---

### Post by G.R.Regis on 2015-12-09
I am a newb to the whole linux/ubuntu but think I've done a fairly good job so far installing 14.04 LTS on my SurfacePro 2.  I pretty much only had an issue with the wifi/bluetooth card that I eventually found a fix for, in part by using a custom kernel.  I now need to select the kernel every time I boot, so instead I wanted to change the default kernel in grub.  It seemed pretty straight forward, but after trying some methods, nothing has worked. 

   I started by editing /etc/default/grub and made this change, GRUB_DEFAULT=4 as the kernel was the fifth option.  I then ran sudo update-grub and rebooted, but it still loaded the generic kernel.    

I then edited /etc/default/grub again by adding GRUB_DEFAULT=saved to the file and ran sudo grub-set-default 4.  I ran sudo update-grub again and rebooted with the same results.    

I then followed these steps:  
Open /etc/default/grub and ensure this line exists:

GRUB_DEFAULT=saved
Apply the change to grub.cfg by running:

grub-mkconfig -o /boot/grub/grub.cfg
Now list all possible menu entries

grep "submenu\|^\smenuentry" /boot/grub/grub.cfg | cut -d "'" -f2
Now set the desired default menu entry

grub-set-default "<submenu title>><menu entry title>"
Verify the default menu entry

grub-editenv list
 I still booted with the generic kernel as default.  When I typed grub-editenv list, I got saved_entry=<Ubuntu>><Linux 3.16.0-surfacepro2+>.  I know I can alway delete the other kernels but I would rather not go that route.  Thanks in advance.

---

### Post by Dennis N on 2015-12-09
I would just leave /etc/default/grub alone in its default state, and make a custom menu entry to appear at the top of the grub menu.

Full details are here:

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

Basically, copy the menu entry to boot the desired kernel from /boot/grub/grub.cfg to /etc/grub.d/40_custom.

The result would be like the first illustration there, which was created from 40_custom in /etc/grub.d with the menuentry for the kernel pasted in. Save the file as /etc/grub.d/06_name. name can be anything, but the file name must start with digits 06,07,08,or 09. Run sudo update-grub and it will appear on top of the generated grub menu. It will be default, since it's first.

Quite easy.

---

### Post by G.R.Regis on 2015-12-09
Thanks for the quick reply.

I tried the following steps and it still boots into the generic kernel by default.  Just to confirm, my /etc/grub.d now has a file named 06_Surface_Pro_2_kernel which look like this
 ```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry 'Ubuntu, with Linux 3.16.0-surfacepro2+' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-surfacepro2+-advanced-095285aa-9820-428c-943c-446b89c052f3' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  095285aa-9820-428c-943c-446b89c052f3
        else
          search --no-floppy --fs-uuid --set=root 095285aa-9820-428c-943c-446b89c052f3
        fi
        echo    'Loading Linux 3.16.0-surfacepro2+ ...'
        linux    /boot/vmlinuz-3.16.0-surfacepro2+ root=UUID=095285aa-9820-428c-943c-446b89c052f3 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-surfacepro2+
    }
```

I also undid the changes in  /etc/default/grub and updated grub, but it is still using the generic kernel as the default.  If I go to advanced boot options, the order has not changed still showing the generic kernel on top.  The same thing when I run grub-mkconfig -o /boot/grub/grub.cfg.

Do I need to add an entry for the menu in the grub.cfg file? I took a peek at it and noticed entries for every other file in grub.d (some commented out).  If I don't, any other suggestions?

---

### Post by G.R.Regis on 2015-12-09
Figured it out.  I changed the bottom part of the posted code with the same lines from the menuentry of the surface pro kernel.
```
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-095285aa-9820-428c-943c-446b89c052f3' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  095285aa-9820-428c-943c-446b89c052f3
    else
      search --no-floppy --fs-uuid --set=root 095285aa-9820-428c-943c-446b89c052f3
    fi
    linux    /boot/vmlinuz-3.16.0-surfacepro2+ root=UUID=095285aa-9820-428c-943c-446b89c052f3 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.16.0-surfacepro2+
```

I did not run sudo update-grub because I was afraid it would delete my changes.  Is that true? And if so, is there any way I can save this as the default so if I need to update grub at some point, I don't need to do this every time?

---

### Post by rmstock2 on 2015-12-09
Here's how to list your boot entries :

```

root@acer30u:/boot/grub# [COLOR=#0000cd]cat grub.cfg | grep "^menuentry "[/COLOR]
**1**[COLOR=#ff0000] menuentry[/COLOR] 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-ed05881c-6d86-4bc1-8ccc-cee6491adc9a' {
**2**[COLOR=#ff0000] menuentry[/COLOR] 'Memory test (memtest86+)' {
**3**[COLOR=#ff0000] menuentry[/COLOR] 'Memory test (memtest86+, serial console 115200)' {
**4**[COLOR=#ff0000] menuentry[/COLOR] 'Mandriva Linux 2011.0 (2011.0) (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-92e466c1-6a5c-4f0c-920c-ec96fd8c1902' {
root@acer30u:/boot/grub#

```

Here's how to list your linux kernel boot entries :

```
root@acer30u:/boot/grub# [COLOR=#0000cd]cat grub.cfg | grep "^[/COLOR][Cntrl-V]+[TAB][COLOR=#0000cd]menuentry "[/COLOR]
    **0**    [COLOR=#ff0000]menuentry[/COLOR] 'Ubuntu, with Linux 3.19.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-39-generic-advanced-ed05881c-6d86-4bc1-8ccc-cee6491adc9a' {
    **1**    [COLOR=#ff0000]menuentry[/COLOR] 'Ubuntu, with Linux 3.19.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-39-generic-recovery-ed05881c-6d86-4bc1-8ccc-cee6491adc9a' {
    **2 **   [COLOR=#ff0000]menuentry[/COLOR] 'Ubuntu, with Linux 3.19.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-37-generic-advanced-ed05881c-6d86-4bc1-8ccc-cee6491adc9a' {
    **3**    [COLOR=#ff0000]menuentry[/COLOR] 'Ubuntu, with Linux 3.19.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-37-generic-recovery-ed05881c-6d86-4bc1-8ccc-cee6491adc9a' {
    **4**   [COLOR=#ff0000]menuentry[/COLOR] 'Ubuntu, with Linux 3.19.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-33-generic-advanced-ed05881c-6d86-4bc1-8ccc-cee6491adc9a' {
    **5 **   [COLOR=#ff0000]menuentry[/COLOR] 'Ubuntu, with Linux 3.19.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-33-generic-recovery-ed05881c-6d86-4bc1-8ccc-cee6491adc9a' {
    **6**    [COLOR=#ff0000]menuentry[/COLOR] 'Ubuntu, with Linux 3.19.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-31-generic-advanced-ed05881c-6d86-4bc1-8ccc-cee6491adc9a' {
    **7**    [COLOR=#ff0000]menuentry[/COLOR] 'Ubuntu, with Linux 3.19.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-31-generic-recovery-ed05881c-6d86-4bc1-8ccc-cee6491adc9a' {
    **8**    [COLOR=#ff0000]menuentry[/COLOR] 'Ubuntu, with Linux 3.19.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-30-generic-advanced-ed05881c-6d86-4bc1-8ccc-cee6491adc9a' {
    **9**    [COLOR=#ff0000]menuentry[/COLOR] 'Ubuntu, with Linux 3.19.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-30-generic-recovery-ed05881c-6d86-4bc1-8ccc-cee6491adc9a' {
   **10**   [COLOR=#ff0000]menuentry[/COLOR] 'Ubuntu, with Linux 3.19.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-25-generic-advanced-ed05881c-6d86-4bc1-8ccc-cee6491adc9a' {
   **11**   [COLOR=#ff0000]menuentry[/COLOR] 'Ubuntu, with Linux 3.19.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-25-generic-recovery-ed05881c-6d86-4bc1-8ccc-cee6491adc9a' {
   **12**   [COLOR=#ff0000]menuentry[/COLOR] 'linux (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz--92e466c1-6a5c-4f0c-920c-ec96fd8c1902' {
   **13**   [COLOR=#ff0000]menuentry[/COLOR] 'linux-nonfb (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz--92e466c1-6a5c-4f0c-920c-ec96fd8c1902' {
   **14**   [COLOR=#ff0000]menuentry[/COLOR] 'failsafe (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz--92e466c1-6a5c-4f0c-920c-ec96fd8c1902' {
root@acer30u:/boot/grub# 
```

to reboot into kernel 3.19.0-37-generic  do this :

```
root@acer30u:/boot/grub# [COLOR=#0000cd]uname -a[/COLOR]
Linux acer30u 3.19.0-39-generic #44~14.04.1-Ubuntu SMP Wed Dec 2 10:00:35 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
root@acer30u:/boot/grub# [COLOR=#0000cd]grub-reboot 'Advanced options for Ubuntu'\>2[/COLOR]
root@acer30u:/boot/grub# [COLOR=#0000cd]grub-reboot 1\>2[/COLOR]
root@acer30u:/boot/grub# [COLOR=#0000cd]shutdown -r now[/COLOR]

Broadcast message from root@acer30u
        (/dev/pts/4) at 2:10 ...

The system is going down for reboot NOW!
root@acer30u:/boot/grub# Connection to acer30 closed by remote host.
Connection to acer30 closed.
[acer20:stock]:(~)$
[acer20:stock]:(~)$ ssh root@acer30
root@acer30's password: 
Welcome to Ubuntu 14.04.3 LTS (GNU/Linux 3.19.0-37-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

3 packages can be updated.
3 updates are security updates.

Last login: Thu Dec 10 02:35:59 2015 from acer20.stokkie.net
root@acer30u:~# [COLOR=#0000cd]uname -a[/COLOR]
Linux acer30u 3.19.0-37-generic #42~14.04.1-Ubuntu SMP Mon Nov 23 15:13:51 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
root@acer30u:~# 
 
```

to reboot into Mandriva 2011 you enter : grub-reboot 4  before a reboot.
The same MENU_ENTRY syntax valid for grub-reboot is also valid for grub-set-default (i assume) :

```

root@acer30u:~# grub-reboot --help
Usage: grub-reboot [OPTION] MENU_ENTRY
Set the default boot menu entry for GRUB, for the next boot only.
  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --boot-directory=DIR    expect GRUB images under the directory DIR/grub
                          instead of the /boot/grub directory

MENU_ENTRY is a number, a menu item title or a menu item identifier. Please note that menu items in
submenus or sub-submenus require specifying the submenu components and then the
menu item component. The titles should be separated using the greater-than
character (>) with no extra spaces. Depending on your shell some characters including > may need escaping. More information about this is available
in the GRUB Manual in the section about the 'default' command. 

Report bugs to <bug-grub@gnu.org>.
root@acer30u:~#

```

```

root@acer30u:~# grub-set-default --help
Usage: grub-set-default [OPTION] MENU_ENTRY
Set the default boot menu entry for GRUB.
This requires setting GRUB_DEFAULT=saved in /etc/default/grub.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --boot-directory=DIR    expect GRUB images under the directory DIR/grub
                          instead of the /boot/grub directory

MENU_ENTRY is a number, a menu item title or a menu item identifier.

Report bugs to <bug-grub@gnu.org>.
root@acer30u:~#

```

---

### Post by Dennis N on 2015-12-10
> **G.R.Regis said:**
> Figured it out.  I changed the bottom part of the posted code with the same lines from the menuentry of the surface pro kernel.
I did not run sudo update-grub because I was afraid it would delete my changes.  Is that true? And if so, is there any way I can save this as the default so if I need to update grub at some point, I don't need to do this every time?

After you copy your custom menu entry file to /etc/grub.d, you have to run sudo update-grub to create a new grub menu that includes this new entry at the top. Be sure to leave the top part of 40_custom in place and add your copied code after right that. 

grub executes all the scripts in /etc/grub.d in sequence (01*, 02* ...) to make the grub menu. exec tail -n 3 tells grub to copy the code after the comments at the top to the new menu (grub.cfg). Since 06 is always done before 10 (which generates the first entry otherwise, labeled 'ubuntu'), grub always puts this 06 custom entry before that when grub is updated. The normal 'ubuntu' entry would change to the new kernel when you update grub, but your custom one will never change content or position and always be on top as default.

---

### Post by efflandt on 2015-12-10
For future reference, this in /etc/default/grub will default grub to select whatever you booted from it last (even Windows):```
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
```

---

### Post by G.R.Regis on 2015-12-11
Dennis:
Thanks for the tips.  I had already tried the steps listed in your second post.  I copied the menuentry for the kernel to 40_custom, saved it as 06_surface, ran sudo update-grub, but after the grub.cfg had no entry for my custom menu 06_surface.  That is why I made the changes as stated in post #4 in this thread.

effiandt:
Tried your steps but as soon as I ran sudo update-grub, it reverted the grub.cfg to boot with the generic kernel even though the las kernel I booted with was the surface pro 2 kernel.

Is there any way to make the changes I made in post #4 stick whenever I run sudo update-grub?

---

### Post by Dennis N on 2015-12-11
> **G.R.Regis said:**
> Dennis:
Thanks for the tips.  I had already tried the steps listed in your second post.  I copied the menuentry for the kernel to 40_custom, saved it as 06_surface, ran sudo update-grub, but after the grub.cfg had no entry for my custom menu 06_surface.  That is why I made the changes as stated in post #4 in this thread.

The file 06_surface has to be made executable after being copied to /etc/grub.d since it is a script. If you didn't do that, it won't run and add the custom menu entry to your grub menu when you update-grub.

Navigate to /etc/grub.d and run **sudo chmod +x 06_surface** and run sudo update-grub again. It should now appear.

---

### Post by G.R.Regis on 2015-12-12
So I ran chmod +x and it seemed to work.  On the grub boot menu the first option is my custom menu, however it i still not quite how I want it.  Now, instead of highlighting the first entry for my custom menu, it has the second entry for launching ubuntu (with the generic kernel) highlighted as default.  I also tried putting GRUB_DEFAULT=saved to see if it would highlight the previous booted selection.  It does that for every other menu option except for my custom menu, i.e. if I boot into windows, after rebooting the boot from windows option is highlighted.  It even does that if I choose advanced booting options, it only doesn't do it for the custom entry.

---

### Post by yancek on 2015-12-12
If your custom entry is the first in the menu, you could try putting the GRUB_DEFAULT=0.
Don't know if that will work if the 'saved' method doesn't but it's easy enough to try.  Run sudo update-grub after the change of course.

---

### Post by Dennis N on 2015-12-12
Hello G.R.

Have a look at my /etc/default/grub. It is important to have **GRUB_DEFAULT=0** if you want to boot the first grub selection automatically. I modified mine from default only by changing **GRUB_TIMEOUT=** from 10 to -1, which then requires manual selection of an entry to proceed. Grub could not know how each entry got into grub.cfg, either by a custom menu entry file or inserted by 10_linux or 30_os-prober - they all look the same. You could have a saved boot setup or different default to get the selection mark (*) anywhere else.

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=-1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

(everything below this is commented out in my file)

---

### Post by G.R.Regis on 2015-12-13
I spoke a little too soon.  When I boot from advanced options, it does remember the kernel I used last time. I did not make any further changes (and the GRUB_DEFAULT was/is set to 0). All is good, thanks for all your help.

---

