---
title: "Grub 2 errors"
date: 2015-05-22
forum: General Help
---

### Post by pfeiffep on 2015-05-22
I've re-installed Grub 2 using sudo grub-install /dev/sdb with no errors, however after issuing sudo update-grub I receive this error
```
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 139
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done
``` I'm not certain how to discover which file has an error - /etc/default/grub doesn't have 139 lines
```
ls -l /etc/grub.d/
total 84
-rwxr-xr-x 1 root root  9424 Apr  1  2014 00_header
-rwxr-xr-x 1 root root  6058 Mar 31  2014 05_debian_theme
-rwxr-xr-x 1 root root   694 May 22 15:57 10_linux_proxy
-rwxr-xr-x 1 root root   384 May 22 15:57 40_custom_proxy
-rwxr-xr-x 1 root root  1210 May 22 15:57 41_linux_proxy
-rwxr-xr-x 1 root root  3022 Sep 23  2013 42_grml
-rwxr-xr-x 1 root root 10412 Apr  1  2014 43_linux_xen
-rwxr-xr-x 1 root root  2657 May 22 15:57 44_os-prober_proxy
-rwxr-xr-x 1 root root   265 May 22 15:57 45_memtest86+_proxy
-rwxr-xr-x 1 root root  1416 Apr  1  2014 46_uefi-firmware
-rwxr-xr-x 1 root root   373 May 22 15:57 47_custom_proxy
-rwxr-xr-x 1 root root   216 Apr  1  2014 48_custom
drwxr-xr-x 4 root root  4096 Mar 22 20:13 backup
drwxr-xr-x 2 root root  4096 Mar 22 20:13 bin
drwxr-xr-x 2 root root  4096 May 22 15:57 proxifiedScripts
-rw-r--r-- 1 root root   483 Apr  1  2014 README
```

Suggestions?

---

### Post by Bashing-om on 2015-05-22
pfeiffep; Sure !
> 
Suggestions?


Starting from the advisory, and then work back to the actual error.
We see:
> 
Syntax error at line 139
Syntax errors are detected in generated GRUB config file.

That " generated GRUB config file" is in fact -> "/boot/grub/grub.cfg".
In that file is the advisement of where the stanza is generated from.
So looking at the header in the stanza that contains line 139 one can look at the file that generated that stanza.
```

cat -n boot/grub/grub.cfg

```

[INDENT][INDENT]and ahunt'n we will go
[/INDENT][/INDENT]

---

### Post by oldfred on 2015-05-22
It may have saved the file with the error as /boot/grub/grub.cfg.new.
As with the errors it will not overwrite the older grub.cfg.

---

### Post by Bashing-om on 2015-05-22
@oldfred; Thanks; ^^

As I live and learn .

[INDENT][INDENT]as the master speaks
[/INDENT][/INDENT]

---

### Post by pfeiffep on 2015-05-22
Thanks you both, but I'm not entirely certain how to interpret what I found
   ```
grub.cfg  

 

 137    ### BEGIN /etc/grub.d/40_custom_proxy ### 
  138    menuentry " Ubuntu 14.04 LTS" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-fbf29380-b1fc-4c8a-bc03-6365d5803394' { 
  139        set root='(hd1,1)' 
  140        search --no-floppy --fs-uuid --set=root fbf29380-b1fc-4c8a-bc03-6365d5803394 
 


grub.cfg.new

 

    137    ### BEGIN /etc/grub.d/40_custom_proxy ### 
    138    menuentry " Ubuntu 14.04 LTS" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-fbf29380-b1fc-4c8a-bc03-6365d5803394' { 
    139    } 
    140    ### END /etc/grub.d/40_custom_proxy ### 


```and how to determine where line 139 is generated. there's an obvious difference, and I'm tempted to copy grub.cfg.new to grub.cfg
I think the character  }  is missing from grub.cfg , but I don't understand      set root='(hd1,1)'

---

### Post by Bashing-om on 2015-05-22
pfeiffep; Hey;

Well :
> 
 I'm not entirely certain how to interpret what I found

We are looking for the where as of line139
the stanza starts with " /etc/grub.d/40_custom_proxy"

Ouch . Why do you feel the need to alter the default boot menu presentation ? And next is from where is this file generated ?
Is the reference UUID " fbf29380-b1fc-4c8a-bc03-6365d5803394 " valid ?
So, let's look at possible sources:
```

cat /etc/grub.d/40_custom
cat /etc/grub.d/40_custom_proxy

```
The last line of the menuentry must be } ; we be checking for that too .
The set root= line should point to the GRUB 2 /boot location ( (hdX,Y) )

verify that UUID and what the assignment is:
```

sudo blkid

```

And I too will open my mind
[INDENT][INDENT]to a learning experience
[/INDENT][/INDENT]

---

### Post by pfeiffep on 2015-05-22
Thank you for your continued help Bashing-om

[COLOR=#b22222]Why do you feel the need to alter the default boot menu presentation ?[/COLOR][INDENT]I simply wanted to append LTS to the Grub menu entry, made a mistake using grub customizer. 
[/INDENT]
[COLOR=#b22222]Is the reference UUID " fbf29380-b1fc-4c8a-bc03-6365d5803394 " valid ?[/COLOR]

[INDENT]```
/dev/sda1: LABEL="SYSTEM" UUID="18463EFA463ED868" TYPE="ntfs" 
/dev/sda2: LABEL="OS" UUID="0280107A801075FF" TYPE="ntfs" 
/dev/sda3: LABEL="HP_RECOVERY" UUID="D08E7AC68E7AA49E" TYPE="ntfs" 
**/dev/sdb1: UUID="fbf29380-b1fc-4c8a-bc03-6365d5803394" TYPE="ext4" **
/dev/sdb2: UUID="b063be96-47ba-4f20-b90d-f0a44ffd6abc" TYPE="ext4" 
/dev/sdb3: UUID="91da439c-443c-4f70-b042-ffeef1f8373f" TYPE="swap" 
/dev/sdb5: UUID="136284b2-9069-4766-a231-041ea7082a54" TYPE="ext4" 
/dev/sdb6: UUID="e8ebab9a-5398-47db-b473-97be238a8913" TYPE="ext4" 
```
[/INDENT]

[COLOR=#b22222]So, let's look at possible sources:[/COLOR]

[INDENT]```
cat /etc/grub.d/40_custom_proxy
#!/bin/sh
#THIS IS A GRUB PROXY SCRIPT
'/etc/grub.d/proxifiedScripts/custom' | /etc/grub.d/bin/grubcfg_proxy "-*
-#text
+' Ubuntu 14.04'~5e732a1878be2342dbfeff5fe3ca5aa3~ as ' Ubuntu 14.04 LTS'
-'Ubuntu, with Linux 3.13.0-51-generic'~031bac0f6699b0751d4e2a8f5e1df8d4~
-'Ubuntu, with Linux 3.13.0-53-generic'~44993218977f9b5f61f2a47ff19420a1~
-'new'~5e732a1878be2342dbfeff5fe3ca5aa3~
```
[/INDENT]

Some of these uuid's are not valid ... so I believe I should edit /etc/grub.d/40_custom_proxy and use the correct uuid for sdb1

I don't have Linux 3.13.0-51-generic on my system anymore, and I notice that Linux 3.13.0-52-generic is missing. Should each of these files have a unique uuid? I would think that the sdb1 uuid should be listed for each one - correct?

If there's an easier method I, too, am willing to learn!

[INDENT]




[/INDENT]

---

### Post by Bashing-om on 2015-05-22
pfeiffep; Ho Kay ;

Let's consider what you want to do :
> 
I simply wanted to append LTS to the Grub menu entry, made a mistake using grub customizer.

As opposed to what you 'can' do.
You can do the simple thing by a very small edit to the existing file:
in /etc/default/grub that says
```

GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`

```
to read with whatever you want in the grub menu, but change the backticks to normal double quotation marks.

As an example I have edited the file in my OS to read
```

GRUB_DISTRIBUTOR="Xubuntu-14.04-amd64 Trusty"

```

Now if this is what you want to do, we need to undo what "grub customizer" has done before proceeding to put this change in effect.

[INDENT][INDENT]your system
[INDENT][INDENT][INDENT]your call
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2015-05-22
Grub customizer often creates new scripts rather than the relatively simple edits we can do. But since it is gui app many still prefer it.

I think all the proxy scripts are from grub customizer. Often just uninstalling it does not fully undo it. You have to fully uninstall customizer & grub2 & copy the grub folders to to backups and then do a full reinstall of grub2, so the old customizer create files are not still in grub.

---

### Post by Bashing-om on 2015-05-22
@oldfred; Whewhhh .

Am I glad you are watching. I sure would have messed this up . I had not considered the necessity to remove 'grub customizer" first.

@ pfeiffep; A word to the wise.

[INDENT][INDENT]wow
[/INDENT][/INDENT]

---

### Post by oldfred on 2015-05-22
Some have good success with grub customizer. And it  is a simple gui app. 
But some have had major issues, and cleaning it out is an issue.

The only reason I know about grub.cfg.new, is that with my original grub2, I added a 40_custom to boot other installs, some older. I now only do clean installs, but copied 40_custom over. And a newer version of grub2 parsed grub.cfg better and noticed my 40_custom had a missing }. I had not  noticed that an entry for an old install was never there before. :)

---

### Post by pfeiffep on 2015-05-22
Thanks to both of you once again ... I think I followed the instructions correctly, I can now update-grub without issues. When I boot there's no entry for Ubuntu 14.04, simply an advanced entry sub menu that enables correct kernel booting. I certainly can live this way, but I'd like to have the"default" 14.04 entry in place....suggestions?
```
 sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-53-generic
Found initrd image: /boot/initrd.img-3.13.0-53-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-53-generic
Found initrd image: /boot/initrd.img-3.13.0-53-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda3
Found Ubuntu 15.04 (15.04) on /dev/sdb5
Found Ubuntu 14.10 (14.10) on /dev/sdb6
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

### Post by Bashing-om on 2015-05-22
pfeiffep; Welp;

Now that just is not right;

While I am think'n, how about labeling your partitions;
Not only do they display in terminal, they display as labelled in Ubuntu, which makes it a lot easier than perhaps displaying a UUID. 
Here is the command to label your partitions: 
```

sudo tune2fs -L "Precise" /dev/sda5 
sudo tune2fs -L "Quantal" /dev/sda6 
sudo tune2fs -L "Raring" /dev/sda8 

```
where again what is inside the quotes can be what ever you want.
for reference mine:
```

sysop@1404mini:~$ sudo blkid
[sudo] password for sysop: 
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdc1: LABEL="1404std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdc2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdc3: LABEL="ubie1504" UUID="2ec4733f-db40-4db0-aef8-5c54e54085ab" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
sysop@1404mini:~$ 

```

EDIT: But I would not label the NTFS partitions from ubuntu, not sure how Windows would take that !

got to be a way
[INDENT][INDENT]to make grub right
[/INDENT][/INDENT]

---

### Post by pfeiffep on 2015-05-22
I gave labeling a try ... my labels showed up at the end of the live vs the way yours did. the command I used ... sudo tune2fs -L "Home" /dev/sdb2
```
/dev/sda1: LABEL="SYSTEM" UUID="18463EFA463ED868" TYPE="ntfs" 
/dev/sda2: LABEL="OS" UUID="0280107A801075FF" TYPE="ntfs" 
/dev/sda3: LABEL="HP_RECOVERY" UUID="D08E7AC68E7AA49E" TYPE="ntfs" 
/dev/sdb1: UUID="fbf29380-b1fc-4c8a-bc03-6365d5803394" TYPE="ext4" LABEL="14.04 LTS" 
/dev/sdb2: UUID="b063be96-47ba-4f20-b90d-f0a44ffd6abc" TYPE="ext4" LABEL="Home" 
/dev/sdb3: UUID="91da439c-443c-4f70-b042-ffeef1f8373f" TYPE="swap" 
/dev/sdb5: UUID="136284b2-9069-4766-a231-041ea7082a54" TYPE="ext4" 
/dev/sdb6: UUID="e8ebab9a-5398-47db-b473-97be238a8913" TYPE="ext4" 
``` Not a big deal, but I expected very similar results as you provided. Maybe I misunderstood - did you actually insert the entire line as ```
LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4"
```to obtain the order?

---

### Post by Bashing-om on 2015-05-22
pfeiffep; Wellp;

Labeling :
the label is what ever you place inside the quote marks for the target partition.
Let's say that in your case partition sdb6 contains the release 15.04 install, and the name you choose is 'ubie1504';
The command to make that happen:
```

sudo tune2fs -L "ubie1504" /dev/sdb6

```

see:
```

man tune2fs

``` for more than you want to know about this command ( or any other command for that matter).

Now for grub:
My code-fu is failing me; but let's see what we can fumble through.
Post back the outputs:
```

cat /etc/default/grub
cat /boot/grub/grub.cfg
cat /etc/grub.d/10_linux

```
and see if we can finger out why there is no default kernel boot entry in the menu .

[INDENT][INDENT]be one of them times
[INDENT][INDENT][INDENT]i just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pfeiffep on 2015-05-22
Thanks for continued help - this is beyond me now....
The labels worked for me, just that they were placed at the end of the line, not as yours were ... no biggie here's the output requested.  Note that /etc/grub.d/10_linux didn't exist so I did the next best thing and provided /etc/grub.d/41_linux_proxy
```
cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="9"
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
```

```
cat /boot/grub/grub.cfg
# DO NOT EDIT THIS FILE
## It is automatically generated by grub-mkconfig using templates
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
insmod ext2
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1 --hint='hd1,msdos1'  fbf29380-b1fc-4c8a-bc03-6365d5803394
else
  search --no-floppy --fs-uuid --set=root fbf29380-b1fc-4c8a-bc03-6365d5803394
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
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=9
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=9
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
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

### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/41_linux_proxy ###
submenu "Advanced options for Ubuntu"{
menuentry "Ubuntu, with Linux 3.13.0-53-generic" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-generic-advanced-fbf29380-b1fc-4c8a-bc03-6365d5803394' {
                recordfail
                load_video
                gfxmode $linux_gfx_mode
                insmod gzio
                insmod part_msdos
                insmod ext2
                set root='hd1,msdos1'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1 --hint='hd1,msdos1'  fbf29380-b1fc-4c8a-bc03-6365d5803394
                else
                  search --no-floppy --fs-uuid --set=root fbf29380-b1fc-4c8a-bc03-6365d580
3394
                fi
                echo    'Loading Linux 3.13.0-53-generic ...'
                linux   /boot/vmlinuz-3.13.0-53-generic root=UUID=fbf29380-b1fc-4c8a-bc03-6365d5803394 ro  quiet splash $vt_handoff
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-3.13.0-53-generic
}
menuentry "Ubuntu, with Linux 3.13.0-53-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-generic-recovery-fbf29380-b1fc-4c8a-bc03-6365d5803394' {
                recordfail
                load_video
                insmod gzio
                insmod part_msdos
                insmod ext2
                set root='hd1,msdos1'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1 --hint='hd1,msdos1'  fbf29380-b1fc-4c8a-bc03-6365d5803394
                else
                  search --no-floppy --fs-uuid --set=root fbf29380-b1fc-4c8a-bc03-6365d5803394
                fi
                echo    'Loading Linux 3.13.0-53-generic ...'
                linux   /boot/vmlinuz-3.13.0-53-generic root=UUID=fbf29380-b1fc-4c8a-bc03-6365d5803394 ro recovery nomodeset 
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-3.13.0-53-generic
}
menuentry "Ubuntu, with Linux 3.13.0-52-generic" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-advanced-fbf29380-b1fc-4c8a-bc03-6365d5803394' {
                recordfail
                load_video
                gfxmode $linux_gfx_mode
                insmod gzio
                insmod part_msdos
                insmod ext2
                set root='hd1,msdos1'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1 --hint='hd1,msdos1'  fbf29380-b1fc-4c8a-bc03-6365d5803394
                else
                  search --no-floppy --fs-uuid --set=root fbf29380-b1fc-4c8a-bc03-6365d5803394
                fi
                echo    'Loading Linux 3.13.0-52-generic ...'
                linux   /boot/vmlinuz-3.13.0-52-generic root=UUID=fbf29380-b1fc-4c8a-bc03-6365d5803394 ro  quiet splash $vt_handoff
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-3.13.0-52-generic
}
menuentry "Ubuntu, with Linux 3.13.0-52-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-recovery-fbf29380-b1fc-4c8a-bc03-6365d5803394' {
                recordfail
                load_video
                insmod gzio
                insmod part_msdos
                insmod ext2
                set root='hd1,msdos1'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1 --hint='hd1,msdos1'  fbf29380-b1fc-4c8a-bc03-6365d5803394
                else
                  search --no-floppy --fs-uuid --set=root fbf29380-b1fc-4c8a-bc03-6365d5803394
                fi
                echo    'Loading Linux 3.13.0-52-generic ...'
                linux   /boot/vmlinuz-3.13.0-52-generic root=UUID=fbf29380-b1fc-4c8a-bc03-6365d5803394 ro recovery nomodeset 
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-3.13.0-52-generic
}
menuentry "Ubuntu, with Linux 3.13.0-51-generic" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-51-generic-advanced-fbf29380-b1fc-4c8a-bc03-6365d5803394' {
                recordfail
                load_video
                gfxmode $linux_gfx_mode
                insmod gzio
                insmod part_msdos
                insmod ext2
                set root='hd1,msdos1'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1 --hint='hd1,msdos1'  fbf29380-b1fc-4c8a-bc03-6365d5803394
                else
                  search --no-floppy --fs-uuid --set=root fbf29380-b1fc-4c8a-bc03-6365d5803394
                fi
                echo    'Loading Linux 3.13.0-51-generic ...'
                linux   /boot/vmlinuz-3.13.0-51-generic root=UUID=fbf29380-b1fc-4c8a-bc03-6365d5803394 ro  quiet splash $vt_handoff
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-3.13.0-51-generic
}
}
### END /etc/grub.d/41_linux_proxy ###

### BEGIN /etc/grub.d/43_linux_xen ###

### END /etc/grub.d/43_linux_xen ###

### BEGIN /etc/grub.d/44_os-prober_proxy ###


set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
menuentry "Ubuntu Vivid Vervet (development branch) (15.04) (on /dev/sdb5)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-136284b2-9069-4766-a231-041ea7082a54' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5 --hint='hd1,msdos5'  136284b2-9069-4766-a231-041ea7082a54
        else
          search --no-floppy --fs-uuid --set=root 136284b2-9069-4766-a231-041ea7082a54
        fi
        linux /boot/vmlinuz-3.19.0-16-generic root=UUID=136284b2-9069-4766-a231-041ea7082a54 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.19.0-16-generic
}
submenu "Advanced options for Ubuntu 15.04 (15.04) (on /dev/sdb5)"{
menuentry "Ubuntu, with Linux 3.19.0-16-generic (on /dev/sdb5)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic--136284b2-9069-4766-a231-041ea7082a54' {
                insmod part_msdos
                insmod ext2
                set root='hd1,msdos5'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5 --hint='hd1,msdos5'  136284b2-9069-4766-a231-041ea7082a54
                else
                  search --no-floppy --fs-uuid --set=root 136284b2-9069-4766-a231-041ea7082a54
                fi
                linux /boot/vmlinuz-3.19.0-16-generic root=UUID=136284b2-9069-4766-a231-041ea7082a54 ro quiet splash $vt_handoff
                initrd /boot/initrd.img-3.19.0-16-generic
}
menuentry "Ubuntu, with Linux 3.19.0-16-generic (upstart) (on /dev/sdb5)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic--136284b2-9069-4766-a231-041ea7082a54' {
                insmod part_msdos
                insmod ext2
                set root='hd1,msdos5'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5 --hint='hd1,msdos5'  136284b2-9069-4766-a231-041ea7082a54
                else
                  search --no-floppy --fs-uuid --set=root 136284b2-9069-4766-a231-041ea7082a54
                fi
                linux /boot/vmlinuz-3.19.0-16-generic root=UUID=136284b2-9069-4766-a231-041ea7082a54 ro quiet splash $vt_handoff init=/sbin/upstart
                initrd /boot/initrd.img-3.19.0-16-generic
}
menuentry "Ubuntu, with Linux 3.19.0-16-generic (recovery mode) (on /dev/sdb5)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic-root=UUID=136284b2-9069-4766-a231-041ea7082a54 ro recovery nomodeset-136284b2-9069-4766-a231-041ea7082a54' {
                insmod part_msdos
                insmod ext2
                set root='hd1,msdos5'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5 --hint='hd1,msdos5'  136284b2-9069-4766-a231-041ea7082a54
                else
                  search --no-floppy --fs-uuid --set=root 136284b2-9069-4766-a231-041ea7082a54
                fi
                linux /boot/vmlinuz-3.19.0-16-generic root=UUID=136284b2-9069-4766-a231-041ea7082a54 ro recovery nomodeset
                initrd /boot/initrd.img-3.19.0-16-generic
}
menuentry "Ubuntu, with Linux 3.19.0-10-generic (on /dev/sdb5)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-10-generic--136284b2-9069-4766-a231-041ea7082a54' {
                insmod part_msdos
                insmod ext2
                set root='hd1,msdos5'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5 --hint='hd1,msdos5'  136284b2-9069-4766-a231-041ea7082a54
                else
                  search --no-floppy --fs-uuid --set=root 136284b2-9069-4766-a231-041ea7082a54
                fi
                linux /boot/vmlinuz-3.19.0-10-generic root=UUID=136284b2-9069-4766-a231-041ea7082a54 ro quiet splash $vt_handoff
                initrd /boot/initrd.img-3.19.0-10-generic
}
}
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os $menuentry_id_option 'osprober-chain-18463EFA463ED868' {
        insmod part_msdos
        insmod ntfs
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd0,msdos1'  18463EFA463ED868
        else
          search --no-floppy --fs-uuid --set=root 18463EFA463ED868
        fi
        parttool ${root} hidden-
        chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os $menuentry_id_option 'osprober-chain-0280107A801075FF' {
        insmod part_msdos
        insmod ntfs
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  0280107A801075FF
        else
          search --no-floppy --fs-uuid --set=root 0280107A801075FF
        fi
        parttool ${root} hidden-        chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os $menuentry_id_option 'osprober-chain-D08E7AC68E7AA49E' {
        insmod part_msdos
        insmod ntfs
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3 --hint='hd0,msdos3'  D08E7AC68E7AA49E
        else
          search --no-floppy --fs-uuid --set=root D08E7AC68E7AA49E
        fi
        parttool ${root} hidden-
        drivemap -s (hd0) ${root}
        chainloader +1
}
submenu "Advanced options for Ubuntu Vivid Vervet (development branch) (15.04) (on /dev/sdb5)"{
menuentry "Ubuntu (on /dev/sdb5)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic--136284b2-9069-4766-a231-041ea7082a54' {
                insmod part_msdos
                insmod ext2
                set root='hd1,msdos5'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5 --hint='hd1,msdos5'  136284b2-9069-4766-a231-041ea7082a54
                else
                  search --no-floppy --fs-uuid --set=root 136284b2-9069-4766-a231-041ea7082a54
                fi
                linux /boot/vmlinuz-3.19.0-16-generic root=UUID=136284b2-9069-4766-a231-041ea7082a54 ro quiet splash $vt_handoff
                initrd /boot/initrd.img-3.19.0-16-generic
}
menuentry "Ubuntu, with Linux 3.19.0-10-generic (on /dev/sdb5)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic--136284b2-9069-4766-a231-041ea7082a54' {
                insmod part_msdos
                insmod ext2
                set root='hd1,msdos5'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5 --hint='hd1,msdos5'  136284b2-9069-4766-a231-041ea7082a54
                else
                  search --no-floppy --fs-uuid --set=root 136284b2-9069-4766-a231-041ea7082a54
                fi
                linux /boot/vmlinuz-3.19.0-16-generic root=UUID=136284b2-9069-4766-a231-041ea7082a54 ro quiet splash $vt_handoff
                initrd /boot/initrd.img-3.19.0-16-generic
}
menuentry "Ubuntu, with Linux 3.19.0-10-generic (upstart) (on /dev/sdb5)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-10-generic--136284b2-9069-4766-a231-041ea7082a54' {
                insmod part_msdos
                insmod ext2
                set root='hd1,msdos5'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5 --hint='hd1,msdos5'  136284b2-9069-4766-a231-041ea7082a54
                else
                  search --no-floppy --fs-uuid --set=root 136284b2-9069-4766-a231-041ea7082a54
                fi
                linux /boot/vmlinuz-3.19.0-10-generic root=UUID=136284b2-9069-4766-a231-041ea7082a54 ro quiet splash $vt_handoff init=/sbin/upstart
                initrd /boot/initrd.img-3.19.0-10-generic
}
menuentry "Ubuntu, with Linux 3.19.0-10-generic (recovery mode) (on /dev/sdb5)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-10-generic-root=UUID=136284b2-9069-4766-a231-041ea7082a54 ro recovery nomodeset-136284b2-9069-4766-a231-041ea7082a54' {
                insmod part_msdos
                insmod ext2
                set root='hd1,msdos5'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5 --hint='hd1,msdos5'  136284b2-9069-4766-a231-041ea7082a54
                else
                  search --no-floppy --fs-uuid --set=root 136284b2-9069-4766-a231-041ea7082a54
                fi
                linux /boot/vmlinuz-3.19.0-10-generic root=UUID=136284b2-9069-4766-a231-041ea7082a54 ro recovery nomodeset
                initrd /boot/initrd.img-3.19.0-10-generic
}
}
menuentry "Gmome 14.10 (14.10) (on /dev/sdb6)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-e8ebab9a-5398-47db-b473-97be238a8913' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6 --hint='hd1,msdos6'  e8ebab9a-5398-47db-b473-97be238a8913
        else
          search --no-floppy --fs-uuid --set=root e8ebab9a-5398-47db-b473-97be238a8913
        fi
        linux /boot/vmlinuz-3.16.0-23-generic root=UUID=e8ebab9a-5398-47db-b473-97be238a8913 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.16.0-23-generic
}
submenu "Advanced options for Ubuntu 14.10 (14.10) (on /dev/sdb6)"{
menuentry "Ubuntu (on /dev/sdb6)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.16.0-23-generic--e8ebab9a-5398-47db-b473-97be238a8913' {
                insmod part_msdos
                insmod ext2
                set root='hd1,msdos6'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6 --hint='hd1,msdos6'  e8ebab9a-5398-47db-b473-97be238a8913
                else
                  search --no-floppy --fs-uuid --set=root e8ebab9a-5398-47db-b473-97be238a8913
                fi
                linux /boot/vmlinuz-3.16.0-23-generic root=UUID=e8ebab9a-5398-47db-b473-97be238a8913 ro quiet splash $vt_handoff
                initrd /boot/initrd.img-3.16.0-23-generic
}
menuentry "Ubuntu, with Linux 3.16.0-23-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.16.0-23-generic--e8ebab9a-5398-47db-b473-97be238a8913' {
                insmod part_msdos
                insmod ext2
                set root='hd1,msdos6'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6 --hint='hd1,msdos6'  e8ebab9a-5398-47db-b473-97be238a8913
                else
                  search --no-floppy --fs-uuid --set=root e8ebab9a-5398-47db-b473-97be238a8913
                fi
                linux /boot/vmlinuz-3.16.0-23-generic root=UUID=e8ebab9a-5398-47db-b473-97be238a8913 ro quiet splash $vt_handoff
                initrd /boot/initrd.img-3.16.0-23-generic
}
menuentry "Ubuntu, with Linux 3.16.0-23-generic (recovery mode) (on /dev/sdb6)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.16.0-23-generic-root=UUID=e8ebab9a-5398-47db-b473-97be238a8913 ro recovery nomodeset-e8ebab9a-5398-47db-b473-97be238a8913' {
                insmod part_msdos
                insmod ext2
                set root='hd1,msdos6'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6 --hint='hd1,msdos6'  e8ebab9a-5398-47db-b473-97be238a8913
                else
                  search --no-floppy --fs-uuid --set=root e8ebab9a-5398-47db-b473-97be238a8913
                fi
                linux /boot/vmlinuz-3.16.0-23-generic root=UUID=e8ebab9a-5398-47db-b473-97be238a8913 ro recovery nomodeset
                initrd /boot/initrd.img-3.16.0-23-generic
}
}
### END /etc/grub.d/44_os-prober_proxy ###

### BEGIN /etc/grub.d/45_memtest86+_proxy ###
menuentry "Memory test (memtest86+)" {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1 --hint='hd1,msdos1'  fbf29380-b1fc-4c8a-bc03-6365d5803394
        else
          search --no-floppy --fs-uuid --set=root fbf29380-b1fc-4c8a-bc03-6365d5803394
        fi
        knetbsd /boot/memtest86+.elf
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1 --hint='hd1,msdos1'  fbf29380-b1fc-4c8a-bc03-6365d5803394
        else
          search --no-floppy --fs-uuid --set=root fbf29380-b1fc-4c8a-bc03-6365d5803394
        fi
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
                fi
                linux /boot/vmlinuz-3.16.0-23-generic root=UUID=e8ebab9a-5398-47db-b473-97be238a8913 ro recovery nomodeset
                initrd /boot/initrd.img-3.16.0-23-generic
}
}
### END /etc/grub.d/44_os-prober_proxy ###

### BEGIN /etc/grub.d/45_memtest86+_proxy ###
menuentry "Memory test (memtest86+)" {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1 --hint='hd1,msdos1'  fbf29380-b1fc-4c8a-bc03-6365d5803394
        else
          search --no-floppy --fs-uuid --set=root fbf29380-b1fc-4c8a-bc03-6365d5803394
        fi
        knetbsd /boot/memtest86+.elf
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1 --hint='hd1,msdos1'  fbf29380-b1fc-4c8a-bc03-6365d5803394
        else
          search --no-floppy --fs-uuid --set=root fbf29380-b1fc-4c8a-bc03-6365d5803394
        fi
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/45_memtest86+_proxy ###

### BEGIN /etc/grub.d/46_uefi-firmware ###
### END /etc/grub.d/46_uefi-firmware ###

```

```
 cat: /etc/grub.d/10_linux: No such file or directory
```

```

cat /etc/grub.d/41_linux_proxy
#!/bin/sh
#THIS IS A GRUB PROXY SCRIPT
sh -c 'echo "### BEGIN /etc/grub.d/proxifiedScripts/linux ###";
"/etc/grub.d/proxifiedScripts/linux";
echo "### END /etc/grub.d/proxifiedScripts/linux ###";
echo "### BEGIN /etc/grub.d/proxifiedScripts/custom ###";
"/etc/grub.d/proxifiedScripts/custom";
echo "### END /etc/grub.d/proxifiedScripts/custom ###";' | /etc/grub.d/bin/grubcfg_proxy "-*
-#text
-'Ubuntu'~38e95587dd21ca1be1f3d537f70b9306~
+'SUBMENU' as 'Advanced options for Ubuntu'{+'Advanced options for Ubuntu'/*, +'Ubuntu, with Linux 3.13.0-53-generic'~44993218977f9b5f61f2a47ff19420a1~ from '/etc/grub.d/proxifiedScripts/custom', -'Advanced options for Ubuntu'/'Ubuntu, with Linux 3.13.0-53-generic'~44993218977f9b5f61f2a47ff19420a1~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 3.13.0-53-generic (recovery mode)'~c1c8b135adf9be6128abf8dc695c4094~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 3.13.0-52-generic'~d63b71ea9fe7efd603ba984388ee104e~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 3.13.0-52-generic (recovery mode)'~1b23240005faa7e3041a71b001ef2147~, +'Ubuntu, with Linux 3.13.0-51-generic'~031bac0f6699b0751d4e2a8f5e1df8d4~ from '/etc/grub.d/proxifiedScripts/custom'}
" multi
```

---

### Post by Bashing-om on 2015-05-22
pfeiffep; UnGood;

> 
Note that /etc/grub.d/10_linux didn't exist 


As it is a standard file:
```

sysop@1404mini:~$ ls -al /etc/grub.d/10_linux 
-rwxr-xr-x 1 root root 11608 Apr 11  2014 /etc/grub.d/10_linux
sysop@1404mini:~$

```
Makes me wonder what did away with it, and how do we get it back ??

as to other 'proxy' files; thought we were going to do away with them. Have you to this time removed "grub customizer" from your system ?
----------------
I am past reliable thinkability for this session. We will pick this back up in my AM.

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by pfeiffep on 2015-05-22
I, too, am past what I can really think through .... yes I used synaptic to completely remove grub customizer and then deleted the custom files. I'll check back in the AM

---

### Post by pfeiffep on 2015-05-23
@Bashing-Om I have 3 Ubuntu systems all running 14.04 LS. If the 10_linux is a 'standard default file' I can easily copy from on machine to the deficient one ... 

I edited the grub file on my working Dell laptop to change the name presented on boot - the name did change, but so did the grub boot screen color to a royal blue. It's obvious that there's more complexity to the grub system of booting than I comprehend. I really don't care about the color, I just mention it to point out my limits.

I await your guidance

---

### Post by oldfred on 2015-05-23
Post this:
sudo ls -l /etc/grub.d

If you copy a file make sure it is exactly the same version of grub. Probably better to just reinstall grub. You can move all of /etc/grub.d to a backup and do a full new reinstall of grub.

       # HOWTO: Purge and Reinstall Grub 2 from the live-CD/DVD/USB - drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

   # purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by Bashing-om on 2015-05-23
pfeiffep; Morning;


Pay attention to oldfred's last . Yes !

Yeah, grub is complex and a lot goes on " under the hood" .
This little line - GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`" - does a lot. Changing it does effect the splash image . Believe me, it continues to be an endeavor to learn what file does what and why. Booting up is a fascinating process.

It is my thought also to purge grub and re-install; depending on what files are present in the grub.d directory.
Let's look:
```

ls -l /etc/grub.d

``` to see what has changed from defaults.

Booting; there can be but one controlling operating system. Which one do you want it to be of the 3 that are installed ? ( highly suggest/recommend that it be 14.04 )
```

sudo blkid
cat /etc/fstab

```
So that we are sure of where to direct the (RE-)install of grub; in that event.

[INDENT][INDENT]it ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by pfeiffep on 2015-05-23
@oldfred Since I have 2 internal hard drives 1 SSD for windows, and 1 HDD for Linux I really do NOT want Grub on my SSD. So if I opt to follow your guidance does it matter if I change the destination from  /dev/sda to /dev/sdb?
Secondarily, how do I verify grub's version? and are there hidden traps in adding the appropriate file?  edited info...Having bios choose the boot drive avoided a nasty problem with Win 7 updates.

@Bashing-om I will provide the requested info once I get on the machine.

Thank you both for your continued time, patience, and guidance.

---

### Post by Bashing-om on 2015-05-23
pfeiffep; K

We intend to leave 'sda' - the NTFS drive - alone .. install ubuntu's grub to 'sdb'.
Cheap insurance to verify that the drive designations have not changed when booting the liveDVD(USB) to effect the reinstall is to run:
```

sudo fdisk -lu

```
to know for sure that 'sdb' remains as the target to install grub to.

That said I have had real good success to purge/re-install grub from the install; but, there are advisories that this sometimes does fail.

it's 'buntu
[INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT]

---

### Post by oldfred on 2015-05-23
If you can boot into Ubuntu, you should be able to do the purge & reinstall. 
But just in case make sure you have working live installer to make grub repairs. While grub is uninstalled and if then reinstall does not work, you may not be able to reboot.
Do make sure to reinstall grub to sdb, not sda as long as sdb is the Linux drive.

---

### Post by pfeiffep on 2015-05-23
Thanks again to both of you!...I have 100% confidence in the fact the grub is installed on /dev/sdb, because when I select /dev/sda (the SSD) only windows boots, there is no mention of Linux. 

So I'm assuming that creating the missing file is NOT a good idea and may make things worse. I don't want that since this is an operating system as it boots 3 different Ubuntu installs.

```
ls -l /etc/grub.d
total 68
-rwxr-xr-x 1 root root  9424 Apr  1  2014 00_header
-rwxr-xr-x 1 root root  6058 Mar 31  2014 05_debian_theme
-rwxr-xr-x 1 root root   694 May 22 15:57 10_linux_proxy
-rwxr-xr-x 1 root root  1210 May 22 15:57 41_linux_proxy
-rwxr-xr-x 1 root root 10412 Apr  1  2014 43_linux_xen
-rwxr-xr-x 1 root root  2657 May 22 15:57 44_os-prober_proxy
-rwxr-xr-x 1 root root   265 May 22 15:57 45_memtest86+_proxy
-rwxr-xr-x 1 root root  1416 Apr  1  2014 46_uefi-firmware
drwxr-xr-x 4 root root  4096 May 22 20:01 backup
drwxr-xr-x 2 root root  4096 Mar 22 20:13 bin
drwxr-xr-x 2 root root  4096 May 22 15:57 proxifiedScripts
-rw-r--r-- 1 root root   483 Apr  1  2014 README
```

Note that the labels moved to where you showed yours AFTER a reboot
```
sudo blkid
/dev/sda1: LABEL="SYSTEM" UUID="18463EFA463ED868" TYPE="ntfs" 
/dev/sda2: LABEL="OS" UUID="0280107A801075FF" TYPE="ntfs" 
/dev/sda3: LABEL="HP_RECOVERY" UUID="D08E7AC68E7AA49E" TYPE="ntfs" 
/dev/sdb1: LABEL="14.04 LTS" UUID="fbf29380-b1fc-4c8a-bc03-6365d5803394" TYPE="ext4" 
/dev/sdb2: LABEL="Home" UUID="b063be96-47ba-4f20-b90d-f0a44ffd6abc" TYPE="ext4" 
/dev/sdb3: UUID="91da439c-443c-4f70-b042-ffeef1f8373f" TYPE="swap" 
/dev/sdb5: LABEL="15.04" UUID="136284b2-9069-4766-a231-041ea7082a54" TYPE="ext4" 
/dev/sdb6: LABEL="Gnome" UUID="e8ebab9a-5398-47db-b473-97be238a8913" TYPE="ext4" 
```

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=fbf29380-b1fc-4c8a-bc03-6365d5803394 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=b063be96-47ba-4f20-b90d-f0a44ffd6abc /home           ext4    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=91da439c-443c-4f70-b042-ffeef1f8373f none            swap    sw              0       0
```

---

### Post by oldfred on 2015-05-23
Everything with proxy in the name is from grub customizer.

You may have original scripts in the folder backup, not sure what all the folders are as standard install does not have any folders, just all the files/scripts. You may be able to restore those, but I think a reinstall may be better.

I might backup current. /etc/grub.d and delete it, just before new install of grub. Then if grub works delete the backup.

---

### Post by Bashing-om on 2015-05-23
pfeiffep; Welp'

While I didther about the best course of action:
The file system looks good and is properly identified - oh joy

Grub for booting - Oh boy
My files for grub:
```

sysop@1404mini:~$ ls -l /etc/grub.d
total 116
-rwxr-xr-x 1 root root  9424 Apr 11  2014 00_header
-rwxr-xr-x 1 root root  6058 Apr 10  2014 05_debian_theme
-rw-r--r-- 1 root root  6071 May 30  2013 05_debian_theme-orig
-rw-r--r-- 1 root root  6071 May 30  2013 05_debian_theme-orig~
-rw-r--r-- 1 root root  1091 Dec 22  2013 06_custom
-rw-r--r-- 1 root root  1093 Dec 22  2013 06_custom~
-rwxr-xr-x 1 root root 11608 Apr 11  2014 10_linux
-rwxr-xr-x 1 root root 10412 Apr 11  2014 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr 11  2014 30_os-prober
-rw-r--r-- 1 root root 10976 May 29  2013 30_os-prober-orig
-rwxr-xr-x 1 root root  1416 Apr 11  2014 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 23  2013 40_custom
-rw-r--r-- 1 root root   214 May 27  2013 40_custom-orig
-rwxr-xr-x 1 root root   216 Oct 23  2013 41_custom
-rw-r--r-- 1 root root   483 Oct 23  2013 README
sysop@1404mini:~$

```
Let's see if 'grub customizer" did the responsible thing and made backups:
post back the outputs of:
```

ls -l /etc/grub.d/backup
ls -l /etc/grub.d/proxifiedScripts/

```

Pending what we find in these directories, I am the more comfortable to purge/(re-)install grub, rather than try and fix all those files.

[INDENT][INDENT]making progress
[INDENT][INDENT][INDENT]even at 2 steps back
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pfeiffep on 2015-05-23
```
ls -l /etc/grub.d/backup
total 16
drwxr-xr-x 5 root root 4096 Mar 22 20:13 boot_grub
-rw-r--r-- 1 root root 1254 Mar 22 20:13 default_grub
drwxr-xr-x 2 root root 4096 Mar 22 20:13 etc_grub_d
-rw-r--r-- 1 root root  519 Mar 22 20:13 RESTORE_INSTRUCTIONS

 ls -l /etc/grub.d/proxifiedScripts/
total 32
-rwxr-xr-x 1 root root  2181 May 22 15:57 custom
-rwxr-xr-x 1 root root 11608 Apr  1  2014 linux
-rwxr-xr-x 1 root root  1992 Mar 12  2014 memtest86+
-rwxr-xr-x 1 root root 11692 Apr 11  2014 os-prober

```

So are the RESTORE_INSTRUCTIONS copied below valid? or shall we proceed with wiping grub out and reinstall?
>  * make sure you have root permissions (`gksu nautilus` or `sudo -s` on command line) otherwise you won't be able to copy the files
 * to fix an unbootable configuration, just copy:
     * '/etc/grub.d/backup/boot_grub' to '/boot/grub'
 * to reset the whole configuration (if it cannot be fixed by using grub customizer), also copy these files:
     * '/etc/grub.d/backup/etc_grub_d' to '/etc/grub.d'
     * '/etc/grub.d/backup/default_grub' to '/etc/default/grub'

I am so far in these weeds I'm not even sure there's ground below ;-) 

Here's the contents and I see the missing file :-()
```
ls -l /etc/grub.d/backup/etc_grub_d
total 76
-rw-r--r-- 1 root root  9424 Mar 22 20:13 00_header
-rw-r--r-- 1 root root  6058 Mar 22 20:13 05_debian_theme
-rw-r--r-- 1 root root 11608 Mar 22 20:13 10_linux
-rw-r--r-- 1 root root 10412 Mar 22 20:13 20_linux_xen
-rw-r--r-- 1 root root  1992 Mar 22 20:13 20_memtest86+
-rw-r--r-- 1 root root 11692 Mar 22 20:13 30_os-prober
-rw-r--r-- 1 root root  1416 Mar 22 20:13 30_uefi-firmware
-rw-r--r-- 1 root root   214 Mar 22 20:13 40_custom
-rw-r--r-- 1 root root   216 Mar 22 20:13 41_custom
-rw-r--r-- 1 root root   483 Mar 22 20:13 README
```

---

### Post by oldfred on 2015-05-24
Its your choice. 
Either backup & delete /etc/grub.d and do a uninstall/reinstall of grub2.
Or copy from backup all the files as it indicates with command line or Nautilus as superuser (gksu).

Either should work.

---

### Post by pfeiffep on 2015-05-24
Thank you both for your help. Either I didn't follow the instructions correctly, or my diddling with grub resulted in a completely non-bootable system. Luckily I had a boot repair disk and now I can boot Ubuntu. I hthought that I selected only /dev/sdb, but I did notice that grub was also being installed on /dev/sda- I haven't checked as yet.

I think I'll leave grub alone from now on ;-)

Added info ... Boot repair also restored Windows MBR, no grub on /dev/sda :-)

---

### Post by Bashing-om on 2015-05-24
pfeiffep; Yuk;

Chances are that " boot repair disk " went hog wild and installed the boot code to all hard drives. I do suggest that Window's boot code be (RE-)installed to that sda Windows drive. Just because I would want the Windows drive pristine and able to boot separate from the linux systems .

> 
I think I'll leave grub alone from now on 


Nawww .. if we break it, we fix it . That is the beauty of ubuntu. When you break it you get to keep the pieces and you can fix it .

Is "/etc/grub.d" all cleaned up now and back to standard ?

Lesson learned;
[INDENT][INDENT]GUI ap does not beat hands on terminal
[/INDENT][/INDENT]

---

### Post by oldfred on 2015-05-24
Glad you got it working.

I do not recommend using Boot-Repair's auto fix when you have multiple drives, as that installs grub to every MBR. But its advanced mode lets you select an operating system and which drive to install into. Then you can have each drive boot its operating system.

---

