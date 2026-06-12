---
title: "Black screen on bootup"
date: 2013-10-05
forum: General Help
---

### Post by olipoh1 on 2013-10-05
Hello everyone,

I'm opening a new thread, similar to solved one:
[http://ubuntuforums.org/showthread.php?t=2178748](http://ubuntuforums.org/showthread.php?t=2178748)

as I'm not the author and it doesn't work for me.

When I boot my Toshiba satellite, I can hear the login bongos play, but can only see a black screen with my mouse cursor. I tried to put [COLOR=#000000][FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"[/FONT][/COLOR] in grub, but it worked only once.
There is a strange thing : if I force the grub menu to display on boot, then choose "ubuntu" line, everything goes fine. So what is the difference ? There must be one as I have a black screen in a case, not in the other.

And I don't know why this error appeared suddenly.
Thanks everyone. Have a good day.

Olivier

PS : my ubuntu is 13.04 with last updates (I suspect one of theses updates to be responsible).

---

### Post by lama2p0 on 2013-10-05
Yes, It would appear mine also isn't fixed.. it takes a series of reboots for it to go.. acpi I'm guessing must be unrelated, and the changes I've made with acpi being a success must of just been by chance..

---

### Post by oldfred on 2013-10-05
There is this bug. But if it worked once.
Any setting on grub menu as you boot is a one time change, more for testing. You have to edit /etc/default/grub    and update grub to make it permanent. 

 Intermittent black screen or low graphics mode message bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150)

Also turn off one Video mode or Intel settings in UEFI/BIOS like Intel NIC if USB flash not working.
Some Laptops need this in place of quiet splash:
       acpi_osi=Linux acpi_backlight=vendor
Some laptops just have backlight set way down, press f key to make it brighter
New Haswell systems may need newest kernel in currently beta 13.10 to support newest video

---

### Post by olipoh1 on 2013-10-06
[FONT=arial]Thank you very much olfred. It helped me.

I read the links you gave and I found 2 solutions :

1. switch from lightdm to gdm

2. then I came back to lightdm and tried something else. I pasted "sleep 1" between line 23 (script) and line 24 (if [ -n "$UPSTART_EVENTS" ]). It doesn't work for everybody, some will need to increase this time to 2 or more; as for me, it works. Oups, the file to edit is :[/FONT] [FONT=Ubuntu Mono]/etc/init/[/FONT][FONT=Ubuntu Mono]lightdm.[/FONT][FONT=Ubuntu Mono]conf[/FONT][FONT=arial]

Thanks again, and good luck to lama2p0 and others.
Olivier[/FONT]

---

