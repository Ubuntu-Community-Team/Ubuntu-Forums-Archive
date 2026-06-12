---
title: "Grub error message on MacBook Pro"
date: 2023-04-12
forum: General Help
---

### Post by abt8102 on 2023-04-12
Hello,

I'm running Ubuntu 22.04 as the only OS on my 2009 MacBook Pro (model MBP5,2) and I followed [this guide]("https://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/#fixing-efi") to get rid of an annoying 40 second white-screen delay during boot that is caused by Apple's firmware.

As a *TL;DR* the guide involves deleting Ubuntu's */boot/efi* partition and then recreating it as a "HFS+" partition and installing grub into that because that's what the Apple firmware wants.

It fixed my original problem, but now after turning on the computer I get a black screen with the following two grub error messages:

    ```
error: no server specified.
error: no suitable video mode found.
```

This screen with these error messages remains stuck for about 10 seconds and then Grub continues to boot the system normally. I didn't have these error message before. What do they mean and how can I get rid of them?

I have never touched the */etc/default/grub* config and it only contains these lines (comments omitted):

    ```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

I already did a *sudo update-grub* and it completed normally but the error messages still remain.

---

### Post by MAFoElffen on 2023-04-13
I see that you also asked this question at: [https://askubuntu.com/questions/1463399/grub-error-message-on-boot](https://askubuntu.com/questions/1463399/grub-error-message-on-boot)

---

### Post by yancek on 2023-04-13
Have you tried the suggestion at the link below for the video error?  Not sure about the server error.  A 10 second delay seems like a minor problem using a new Ubuntu on such an old Mac.  Also, I would have mentioned the fact that you are having this problem on a Mac in the title so that it would get the attention of those members here who are familiar with them.

[URL="https://ubuntuforums.org/showthread.php?t=2409853"]https://ubuntuforums.org/showthread.php?t=2409853


[/URL]

---

### Post by abt8102 on 2023-04-13
> **yancek said:**
> Have you tried the suggestion at the link below for the video error?  Not sure about the server error.  A 10 second delay seems like a minor problem using a new Ubuntu on such an old Mac.  Also, I would have mentioned the fact that you are having this problem on a Mac in the title so that it would get the attention of those members here who are familiar with them.

[URL="https://ubuntuforums.org/showthread.php?t=2409853"]https://ubuntuforums.org/showthread.php?t=2409853


[/URL]

Thank you, I will give them a try now. I just thought it was strange because my */etc/default/grub *is exactly the same as before I followed the guide, so nothing about the grub configuration has changed really.

I should mention that when following the guide, while installing the *grub-efi-amd64 *package a blue terminal popped up asking me whether I wanted to reinstall or reconfigure grub and I selected *no *because I figured that grub was going to be reinstalled to the new HFS+ partition later anyway. I don't know much about grub or why the *grub-efi-amd64 *package was needed in the first place.

---

### Post by MAFoElffen on 2023-04-13
Actually, while editing the /etc/default/grub menu, instead change this line:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
To this
```

GRUB_CMDLINE_LINUX_DEFAULT="-- splash video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank"

```
Then change this line
```

#GRUB_GFXMODE=640x480

```
To this
```

GRUB_GFXMODE=1920x1080x24

```
Save and exit. Then do
```

sudo update-grub

```
That Mac Book Pro has nVidia  GeForce 9600M GT and Intel i915 graphics.

---

### Post by abt8102 on 2023-04-13
OK I just tried the suggestion mentioned in that thread and added
```
GRUB_TERMINAL=console
```
to */etc/default/grub* and ran a *sudo update-grub* after that.

Curiously I now again have a roughly 30 to 40 second long white-screen on boot!! Makes me wonder if my original problem wasn't caused by Apple firmware but by grub all along. I have really no idea what's going on anymore.

Commenting out the *GRUB_TERMINAL=console *restores the previous error message screen.

Addendum:

After doing some more researach and finding [this article]("https://help.ubuntu.com/community/UEFIBooting") on help.ubuntu.com about UEFI Booting, I followed their advice and added these two commands to the top of my [I]/boot/grub/grub.cfg
[/I]
```
set debug=video
insmod efi_gop

```

I now get the following messages displayed on screen for about 10 seconds:

```

video/efi_gop.c:87: GOP: found usable mode
error: no server is specified.
video/efi_gop.c:388: GOP: beeping mode 0
video/efi_gop.c:439: GOP: initialising FB @ 0xc0010000 1920x1200x32
video/efi_gop.c:516: GOP: Success

```

Normally I wouldn't care too much as the system is working otherwise, but this error screen slows down the boot process by a good 10 seconds and it won't even go away when pressing ENTER or ESCAPE.

I'm posting my /boot/grub/grub.cfg below, I think the culprit must be in there somewhere and something in there must also be causing the *error: no server is specified. *message.

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


set debug=video
insmod efi_gop


### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${initrdfail}" = 2 ]; then
   set initrdfail=
elif [ "${initrdfail}" = 1 ]; then
   set next_entry="${prev_entry}"
   set prev_entry=
   save_env prev_entry
   if [ "${next_entry}" ]; then
      set initrdfail=2
   fi
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
function initrdfail {
    if [ -n "${have_grubenv}" ]; then if [ -n "${partuuid}" ]; then
      if [ -z "${initrdfail}" ]; then
        set initrdfail=1
        if [ -n "${boot_once}" ]; then
          set prev_entry="${default}"
          save_env prev_entry
        fi
      fi
      save_env initrdfail
    fi; fi
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
insmod part_gpt
insmod ext2
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  761584f6-29e7-446a-8a8f-ea421eeacc28
else
  search --no-floppy --fs-uuid --set=root 761584f6-29e7-446a-8a8f-ea421eeacc28
fi
    font="/usr/share/grub/unicode.pf2"
fi


if loadfont $font ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=de_DE
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
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
    if [ ${grub_platform} != pc ]; then
      set linux_gfx_mode=keep
    elif hwmatch ${prefix}/gfxblacklist.txt 3; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-761584f6-29e7-446a-8a8f-ea421eeacc28' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  761584f6-29e7-446a-8a8f-ea421eeacc28
    else
      search --no-floppy --fs-uuid --set=root 761584f6-29e7-446a-8a8f-ea421eeacc28
    fi
    linux    /boot/vmlinuz-5.19.0-32-generic root=UUID=761584f6-29e7-446a-8a8f-ea421eeacc28 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-5.19.0-32-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-761584f6-29e7-446a-8a8f-ea421eeacc28' {
    menuentry 'Ubuntu, with Linux 5.19.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.19.0-32-generic-advanced-761584f6-29e7-446a-8a8f-ea421eeacc28' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  761584f6-29e7-446a-8a8f-ea421eeacc28
        else
          search --no-floppy --fs-uuid --set=root 761584f6-29e7-446a-8a8f-ea421eeacc28
        fi
        echo    'Loading Linux 5.19.0-32-generic ...'
        linux    /boot/vmlinuz-5.19.0-32-generic root=UUID=761584f6-29e7-446a-8a8f-ea421eeacc28 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-5.19.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 5.19.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.19.0-32-generic-recovery-761584f6-29e7-446a-8a8f-ea421eeacc28' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  761584f6-29e7-446a-8a8f-ea421eeacc28
        else
          search --no-floppy --fs-uuid --set=root 761584f6-29e7-446a-8a8f-ea421eeacc28
        fi
        echo    'Loading Linux 5.19.0-32-generic ...'
        linux    /boot/vmlinuz-5.19.0-32-generic root=UUID=761584f6-29e7-446a-8a8f-ea421eeacc28 ro recovery nomodeset dis_ucode_ldr 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-5.19.0-32-generic
    }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/10_linux_zfs ###
### END /etc/grub.d/10_linux_zfs ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###


### BEGIN /etc/grub.d/35_fwupd ###
### END /etc/grub.d/35_fwupd ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg
fi
### END /etc/grub.d/41_custom ###

```

---

### Post by abt8102 on 2023-04-13
@MAFoElffen
Thank you, I just tried it but I still get the same two error messages, only now in reverse order.

---

### Post by abt8102 on 2023-04-13
So adding *[COLOR=#000000][FONT=&amp]insmod efi_gop[/FONT][/COLOR]* to the top of *[COLOR=#000000]/boot/grub/grub.cfg[/COLOR] *gets rid of the **[COLOR=#000000][FONT=&amp]error: no suitable video mode found.[/FONT][/COLOR] **The other GOP messages were just because I had previously also enabled debugging with [COLOR=#000000][COLOR=#000000]set *debug=video*[/COLOR][/COLOR][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
As for the *"[COLOR=#000000][FONT=&amp]error: no server specified",[/FONT][/COLOR]* it apparently has to do with the *font loading* of all things.

 Commenting out the if-check for the *x$feature_default_font_path* and so making grub try to load the font from OS partition gets rid of the error message, however I am then back to a 30 second white screen.

Both */boot/grub/unicode.pf2* and */boot/grub/fonts/unicode.pf2* files are present in the boot partition so I don't understand what grub is complaining about. And what is the error message even supposed to mean, what kind of server would be involved in loading the font file?

---

### Post by abt8102 on 2023-04-13
The error messages appear no matter what video mode I chose. I can "overwrite" them by displaying the grub menu, then you will only see them flashing on the screen for a split second. So the actual boot delay is caused by something else.

I did some debugging by adding *echo *statements after every step in the *Ubuntu *menu entry in */boot/grub/grub.cfg* and everything runs instantly. There is just a VERY long delay after the last grub command *initrd /boot/initrd.img-5.19.0-32-generic* completes  and before the first kernel diagnostic boot messages show up.

The first boot messages I see on the screen have a timestamp of about 2 seconds so I assume that means the kernel has been running for 2 seconds. I don't know what's going on in the remaining 8 or so seconds where nothing happens and I just get a black screen.

---

### Post by MAFoElffen on 2023-04-13
Do this to try to see:
```

systemd-analyze blame

```
You had said kernel was booting and/or booted already, so, that should show each process and how long they took.

---

### Post by MAFoElffen on 2023-04-13
I just booted my Mac Book (3,1)... Let me tell you that any edits to /boot/grub/grub.cfg shouldn't do anything. As that file is built dynamically during bootup, from the files in /etc/grub.d

```

mafoelffen@Mikes-MacBook:~$ systemd-analyze
Startup finished in 6.066s (kernel) + 1min 38.418s (userspace) = 1min 44.484s 
graphical.target reached after 1min 33.600s in userspace
mafoelffen@Mikes-MacBook:~$ systemd-analyze blame
17min 3.858s apt-daily-upgrade.service
     41.207s snapd.service
     23.584s networkd-dispatcher.service
     23.520s logrotate.service
     22.989s ua-timer.service
     18.267s udisks2.service
     16.949s ModemManager.service
     16.838s snapd.apparmor.service
     16.557s apparmor.service
     16.154s NetworkManager-wait-online.service
     15.130s dev-sda7.device
      9.559s dev-loop10.device
      9.559s accounts-daemon.service
      9.454s dev-loop14.device
      9.194s dev-loop13.device
      8.558s dev-loop11.device
      8.252s dev-loop12.device
      8.228s systemd-journal-flush.service
      8.191s dev-loop18.device
      8.140s dev-loop8.device
      8.101s dev-loop1.device
      8.083s dev-loop7.device
      7.444s power-profiles-daemon.service
      7.423s polkit.service
      7.188s dev-loop2.device
      7.008s NetworkManager.service
      7.007s avahi-daemon.service
      7.005s bluetooth.service
      6.656s switcheroo-control.service
      6.634s thermald.service
      6.616s systemd-logind.service
      6.590s dev-loop4.device
      6.588s dev-loop6.device
      6.039s wpa_supplicant.service
      5.836s dev-loop0.device
      4.923s cups.service
      4.178s systemd-udevd.service
      4.064s packagekit.service
      3.591s update-notifier-download.service
      3.450s rsyslog.service
      3.327s apport.service
      3.121s lightdm.service
      3.106s plymouth-quit-wait.service
      2.937s dev-loop23.device
      2.721s snap-bare-5.mount
      2.656s snap-canonical\x2dlivepatch-146.mount
      2.557s snap-core-14784.mount
      2.370s snap-core18-2697.mount
      2.332s dev-loop20.device
      2.160s snap-core20-1822.mount
      2.159s gpu-manager.service
      2.083s grub-common.service
      1.983s snap-firefox-1993.mount
      1.964s snap-firefox-2391.mount
      1.931s upower.service
      1.901s systemd-fsck@dev-disk-by\x2duuid-70D6\x2d1701.service
      1.846s systemd-tmpfiles-setup.service
      1.754s snap-gnome\x2d3\x2d38\x2d2004-119.mount
      1.591s snap-gtk\x2dcommon\x2dthemes-1519.mount
      1.543s systemd-modules-load.service
      1.542s snap-gtk\x2dcommon\x2dthemes-1535.mount
      1.524s e2scrub_reap.service
      1.399s snap-snap\x2dstore-599.mount
      1.259s systemd-rfkill.service
      1.217s snap-snap\x2dstore-638.mount
      1.212s systemd-sysusers.service
      1.201s e2scrub_all.service
      1.087s colord.service
      1.000s systemd-random-seed.service
       968ms user@1000.service
       967ms systemd-resolved.service
       890ms systemd-tmpfiles-clean.service
       824ms systemd-backlight@backlight:intel_backlight.service
       824ms snapd.seeded.service
       794ms snap-snapd\x2ddesktop\x2dintegration-49.mount
       790ms keyboard-setup.service
       761ms systemd-journald.service
       755ms systemd-tmpfiles-setup-dev.service
       728ms systemd-udev-trigger.service
       726ms kerneloops.service
       674ms grub-initrd-fallback.service
       573ms systemd-sysctl.service
       533ms systemd-timesyncd.service
       485ms modprobe@drm.service
       479ms systemd-oomd.service
       417ms dev-loop22.device
       407ms fstrim.service
       314ms openvpn.service
       288ms systemd-remount-fs.service
       255ms dev-disk-by\x2duuid-b4d75638\x2dd0b2\x2d40f8\x2da430\x2d8ad758768>
       227ms rtkit-daemon.service
       190ms snap-gnome\x2d3\x2d38\x2d2004-137.mount
       172ms setvtrgb.service
       171ms ufw.service
       159ms boot-efi.mount
       148ms plymouth-start.service
       135ms snap-core20-1852.mount
       117ms console-setup.service
       112ms snap-canonical\x2dlivepatch-196.mount
       105ms snap-snapd\x2ddesktop\x2dintegration-57.mount
        99ms plymouth-read-write.service
        96ms dev-hugepages.mount
        92ms dev-mqueue.mount
        88ms sys-kernel-debug.mount
        85ms sys-kernel-tracing.mount
        84ms proc-sys-fs-binfmt_misc.mount
        77ms snap-core22-607.mount
17min 3.858s apt-daily-upgrade.service
     41.207s snapd.service
     23.584s networkd-dispatcher.service
     23.520s logrotate.service
     22.989s ua-timer.service
     18.267s udisks2.service
     16.949s ModemManager.service
     16.838s snapd.apparmor.service
     16.557s apparmor.service
     16.154s NetworkManager-wait-online.service
     15.130s dev-sda7.device
      9.559s dev-loop10.device
      9.559s accounts-daemon.service
      9.454s dev-loop14.device
      9.194s dev-loop13.device
      8.558s dev-loop11.device
      8.252s dev-loop12.device
      8.228s systemd-journal-flush.service
      8.191s dev-loop18.device
      8.140s dev-loop8.device
      8.101s dev-loop1.device
      8.083s dev-loop7.device

```
Mine is slower than yours. Core 2 Duo is not fast.

---

### Post by abt8102 on 2023-04-14
Yes I did look at *systemd-analyze blame* and *dmesg* but the delay I'm seeing is happening before the kernel is loaded. I found bug reports of people having similar problems [here]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1882159") and [here]("https://unix.stackexchange.com/questions/502931/debugging-boot-performance-issues-in-grub-before-kernel-logging-starts")

I added a *debug=all* to my */boot/grub/grub.cfg* and indeed grub is spamming log messages for several seconds after it supposedly handed over control to the kernel. It seemed to be stuck in a loop printing thousands of messages like this (with increasing sector addresses):

```
disk/efi/efidisk.c:593: reading 0x40 sectors at the sector 0xfefdb80 from hd0
```

The harddisk is a brand-new SSD that I only installed days ago. I had the same delay (only even longer) with the HDD that was previously installed, so I doubt there is anything wrong with the hard drive(s).

Since I don't really need Grub on this system at all, I want to get rid of the boot loader entirely and [boot the kernel directly]("https://askubuntu.com/questions/510856/how-to-boot-load-the-kernel-using-efi-stub-efistub-loader?noredirect=1&lq=1"). I hope that will fix the problem.

---

### Post by abt8102 on 2023-04-14
Hm sadly booting the kernel directly doesn't speed things up either. After powering on the MacBook I just get a white-screen for about 30 seconds and then I get the first kernel diagnostic messages.

*systemd-analyze* reports a total boot time of about 20 seconds. However measuring the time from power-on to desktop with a stopwatch shows that it takes a little less than a full minute.

```
Startup finished in 4.634s (kernel) + 15.128s (userspace) = 19.762s 
graphical.target reached after 15.117s in userspace
```

I have also previously spent days messing around with various invocations of Apple's *bless* tool and mactel's Linux equivalent *hfs-bless* but it never made any difference. I don't even know who is to blame at this point. Linux or the Apple firmware?

Anyway this has been an extremely frustrating experience and since I'm all our of ideas I guess I'll just have to accept this terribly slow boot process.

---

### Post by MAFoElffen on 2023-04-14
My MacBook (3,1) is 2007, Has Core2Duo like yours, but is 2 years older. I also have an SSD installed in mine. 

I have booted Intel version of it with similar config (So Mac and Windows types of machines)... The Core 2 Duo, is painstakingly slow to boot. I just accept that.

You cay you have a 30 second delay. Mine takes almost 2 minutes to boot. Your's is already booting faster than mine.

---

