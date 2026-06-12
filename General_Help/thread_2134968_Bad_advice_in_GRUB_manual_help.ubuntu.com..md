---
title: "Bad advice in GRUB manual? help.ubuntu.com.*"
date: 2013-04-12
forum: General Help
---

### Post by Locus Kiesselbachi on 2013-04-12
Problem:
Need to change idle timeout of grub menu.

[Community Help Wiki]("https://help.ubuntu.com/community/Grub2") at help.ubuntu.com says that:
/etc/grub.d/00_header ... change line **236** (this line is in the "make_timeout()" function) to "set timeout=0",
but...
"make_timeout()" is situated at line [B]279
[/B]
I conclude someone had made changes in GRUB, but not updated THE manual!
That also means I should not go forward with next step, which asks me to:
[COLOR=#333333][FONT=Ubuntu]edit [/FONT][/COLOR]/etc/grub.d/10_linux[COLOR=#333333][FONT=Ubuntu] ... change line 188 to "[/FONT][/COLOR]set linux_gfx_mode=keep",
but...
in line 188 is "```
    *) GENKERNEL_ARCH="$machine" ;;
```" Im not going to delete/change that! Manual does not say what must be in line 188!

I already have messed with no effect in:
```

#GRUB_HIDDEN_TIMEOUT="0" 
GRUB_HIDDEN_TIMEOUT_QUIET="true" 
GRUB_TIMEOUT="10"
```
/etc/default/grub
yes I also made "sudo update-grub" every time I changed something in grub.

Im messing around with this grub time-out problem in [this thread]("http://ubuntuforums.org/showthread.php?t=2134683").

Can anyone suggest more manuals to dig in?

---

### Post by deadflowr on 2013-04-12
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

I myself, have had no such problem changing the default timeout in /etc/default/grub.

Edit: it's also important to know that there are different versions of grub2.
The 'scripts' in version 1.98 differ slightly from those in version 2.00 or even 1.99.

---

### Post by dave2001 on 2013-04-12
Seconding Deadflowr's info. The only file you need to edit is /etc/default/grub. 

However, *no changes will be enacted until* you run "sudo update-grub" to auto generate a new grub.cfg

if your following those step correctly, and still not seeing changes, I'd guess you've messed up some other aspect of grub already, and should just reinstall it.

---

### Post by Locus Kiesselbachi on 2013-04-12
ehh!
```
sudo leafpad /etc/default/grub
```
I just type this code to terminal and copy grub here

```
# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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

Time-out is zero as in can get! 
Im out of ideas!
If you notice anything or have some toughts let me now.

P.S.
system has two hard-drives, one has Lubuntu, other has win 7. I dont want grub menu, when I want to choose boot I let BIOS do it.

---

### Post by oldfred on 2013-04-12
Is it shutting down normally? Any errors force grub to show. You may be able to turn os-prober off if always booting from BIOS. Then it only has one system and should not show grub menu.

       Discussion of timeouts issue & recordfail:
[http://ubuntuforums.org/showthread.php?t=1717700](http://ubuntuforums.org/showthread.php?t=1717700)

      
  turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by dave2001 on 2013-04-13
> **Locus Kiesselbachi said:**
> ehh!

P.S.
system has two hard-drives, one has Lubuntu, other has win 7. I dont want grub menu, when I want to choose boot I let BIOS do it.

This is why you should put your system setup in initial posts. *When Grub encounters another OS it automatically shows the boot menu*. I'm sure Oldfred's above method works for this, but supposedly the "preferred" method for altering grub behavior these days is through editing /etc/grub/default.

To disable the OS prober, and thus stop having your grub menu show even though the timeout is set to O, add this to the file:

[HTML]GRUB_DISABLE_OS_PROBER=true[/HTML] and then update grub.

You might want to consider puting in a one-two second silent timeout or enabling the recovery option. You'll be wishing you had access to your grub menu if an update ever screws your system.

---

### Post by Locus Kiesselbachi on 2013-04-15
to [dave2001]("http://ubuntuforums.org/member.php?u=1047045"):
Your given code did not help. I also found it in GRUB manual, link given by [deadflowr]("http://ubuntuforums.org/member.php?u=1276577"). As I said it didnt turn off OSprober. Why? :confused: Dont know, it should have.

to [oldfred]("http://ubuntuforums.org/member.php?u=852711")
Your given link did help.
```
sudo leafpad [COLOR=#000000][FONT=Ubuntu Mono]/boot/grub/grub.cfg[/FONT][/COLOR]
```
...I looked for:
```
[COLOR=Red]***#***[/COLOR][COLOR=#000000]*if [ "${recordfail}" = 1 ]; then*[/COLOR]
[COLOR=Red]***#***[/COLOR][COLOR=#000000]* set timeout=-1*[/COLOR]
[COLOR=Red]***#***[/COLOR][COLOR=#000000]*else*[/COLOR]
[COLOR=#000000]*set timeout=*[/COLOR][COLOR=Red]***0***[/COLOR]
[COLOR=Red]***#***[/COLOR][COLOR=#000000]*fi*[/COLOR]
```
As I understand, this change in grub.cfg disappears if made "sudo update-grub". So I will not update it.
To make it permanent user have to change [COLOR=#000000]/etc/grub.d/00_header, as I started this thread with. 
But** this is the point of this thread**, manual for it gives misinformation and misguides noobs like myself.


[/COLOR];) I temporarily deleted "30_os-prober" part in grub.cfg, leaving only "###BEGIN..." and "###END...". No effect.[COLOR=#000000]

I will add **grub.cfg** in this replay for anyone who might be interested:
[/COLOR]```
## DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"


if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi


export menuentry_id_option


if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi


function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}


function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}


function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}


if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  9e3b5833-7c11-4181-bd58-e8b1a6fbdb5b
else
  search --no-floppy --fs-uuid --set=root 9e3b5833-7c11-4181-bd58-e8b1a6fbdb5b
fi
    font="/usr/share/grub/unicode.pf2"
fi


if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-9e3b5833-7c11-4181-bd58-e8b1a6fbdb5b' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c0ffb4aa-021f-4fbe-abc1-6b1a3fc76e31
    else
      search --no-floppy --fs-uuid --set=root c0ffb4aa-021f-4fbe-abc1-6b1a3fc76e31
    fi
    linux    /vmlinuz-3.5.0-17-generic root=UUID=9e3b5833-7c11-4181-bd58-e8b1a6fbdb5b ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.5.0-17-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-9e3b5833-7c11-4181-bd58-e8b1a6fbdb5b' {
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-9e3b5833-7c11-4181-bd58-e8b1a6fbdb5b' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c0ffb4aa-021f-4fbe-abc1-6b1a3fc76e31
        else
          search --no-floppy --fs-uuid --set=root c0ffb4aa-021f-4fbe-abc1-6b1a3fc76e31
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /vmlinuz-3.5.0-17-generic root=UUID=9e3b5833-7c11-4181-bd58-e8b1a6fbdb5b ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-9e3b5833-7c11-4181-bd58-e8b1a6fbdb5b' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c0ffb4aa-021f-4fbe-abc1-6b1a3fc76e31
        else
          search --no-floppy --fs-uuid --set=root c0ffb4aa-021f-4fbe-abc1-6b1a3fc76e31
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /vmlinuz-3.5.0-17-generic root=UUID=9e3b5833-7c11-4181-bd58-e8b1a6fbdb5b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.5.0-17-generic
    }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c0ffb4aa-021f-4fbe-abc1-6b1a3fc76e31
    else
      search --no-floppy --fs-uuid --set=root c0ffb4aa-021f-4fbe-abc1-6b1a3fc76e31
    fi
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c0ffb4aa-021f-4fbe-abc1-6b1a3fc76e31
    else
      search --no-floppy --fs-uuid --set=root c0ffb4aa-021f-4fbe-abc1-6b1a3fc76e31
    fi
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-9CBC43D6BC43AA1A' {
    insmod part_msdos
    insmod ntfs
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  9CBC43D6BC43AA1A
    else
      search --no-floppy --fs-uuid --set=root 9CBC43D6BC43AA1A
    fi
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###



```[COLOR=#000000]

[/COLOR]

---

### Post by dave2001 on 2013-04-15
I will have to maintain my position that there is something out of whack with your system. Normally everything suggested in this thread works as intended. Glad you found a workaround that did the job.

---

