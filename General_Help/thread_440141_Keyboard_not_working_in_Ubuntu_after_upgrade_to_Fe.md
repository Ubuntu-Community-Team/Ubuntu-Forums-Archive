---
title: "Keyboard not working in Ubuntu after upgrade to Feisty"
date: 2007-05-11
forum: General Help
---

### Post by runesvend on 2007-05-11
Hello

I started by installing Edgy Eft, no problems there at all. I've had a previous installation og Ubuntu where I experience no problems as well. I upgraded my current installation via an internet connection to Feisty Fawn and after the computer had booted the keyboard didn't work at the login screen.

The problem, as I see it, must be in Ubuntu since: at the BIOS screen the keyboard works; I can enter the BIOS and move the around in the menus, selecting Ubuntu in GRUB via the keyboard works as well. I have also tried with another keyboard of a different brand, same deal.

Both keyboards are connected to my PC via a PS/2 plug. My mouse, which is an USB mouse, works fine. This, of course, begs the question if I've tried with a USB keyboard but I don't own one unfortunately.

Update info:

Keyboard does not work when booting into my Ubuntu installation in recovery mode
Keyboard works when pressing 'c' at the GRUB menu to get a command line
Neither Num Lock, Caps Lock nor Scroll Lock works when pressing them (no light turns on). These buttons are fully functional in the BIOS

Any suggestions? This is *really* annoying especially since I've come to like Ubuntu a lot since choosing it over Windows...

Thanks in advance!

---

### Post by carolinason on 2007-05-11
Just some ideas.

it sounds like Ubuntu upgrade did not work fully. It might be a setting in  /etc/X11/xorg.conf. Not sure how you could get a copy of this without the use of your keyboard.

I've had the problem of keyboard works in bios not in os before, but it has been years and I cannot remember my fix. It seems it was xorg though except back then it was xfree.

I might have wimped out and did a clean install.

---

### Post by Loki-uk on 2007-05-11
Is your motherboard an SIS chipset? there seems to be a bg in the kernel that is preventing the PS2 from working in on some SIS chipset motherboards (asus seem to be quite comon).

There is a patch (for ps2 mice at least) but it's source and you have to recompile the kernel. 

Loki

---

### Post by runesvend on 2007-05-14
carolinason, I've booted into Ubuntu from a live CD now and I'm including the xorg.conf from my non-working installation in this post. Since my post I've reinstalled Ubuntu 6.10 from my live CD and upgraded to 7.04 again and the same thing happens.

Loki-uk, my chipset is from VIA Technologies and it's called VIA KT266A. I have an ABIT KR7A-RAID motherboard.

Thanks for your time.

EDIT: I've included portions of the log file for xorg.conf from my faulty installation (/var/log/xorg.0.log) which seem to indicate an error with the keyboard.

---

### Post by runesvend on 2007-05-14
I've been looking through some logs and found things that contain either "PS/2" or "keyboard" in hope that it will help. There are some interesting finds amongst them I think:

Various logs from /var/log/:

From "messages":

[B](Prior to upgrade)
*May 11 21:35:04 rune-desktop kernel: [17179573.876000] input: AT Translated Set 2 keyboard as /class/input/input0*

(After upgrading)
[I]May 14 11:45:02 rune-desktop kernel: [   24.533376] input: AT Translated Set 2 keyboard as /class/input/input1[/B]
[/I]
[I]May 14 11:45:02 rune-desktop kernel: [   24.450880] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May 14 11:45:02 rune-desktop kernel: [   24.450884] PNP: PS/2 controller doesn't have AUX irq; using default 12[/I]

From ":0.log":

[I][B]The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols[/B]
Errors from xkbcomp are not fatal to the X server
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
[/I]
From "Xorg.0.log":

[I](**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "dk"
(**) Generic Keyboard: XkbLayout: "dk"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled[/I]

---

### Post by pilpi on 2007-05-18
I'm having the same problem after upgrading to edgy. The strange thing is, the keyboard works sometimes. Then I boot up the PC, it always works in grub. Then often on the first boot it doesn't respond in the login screen in X anymore, but on the second or third it might. This applies to recovery console, too though so it's not only related to X. I have an asus A7V133-C (not sure about the -C though) motherboard. 

Also, System->quit doesn't have reboot or shutdown in gnome, only hibernate in the lower row :P. this is merely a nuisance though.

---

### Post by carolinason on 2007-06-05
Excuse me for my absence.

I have the same xorg error messages in my system log, these appear to be for a tablet pc. Also, pilpi could be confirming a bug.

Perhaps this a poor way to troubleshoot the issue, but I would just do a clean install of 7.04 as opposed to the 6.10 -> 7.04 upgrade path.

---

### Post by Yendor on 2007-06-08
There is another thread for this issue located here: [http://ubuntuforums.org/showthread.php?t=459742](http://ubuntuforums.org/showthread.php?t=459742)

Clean reinstall doesn't help - from either the live cd or alternate install cd.

Installing a USB keyboard (or, at least a cheap ps/2->usb adapter) seems to be the only "fix" at this time.

---

### Post by mactece on 2007-07-10
I now have the keyboard back - plugged into the mouse ps2 port. follow the link to the thread in the post above for more details.

---

