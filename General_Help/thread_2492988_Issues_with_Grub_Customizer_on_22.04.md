---
title: "Issues with Grub Customizer on 22.04"
date: 2023-11-29
forum: General Help
---

### Post by madscientist032 on 2023-11-29
Hello all - I recently upgraded my system to 22.04 after being on 20.04 and I have a need to change my grub boot settings.

Currently, my workstation has a dual-boot situation. The main boot disk has a Ubuntu 22.04 install + a Windows 10 installation carved out on a separate partition. Both OS's are installed on the same physical disk ([FONT=Lucida Console]/dev/nvme0n1[/FONT])

Today, the system will  boot directly into Ubuntu. If I need or want to boot into Windows, I  have to mash DEL/F10 to get into my BIOS/EFI which due to my wirless keyboard, sometimes the input does not register in time and I have to reboot and pray to the linux gods that it works on the second go-around.

Ideally, I want the system to provide the Grub boot menu which will allow me to select ubuntu/windows accordingly vs having to mash F10/DEL to get into BIOS/EFI. 

The problem is, Grub Customizer doesn't seem to be working properly on 22.04 and I am at a loss on how to fix w/o having to reinstall Ubuntu. I am aware there are some issues with Grub Customizer on 22.04 but I've also seen reports/users not having issues, so I'm posting here for support. 

Here is my grub customizer cfg file, if I understand the documentation correctly it SHOULD be prompting me with a menu but alas it does not.

```
madsci@bosdsk2ubncto:~$ date ;  cat /etc/default/grub
Wed Nov 29 10:05:12 AM EST 2023
-rw-r--r-- 1 root root 1505 Nov 29 10:01 /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="saved"
#GRUB_TIMEOUT_STYLE="hidden"
#GRUB_TIMEOUT="-1"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"

#GRUB_HIDDEN_TIMEOUT="0"
#GRUB_DISABLE_OS_PROBER="false"
GRUB_SAVEDEFAULT="true"

export GRUB_COLOR_NORMAL="white/black"
export GRUB_COLOR_HIGHLIGHT="light-green/black"
export GRUB_MENU_PICTURE="/home/madsci/Pictures/bulba_background_01.jpg"
GRUB_FONT="/boot/grub/unicode.pf2"

```

Any advice or pointers would be greatly appreciated.

---

### Post by oldfred on 2023-11-29
You really do not need grub customizer to change a setting in /etc/default/grub.
I use this:
> [FONT=monospace][COLOR=#000000]GRUB_TIMEOUT_STYLE=menu [/COLOR]
GRUB_TIMEOUT=3
[/FONT]
I change 10 second delay to 3, so I normally boot quickly. But have then just 3 seconds to change which system I want to boot.

I have a grub script which changes many setting and adds 40_custom entries.
It includes these , script is run with sudo so each command does not have sudo.
```
 sed -i '/GRUB_TIMEOUT=/ s/10/3/' /etc/default/grub
  sed -i '/GRUB_TIMEOUT_STYLE=/ s/hidden/menu/' /etc/default/grub


```

I like to backup grub's original configuration just after install which normally includes os-prober entry.
I turn off os-prober and add any entries I want into 40_custom. After I did it once or twice I just needed the entries into 40_custom, but still backup grub after install.

sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup

More info con customizing grub.
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen) & 
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config) &

---

### Post by MAFoElffen on 2023-11-29
I do not recommend the use of "Grub Customizer". Many users of many Distro's keep having booting issues with it. Then they come here for help with an application that is not well maintained and causes problems 'eventually'. 

I don't usually talk bad about an application, and I just help people with what they have, and what they want to do. But this one is an exception. Since it's release many years ago, I have had to help many Users recover from problems caused by it. It's like a timebomb ready to go off.

Anything you can do with that, you can do manually via referring to the documentation here and at GNU.

---

### Post by tea for one on 2023-11-29
Do you have these folders?
/etc/grub.d/backup
/etc/grub.d/bin
/etc/grub.d/proxifiedScripts

---

### Post by madscientist032 on 2023-11-29
Thanks for the advice! I am aware that Grub Customizer isn't really needed to do what I want, and to be honest, manually going and poking around is my preferred method. However, I get leery of modifying grub settings via CLI hence why I used a UI. 

I applied your feedback to my grub file & rebooted, the system still does not prompt me with a menu.. so I am currently looking at the documentation you've supplied in the hopes I can get where I need to go.

I may end up needing to revert to a "default" grub settings and customize from there accordingly as I did not make a backup of my grub file prior to customizing (whoops!)

Either way, I'm going to end up removing the grub customizer program & just modifying the grub file(s) manually once everything works proper & as expected.

EDIT: I wrote this prior to seeing other posts come in, her'es the content of my /etc/grub.d directory...

```
madsci@bosdsk2ubncto:~$ ls -l /etc/grub.d
total 144
-rwxr-xr-x 1 root root 10627 Jan 11  2022 00_header
-rwxr-xr-x 1 root root  6260 Dec  2  2022 05_debian_theme
-rwxr-xr-x 1 root root 18683 Dec  2  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec  2  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root  2924 Feb  6  2022 20_memtest86+
-rwxr-xr-x 1 root root 13369 Dec  2  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec  2  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 20  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Jan 11  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec  2  2022 41_custom
drwxr-xr-x 4 root root  4096 Jan 20  2023 backup
-rw-r--r-- 1 root root   483 Jan 11  2022 README
madsci@bosdsk2ubncto:~$ 
```

---

### Post by tea for one on 2023-11-29
No proxifiedscipts - that's good news.

I would first edit /etc/default/grub
```
#GRUB_DISABLE_OS_PROBER="false" - [COLOR="#0000FF"]remove the comment #[/COLOR]
```
Save and exit
```
sudo-update-grub
```
Does the output find the Windows Boot Manager?

---

### Post by madscientist032 on 2023-11-29
> **tea for one said:**
> Does the output find the Windows Boot Manager?

Yes! Output is below.

I ended up rebooting after posting out of curiosity... I still do not get the GRUB boot menu.

```
madsci@bosdsk2ubncto:/etc/default$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
using custom appearance settings
Found linux image: /boot/vmlinuz-6.2.0-37-generic
Found initrd image: /boot/initrd.img-6.2.0-37-generic
Found linux image: /boot/vmlinuz-6.2.0-36-generic
Found initrd image: /boot/initrd.img-6.2.0-36-generic
Found linux image: /boot/vmlinuz-5.19.0-50-generic
Found initrd image: /boot/initrd.img-5.19.0-50-generic
Found linux image: /boot/vmlinuz-5.15.0-89-generic
Found initrd image: /boot/initrd.img-5.15.0-89-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
```

---

### Post by tea for one on 2023-11-29
So far far, so good - quite encouraging
You mentioned in post 1 that "Today, the system will boot directly into Ubuntu".
Boot priority has not changed, only Windows Boot Manager should now be in the Grub menu.

You may want to edit etc/default/grub again to make grub appear when you power on.
oldfred mentioned:-
```
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=3 [COLOR="#0000FF"]- I prefer 10 because I daydream too much[/COLOR]
```
Save and exit and update-grub again.
Power off and power on again.

Drinks all round or a slap on the belly with a wet fish?  ;)

Edit - you rebooted before I had finished this post.

---

### Post by madscientist032 on 2023-11-29
No worries. I've already modified GRUB_TIMEOUT_STYLE and GRUB_TIMEOUT as per oldfred's suggestion.

The end goal is to have my system display the GRUB menu & prompting me with which OS to boot into, vs bypassing the grub menu and booting directly into Ubuntu. I apologize for the disconnect. 

Here's a diff of the previous and current GRUB files:

```
madsci@bosdsk2ubncto:~$ diff /etc/default/grub /etc/default/grub.backup_20231129.1 
7,8c7,8
< GRUB_TIMEOUT_STYLE="menu"
< GRUB_TIMEOUT="5"
---
> #GRUB_TIMEOUT_STYLE="hidden"
> #GRUB_TIMEOUT="-1"
36c36
< GRUB_DISABLE_OS_PROBER="false"
---
> #GRUB_DISABLE_OS_PROBER="false"
42c42
< GRUB_FONT="/boot/grub/unicode.pf2"
---
> GRUB_FONT="/boot/grub/unicode.pf2"
\ No newline at end of file
madsci@bosdsk2ubncto:~$ 
```

BTW no clue on why or how GRUB_FONT is different between the two files... I didn't touch that so wondering if that was during a grub-update execution?

---

### Post by MAFoElffen on 2023-11-29
Add this line:
```

GRUB_RECORDFAIL_TIMEOUT=5

```
Then update-grub again...

---

### Post by madscientist032 on 2023-11-30
> **MAFoElffen said:**
> Add this line:
```

GRUB_RECORDFAIL_TIMEOUT=5

```
Then update-grub again...

Added & updated & rebooted... same behaviour. Boots straight to Ubuntu & does not provide me the GRUB boot menu. 

Here's the current grub configuration as it's been some time since I've posted the original and I've applied the modifications as per everyone's feedback thus far. 

```
madsci@bosdsk2ubncto:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

#Added as per "MAFoElffen" on 11-30-2023 
GRUB_RECORDFAIL_TIMEOUT=5

GRUB_DEFAULT="saved"
GRUB_TIMEOUT_STYLE="menu"
GRUB_TIMEOUT="5"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"

#GRUB_HIDDEN_TIMEOUT="0"
GRUB_DISABLE_OS_PROBER="false"
GRUB_SAVEDEFAULT="true"

export GRUB_COLOR_NORMAL="white/black"
export GRUB_COLOR_HIGHLIGHT="light-green/black"
export GRUB_MENU_PICTURE="/home/madsci/Pictures/bulba_background_01.jpg"
GRUB_FONT="/boot/grub/unicode.pf2"
madsci@bosdsk2ubncto:~$ 

```

---

### Post by oldfred on 2023-11-30
When you run sudo update-grub, do you get any error messages.
Like that it creates /boot/grub/grub.cfg.new which is the error file?

---

### Post by MAFoElffen on 2023-12-01
> **madscientist032 said:**
> 
Here's the current grub configuration
```

[COLOR=#ff0000]GRUB_DEFAULT="saved"[/COLOR]
GRUB_TIMEOUT_STYLE="menu"
GRUB_TIMEOUT="5"
GRUB_RECORDFAIL_TIMEOUT=5
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
[COLOR=#ff0000]GRUB_TERMINAL="console"[/COLOR] [COLOR=#FF0000]## <-- This should really be commented out!!![/COLOR]
GRUB_INIT_TUNE="480 440 1"
GRUB_DISABLE_OS_PROBER="false"
[COLOR=#FF0000]GRUB_SAVEDEFAULT="true"[/COLOR]
export GRUB_COLOR_NORMAL="white/black" ## foreground and background colors
export GRUB_COLOR_HIGHLIGHT="light-green/black" ## Highlight foreground and background colors
export GRUB_MENU_PICTURE="/home/madsci/Pictures/bulba_background_01.jpg" ## grub background picture setting
GRUB_FONT="/boot/grub/unicode.pf2" ## grub font setting...

```
Here is mine... Then I'll discuss what I see in yours:
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=5
GRUB_RECORDFAIL_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="-- splash intel_kvm.nested=1 video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank intel_iommu=on systemd.unified_cgroup_hierarchy=0 intremap=no_x2apic_optout nox2apic reboot=pci"
GRUB_CMDLINE_LINUX=""
GRUB_GFX_MODE=1280x1024x32
GRUB_DISABLE_OS_PROBER=false

```
Let's talk about what the Grub2 variables in yours mean...

GRUB_DEFAULT means that it automatically boots whatever it points to. You can say a #, where it starts with Menu Entry 0, or part of a string in the menu title, or the keyword "saved'. If you say &#8216;saved&#8217;, then the default menu entry will be that saved by &#8216;GRUB_SAVEDEFAULT&#8217; or grub-set-default. 

GRUB_SAVEDEFAULT means, if this option is set to &#8216;true&#8217;, then, when an entry is selected, save it as a new default entry for use by future runs of GRUB. This is only useful if &#8216;GRUB_DEFAULT=saved&#8217;; it is a separate option because &#8216;GRUB_DEFAULT=saved&#8217; _is useful without this option_, in conjunction with grub-set-default. Unset by default.

If you comment out these two above variables... It will go back to normal, and boot the first menu item in the menu, which is the Grub default... No harm, no foul leaving it.

GRUB_TERMINAL means that you want a text console boot mode (init 3)... You need to comment that out of you don't want that to affect your graphics, and you are trying to do Grub Theming. This is probably why your font setting is not working.

I commented the rest above... Next to each item.

---

### Post by ajgreeny on 2023-12-01
You have double quote marks around all or most of the chosen options in your /etc/default/grub file which are not in the default versions shown elsewhere in this thread.
I'm not on my Linux box at the moment so can't check this but try removing the "" from those entries, run **sudo update-grub** again and see if that works.
NB:
I may be totally incorrect but small syntax errors like this can cause problems so its worth checking!

---

### Post by dragonfly41 on 2023-12-01
Add efibootmgr as a CLI tool to define boot order.
And (optionally) I chose to install rEFInd as my primary boot manager (UI).
Offer a nice GUI at boot time.
It shows up as boot option in efibootmgr (or BIOS).

Clip from efibootmgr print in terminal ... running command efibootmgr

[FONT=monospace][COLOR=#000000]BootOrder: 0003,0001,0000,0007,0010,0009,000A,000D[/COLOR]
Boot0000* Windows Boot Manager     <<third in BootOrder
Boot0001* ubuntu                   <<second in BootOrder
Boot0003* rEFInd Boot Manager      <<first in BootOrder


P.S. I keep LiveUSB plugged into powered USB expander and it shows in efibootmgr as ..

[/FONT][FONT=monospace][COLOR=#000000]Boot0009* USB Storage Device

[/COLOR]Other Ubuntu OS in separate USB containers can likewise be in BootOrder. So this keeps order in a birds nest of experiments.

[/FONT]

---

### Post by tea for one on 2023-12-01
+1 to rEFInd - good suggestion
I use it on a portable USB, when Grub is damaged/not responding.

---

### Post by madscientist032 on 2023-12-01
Hello - lots of activity here! I was away on personal matters, which meant I couldn't respond sooner. Thanks everyone for your feedback so far.

I am not having any issues updating the grub file.

In fact, I went ahead and made the following changes to my grub file and am about to reboot & see where things stand. 

[IMG]https://cdn.discordapp.com/attachments/750412299533156456/1180250669018525868/Screenshot_from_2023-12-01_15-53-35.png?ex=657cbd17&is=656a4817&hm=604121c02498d5518aad85e940a8e80285bf2bef026ecf595b099372d7ca0725&[/IMG]

I get this output on latest update, it does not seem to generate any issues or errors. I do not recall seeing anything bad on previous updates either. 

```
madsci@bosdsk2ubncto:/etc/default$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
using custom appearance settings
Found background image: /home/madsci/Pictures/bulba_background_01.jpg
Found linux image: /boot/vmlinuz-6.2.0-37-generic
Found initrd image: /boot/initrd.img-6.2.0-37-generic
Found linux image: /boot/vmlinuz-6.2.0-36-generic
Found initrd image: /boot/initrd.img-6.2.0-36-generic
Found linux image: /boot/vmlinuz-5.19.0-50-generic
Found initrd image: /boot/initrd.img-5.19.0-50-generic
Found linux image: /boot/vmlinuz-5.15.0-89-generic
Found initrd image: /boot/initrd.img-5.15.0-89-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
madsci@bosdsk2ubncto:/etc/default$ 
```

---

### Post by tea for one on 2023-12-01
#GRUB_DEFAULT=0

You have the comment symbol there - is that deliberate or a typo?

---

### Post by MAFoElffen on 2023-12-01
I would uncomment that one... (the 0). And does it work? If so, how does it work, and how does it look now?

---

### Post by ajgreeny on 2023-12-02
And as I said before, please remove most of those " " around many of the options in the file; they are certainly unnecessary and I have almost none of them.
Here's the important bits of my version which works as it should.
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=2
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_DISTRIBUTOR="Xubuntu-22-04"       #[COLOR="#0000FF"]This my edited line and shows exactly what is shown in the grub menu[/COLOR]
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

```

---

### Post by oldfred on 2023-12-02
Mine is very similar to ajgreeny's. 

```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /etc/default/grub | grep -v "#" [/COLOR]
GRUB_DEFAULT=0 
GRUB_TIMEOUT_STYLE=menu 
GRUB_TIMEOUT=3 
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth" 
GRUB_CMDLINE_LINUX="" 
GRUB_DISABLE_OS_PROBER=true 
GRUB_DISTRIBUTOR=jammy
[/FONT]
```

---

### Post by dragonfly41 on 2023-12-02
Being curious .. here is mine
[FONT=monospace][COLOR=#000000]```

GRUB_DEFAULT="0"[/COLOR]
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

But custom installed rEFInd takes over and I see only a UI.
But the UI allows diving into grub menu if I wish. And BIOS and other goodies such as mem test.



[/FONT]

---

### Post by MAFoElffen on 2023-12-02
@dragonfly41

Suggested EDIT:
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_RECORDFAIL_TIMEOUT=10
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
The first two records of yours should not have quotation marks. They are values, not strings.

---

### Post by #&amp;thj^% on 2023-12-02
If I remember correctly "rEFInd " puts those Quotes in.
Sorry for the the Drive Bye
```
GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 quiet"
GRUB_DISTRIBUTOR="Crystal"
GRUB_TIMEOUT=5
GRUB_DEFAULT=0

```
I was wrong. :P

---

### Post by madscientist032 on 2023-12-02
All - I reverted my GRUB configuration to what I believe are the default values, executed update-grub & rebooted. 

I am still not seeing the boot menu with Ubuntu/Windows/Memtest86/prior linux kernels after POST. What am I missing? 

```
madsci@bosdsk2ubncto:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
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
GRUB_INIT_TUNE="480 440 1"

```

There were no errors during the update-grub process.

---

### Post by #&amp;thj^% on 2023-12-02
I see one thing straight away
```
"`lsb_release -i -s 2> /dev/null || echo Debian`"
```
You seem to have picked up back-ticks "''"
Do you now see that?

---

### Post by madscientist032 on 2023-12-02
> **1fallen said:**
> I see one thing straight away
```
"`lsb_release -i -s 2> /dev/null || echo Debian`"
```
You seem to have picked up back-ticks "''"
Do you now see that?

Yes, I went ahead and removed them & applied update-grub, rebooted, still no change (wasn't expecting a change but still wanted to verify regardless.)

---

### Post by #&amp;thj^% on 2023-12-02
Dang another one of these>>>Grub Customizer on 22.04.
I heard  there is an update to a another maintained PPA, but I'm unsure how you installed yours, as it was removed from jammy due to a bug.
can you show me your apt/source list;
```
inxi -r
```
BTW I agree with all the others over Grub Customizer, just bad juju. :)
BTW Here is the long bug list from that PPA: [https://bugs.launchpad.net/~danielrichter2007](https://bugs.launchpad.net/~danielrichter2007)
EDIT: This may help, instructions from the Developer: [https://answers.launchpad.net/grub-customizer/+faq/1355](https://answers.launchpad.net/grub-customizer/+faq/1355)

---

### Post by tea for one on 2023-12-02
> **madscientist032 said:**
> I am still not seeing the boot menu with Ubuntu/Windows/Memtest86/prior linux kernels after POST. What am I missing? 
```
GRUB_TIMEOUT_STYLE=[COLOR="#FF0000"]hidden[/COLOR]
GRUB_TIMEOUT_STYLE=[COLOR="#0000FF"]menu[/COLOR]
```
Change hidden to menu in /etc/default/grub

Edit: I've just noticed that your revised grub file needs a bit more attention.
```
GRUB_TIMEOUT=5
GRUB_DISABLE_OS_PROBER=false
```
Save and reboot

---

### Post by madscientist032 on 2023-12-02
> **1fallen said:**
> Dang another one of these>>>Grub Customizer on 22.04.
I heard  there is an update to a another maintained PPA, but I'm unsure how you installed yours, as it was removed from jammy due to a bug.

I originally installed Grub Customizer back when this workstation was running Ubuntu on 20.04 and I had zero issues with it. I'm going to get rid of it once I figure out my issue now that I know it's broken PLUS the fact I don't need it in the first place! :)

> **tea for one said:**
> ```
GRUB_TIMEOUT_STYLE=[COLOR="#FF0000"]hidden[/COLOR]
GRUB_TIMEOUT_STYLE=[COLOR="#0000FF"]menu[/COLOR]
```
Change hidden to menu in /etc/default/grub

Edit: I've just noticed that your revised grub file needs a bit more attention.
```
GRUB_TIMEOUT=5
GRUB_DISABLE_OS_PROBER=false
```
Save and reboot

Made changes and rebooted. No change :( 

Contents of current grub file:

```
madsci@bosdsk2ubncto:~$ date ; cat /etc/default/grub | grep -v "#"
Sat Dec  2 08:36:42 PM EST 2023

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

GRUB_INIT_TUNE="480 440 1"
GRUB_DISABLE_OS_PROBER=false

madsci@bosdsk2ubncto:~$ 
```

---

### Post by MAFoElffen on 2023-12-02
Please change to this:
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=5
[COLOR=#ff0000]GRUB_RECORDFAIL_TIMEOUT=5[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

GRUB_INIT_TUNE="480 440 1"
GRUB_DISABLE_OS_PROBER=false

```
I keep saying that. i guess I need to add refrences, that it gets around this BUG: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1800722](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1800722)

Then do this 
```

sudo apt update
sudo apt-get install ppa-purge
sudo ppa-purge ppa:danielrichter2007/grub-customizer
sudo update-grub

```
Reboot and test...

---

### Post by oldfred on 2023-12-02
Does uninstalling grub-customizer restore the backup grub script files?

I might also totally uninstall grub & reinstall it. If uninstalled & reinstall does not work, you have to have a live installer to restore grub.

Make sure repositories are updated
sudo apt update
sudo apt upgrade
sudo apt purge grub-efi-amd64 grub grub-pc grub-common # if any file not there & error, re-run without that one file
sudo mv /boot/grub /boot/grub_backup
sudo mv /etc/grub.d /etc/grub.d_backup
sudo mkdir /boot/grub
sudo mkdir /etc/grub.d
sudo apt-get install grub-efi-amd64
sudo update-grub

Total reinstall will restore grub to defaults.

---

### Post by madscientist032 on 2023-12-03
> **MAFoElffen said:**
> Please change to this:
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=5
[COLOR=#ff0000]GRUB_RECORDFAIL_TIMEOUT=5[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

GRUB_INIT_TUNE="480 440 1"
GRUB_DISABLE_OS_PROBER=false

```
I keep saying that. i guess I need to add refrences, that it gets around this BUG: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1800722](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1800722)

Then do this 
```

sudo apt update
sudo apt-get install ppa-purge
sudo ppa-purge ppa:danielrichter2007/grub-customizer
sudo update-grub

```
Reboot and test...

Thank you for the reminder! It seems in the shuffle I lost that change. I've added it back accordingly alongside the bug URL for future reference. 
The old PPA is removed and I also went ahead and removed grub-customizer as well. 

> **oldfred said:**
> Does uninstalling grub-customizer restore the backup grub script files?

I might also totally uninstall grub & reinstall it. If uninstalled & reinstall does not work, you have to have a live installer to restore grub.

.....

Total reinstall will restore grub to defaults.

As mentioned above, I went ahead and uninstalled grub-customizer. I **did NOT reinstall grub just yet**

SO it seems uninstalling grub-customizer doesn't restore any files and that if i want to go back to Vanilla & need to reinstall grub. 

I'm not super comfortable doing this on my main machine so I'm going to test in one of my VMs (incidentally it's one I used to validate going from 20.04 to 22.04 before executing it on my workstation!)

Thanks to everyone for your patience and support thus far.

---

### Post by Rovano on 2023-12-06
```
GRUB_SAVEDEFAULT="false"
[COLOR=#00ff00]GRUB_RECORDFAIL_TIMEOUT=5[/COLOR]
GRUB_DEFAULT="2"
GRUB_TIMEOUT_STYLE="hidden"
[COLOR=#00ff00]GRUB_TIMEOUT="5"[/COLOR]
GRUB_DISTRIBUTOR=[COLOR=#00ff00]"[/COLOR]`lsb_release -i -s 2> /dev/null || echo Debian`[COLOR=#00ff00]"[/COLOR]
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

export GRUB_COLOR_NORMAL="light-gray/black"
export GRUB_COLOR_HIGHLIGHT="magenta/black"

```

I have almost the same thing as in comment #31.
I'm just looking that he's missing some characters.

I was happy using recordfail with a change aimed at grub timeout. After some update about 2 months back, it started ignoring the 5 second timeout, and kept waiting for 30 seconds.

So I did the transformation and wrote the time hard.

I forgot to write that this is the config from version 23.10. But it will definitely work even on 22.04.

You can play with it more, but you have to change the pre-set scripts around or templates.

Maybe I'll make up my mind a bit now. I have a feeling that the hidden setting and those styles will make the graphics a little different.

There is no need to set the menu there.

Don't forget.
```
[COLOR=#00ff00]sudo update-grub[/COLOR]

```

GL

---

### Post by madscientist032 on 2023-12-06
> **oldfred said:**
> Does uninstalling grub-customizer restore the backup grub script files?

I might also totally uninstall grub & reinstall it. If uninstalled & reinstall does not work, you have to have a live installer to restore grub.

Make sure repositories are updated
sudo apt update
sudo apt upgrade
sudo apt purge grub-efi-amd64 grub grub-pc grub-common # if any file not there & error, re-run without that one file
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-efi-amd64
sudo update-grub

Total reinstall will restore grub to defaults.

Houston, we have liftoff! I have a boot menu and I can pick what OS I need to boot into vs going straight to Ubuntu.

I also removed that PPA for grub-customizer which in turn removed the software, so that's great to have completed as well. 

While it's unfortunate that I had no choice but to reinstall GRUB to fix my issue, I'm glad my system works as intended and this time I'll be a bit more careful about what I modify & be more diligent about making & keeping backups...

I am going to mark this thread as SOLVED. Thanks to everyone for your support on this!

---

