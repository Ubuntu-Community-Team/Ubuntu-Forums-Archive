---
title: "GNU GRUB no longer auto times out"
date: 2015-03-03
forum: General Help
---

### Post by peridian on 2015-03-03
Hi,

I don't know what has happened, but in the last few days my GRUB bootup seems to have stopped auto timing out, and just sits there with the Ubuntu option highlighted continuously until I hit enter.

I currently have GNU GRUB version 2.02^beta2-9ubuntu1.  Ubuntu 14.04.1.

I've tried changing the timeout in the */etc/default/grub* file from 10 seconds to 5, I've also tried running ```
sudo update-grub
``` with both values but it always appears to succeed without error and yet has no effect.  I've also checked the /boot partition to make sure it still has space left (only 38% used).

Any ideas?

Regards,
Rob.

---

### Post by Kirboosy on 2015-03-04
Can you copy and paste the entire */etc/default/grub* that you have?

~Caboose

---

### Post by peridian on 2015-03-04
I just tried setting the GRUB_HIDDEN_TIMEOUT value, but no luck.  I've also checked that there is definitely a file at /boot/grub/grub.cfg

/etc/default/grub

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=1
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
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

Also, output of ls /boot

```

abi-3.13.0-32-generic     config-3.13.0-46-generic      lost+found                    System.map-3.13.0-43-generic
abi-3.13.0-43-generic     grub                          memtest86+.bin                System.map-3.13.0-46-generic
abi-3.13.0-46-generic     initrd.img-3.13.0-32-generic  memtest86+.elf                vmlinuz-3.13.0-32-generic
config-3.13.0-32-generic  initrd.img-3.13.0-43-generic  memtest86+_multiboot.bin      vmlinuz-3.13.0-43-generic
config-3.13.0-43-generic  initrd.img-3.13.0-46-generic  System.map-3.13.0-32-generic  vmlinuz-3.13.0-46-generic

```

Regards,
Rob.

---

### Post by grahammechanical on 2015-03-04
This is what the Grub manual says about GRUB_HIDDEN_TIMEOUT

> Wait this many seconds for a key to be pressed before displaying the menu. If no key is pressed during that time, display the menu for the number of seconds specified in GRUB TIMEOUT before booting the default entry. We expect that most people who use GRUB HIDDEN TIMEOUT will want to have GRUB TIMEOUT set to ‘0’ so that the menu is not displayed at all unless a key is pressed. Unset by default.


So, GRUB_HIDDEN_TIMEOUT is not part of the solution. On my system not only is hidden timeout set to = 0 but it is commented out with a #.

This is what the Grub manual says about GRUB_TIMEOUT

> Boot the default entry this many seconds after the menu is displayed, unless a key is pressed. The default is ‘5’. Set to ‘0’ to boot immediately without displaying the menu, or to ‘-1’ to wait indefinitely.


On Ubuntu the default is usually set to 10 seconds. You have set yours to 5 seconds and have run sudo update-grub. So what can I suggest?

1) run both of these commands

```
sudo update-grub
sudo grub-install /dev/sda
```

I am assuming that you have only one hard disk (sda) and Ubuntu is installed on it and not on a second hard disk (sdb). I have found that sometimes in order for a modification to the Grub configuration files we sometimes need to re-install Grub using that command.

2) check the keyboard to see if a key is not shorting across. OK. I admit it. I am getting desperate for suggestions.

3) open /boot/grub/grub.cfg in Gedit and look near the top of the file and look for these lines

> terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###


That is taken from my grub.cfg. See if the 2 "set timeout=" in your grub.cfg are similar. The second "set timeout=" should be 5 on your system. Is there anything usual about those 2 "set timeout=" settings?

Regards.

---

### Post by Kirboosy on 2015-03-05
Yeah grahammechanical is right. Make your grub look like this

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

Comment out the GRUB_HIDDEN_TIMEOUT. Lets try to keep it simple

Hope that helps!
~Caboose
PS I would recommend running ```
sudo apt-get autoremove 
``` to clean up old kernels once you get everything working again!

---

### Post by peridian on 2015-03-06
Hi,

Did as suggested, no change.  It's almost as if the GNU GRUB screen I see on boot is not the one being touched by the configuration.


[LIST=1]
[*]How can I check that the /boot directory I look at in my user session is the correct one used by the boot sequence?
[*]I have pasted my entire grub.cfg file below, does anything stand out?
[*]When I performed the autoremove, it only removed the 3.13.0-32 images, and left both 3.13.0-43 and 3.13.0-46 in place.  Is it normal to have the last two releases, or should there only be the latest?
[/LIST]

Regards,
Rob.

Some more command output:

```

user@hostname:~$ df
Filesystem                  1K-blocks     Used Available Use% Mounted on
/dev/mapper/ubuntu--vg-root 238961232 22193064 204606532  10% /
none                                4        0         4   0% /sys/fs/cgroup
udev                           488116        4    488112   1% /dev
tmpfs                          100680     1096     99584   2% /run
none                             5120        0      5120   0% /run/lock
none                           503392       72    503320   1% /run/shm
none                           102400       20    102380   1% /run/user
/dev/sda1                      240972    83406    145125  37% /boot
/home/user/.Private         238961232 22193064 204606532  10% /home/user


user@hostname:~$ ls /dev
agpgart          full          net                 ram4      snd     tty21  tty39  tty56      ttyS14  ttyS31     vcs7
autofs           fuse          network_latency     ram5      stderr  tty22  tty4   tty57      ttyS15  ttyS4      vcsa
block            hidraw0       network_throughput  ram6      stdin   tty23  tty40  tty58      ttyS16  ttyS5      vcsa1
bsg              hpet          null                ram7      stdout  tty24  tty41  tty59      ttyS17  ttyS6      vcsa2
btrfs-control    input         port                ram8      tty     tty25  tty42  tty6       ttyS18  ttyS7      vcsa3
bus              kmsg          ppp                 ram9      tty0    tty26  tty43  tty60      ttyS19  ttyS8      vcsa4
char             log           psaux               random    tty1    tty27  tty44  tty61      ttyS2   ttyS9      vcsa5
console          loop0         ptmx                rfkill    tty10   tty28  tty45  tty62      ttyS20  ubuntu-vg  vcsa6
core             loop1         pts                 rtc       tty11   tty29  tty46  tty63      ttyS21  uhid       vcsa7
cpu              loop2         ram0                rtc0      tty12   tty3   tty47  tty7       ttyS22  uinput     vga_arbiter
cpu_dma_latency  loop3         ram1                sda       tty13   tty30  tty48  tty8       ttyS23  urandom    vhci
cuse             loop4         ram10               sda1      tty14   tty31  tty49  tty9       ttyS24  usb        vhost-net
disk             loop5         ram11               sda2      tty15   tty32  tty5   ttyprintk  ttyS25  vcs        zero
dm-0             loop6         ram12               sda5      tty16   tty33  tty50  ttyS0      ttyS26  vcs1
dm-1             loop7         ram13               sdb       tty17   tty34  tty51  ttyS1      ttyS27  vcs2
dri              loop-control  ram14               sg0       tty18   tty35  tty52  ttyS10     ttyS28  vcs3
ecryptfs         mapper        ram15               sg1       tty19   tty36  tty53  ttyS11     ttyS29  vcs4
fb0              mcelog        ram2                shm       tty2    tty37  tty54  ttyS12     ttyS3   vcs5
fd               mem           ram3                snapshot  tty20   tty38  tty55  ttyS13     ttyS30  vcs6

```

/boot/grub/grub.cfg

```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi


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
insmod lvm
insmod ext2
set root='lvmid/BvyP0E-ij0c-w7zu-C9zT-FAVg-8E9P-jxS1mQ/eHmCc1-rwhZ-Ucvc-mp8W-0cJT-M5mf-e4PY3h'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint='lvmid/BvyP0E-ij0c-w7zu-C9zT-FAVg-8E9P-jxS1mQ/eHmCc1-rwhZ-Ucvc-mp8W-0cJT-M5mf-e4PY3h'  437b1022-0dc2-47dc-90b7-5104c8a317c7
else
  search --no-floppy --fs-uuid --set=root 437b1022-0dc2-47dc-90b7-5104c8a317c7
fi
    font="/usr/share/grub/unicode.pf2"
fi


if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=5
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=5
  fi
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-437b1022-0dc2-47dc-90b7-5104c8a317c7' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a4d3f2b1-fd0f-49fa-8258-7c0ca8180a14
	else
	  search --no-floppy --fs-uuid --set=root a4d3f2b1-fd0f-49fa-8258-7c0ca8180a14
	fi
	linux	/vmlinuz-3.13.0-46-generic root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff
	initrd	/initrd.img-3.13.0-46-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-437b1022-0dc2-47dc-90b7-5104c8a317c7' {
	menuentry 'Ubuntu, with Linux 3.13.0-46-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-46-generic-advanced-437b1022-0dc2-47dc-90b7-5104c8a317c7' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a4d3f2b1-fd0f-49fa-8258-7c0ca8180a14
		else
		  search --no-floppy --fs-uuid --set=root a4d3f2b1-fd0f-49fa-8258-7c0ca8180a14
		fi
		echo	'Loading Linux 3.13.0-46-generic ...'
		linux	/vmlinuz-3.13.0-46-generic root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/initrd.img-3.13.0-46-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-46-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-46-generic-recovery-437b1022-0dc2-47dc-90b7-5104c8a317c7' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a4d3f2b1-fd0f-49fa-8258-7c0ca8180a14
		else
		  search --no-floppy --fs-uuid --set=root a4d3f2b1-fd0f-49fa-8258-7c0ca8180a14
		fi
		echo	'Loading Linux 3.13.0-46-generic ...'
		linux	/vmlinuz-3.13.0-46-generic root=/dev/mapper/ubuntu--vg-root ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/initrd.img-3.13.0-46-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-advanced-437b1022-0dc2-47dc-90b7-5104c8a317c7' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a4d3f2b1-fd0f-49fa-8258-7c0ca8180a14
		else
		  search --no-floppy --fs-uuid --set=root a4d3f2b1-fd0f-49fa-8258-7c0ca8180a14
		fi
		echo	'Loading Linux 3.13.0-43-generic ...'
		linux	/vmlinuz-3.13.0-43-generic root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/initrd.img-3.13.0-43-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-43-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-recovery-437b1022-0dc2-47dc-90b7-5104c8a317c7' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a4d3f2b1-fd0f-49fa-8258-7c0ca8180a14
		else
		  search --no-floppy --fs-uuid --set=root a4d3f2b1-fd0f-49fa-8258-7c0ca8180a14
		fi
		echo	'Loading Linux 3.13.0-43-generic ...'
		linux	/vmlinuz-3.13.0-43-generic root=/dev/mapper/ubuntu--vg-root ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/initrd.img-3.13.0-43-generic
	}
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a4d3f2b1-fd0f-49fa-8258-7c0ca8180a14
	else
	  search --no-floppy --fs-uuid --set=root a4d3f2b1-fd0f-49fa-8258-7c0ca8180a14
	fi
	knetbsd	/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a4d3f2b1-fd0f-49fa-8258-7c0ca8180a14
	else
	  search --no-floppy --fs-uuid --set=root a4d3f2b1-fd0f-49fa-8258-7c0ca8180a14
	fi
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
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



```

---

### Post by Kirboosy on 2015-03-09
So I did a little bit of digging it might be related to the grubenv. Its located under [I][B]/boot/grub/grubenv 

[/B][/I]Edit that file and see if there is a **recordfail** marker in that file. 

1. There is a script I used to use called "Bootinfoscript" it was a open source project that gathered the boot info and made it a simple to read printout. However I'm not 100% sure if it works anymore because its become a stale/dead project
2. There is nothing in your grub.cfg that stands out and would cause issues.
3.Keeping 2 kernels is a safety. Just in case for whatever reason you can't use the newest kernel you can always fall back to the older kernel. You could most likely get away with running the latests/active kernel but if anything were to go wrong with your system you would be out of luck.

Hope that helps!
~Caboose

---

### Post by Cavsfan on 2015-03-09
What does your system look like in gparted. You may have to install it if you haven't already.

[ATTACH=CONFIG]260541[/ATTACH]

---

### Post by peridian on 2015-03-10
> **Caboose885 said:**
> So I did a little bit of digging it might be related to the grubenv. Its located under [I][B]/boot/grub/grubenv 

[/B][/I]Edit that file and see if there is a **recordfail** marker in that file. 


Thank you, you managed to point me in the right direction.  Along with [this]("http://ubuntuforums.org/archive/index.php/t-1827348.html") post from these forums, I found out about the following:

First check for recordfail by using the following command:

```

sudo grub-editenv list

```

If there is no output, then it's fine.  If it shows the recordfail=1 line, then do the following:

```

sudo grub-editenv - unset recordfail

```

Note that the dash with spaces either side is on purpose.

At some point my GRUB must have failed and although the recordfail is supposed to clear automatically, this one got stuck.  I have a server that only half an hour ago started suffering the same problem, but in its case the flag cleared automatically after I physically rebooted it.

Thanks again.

Regards,
Rob.

---

