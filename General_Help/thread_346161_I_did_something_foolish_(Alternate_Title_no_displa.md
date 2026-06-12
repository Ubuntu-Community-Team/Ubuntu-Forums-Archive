---
title: "I did something foolish (Alternate Title: no display manager after boot problems...)"
date: 2007-01-25
forum: General Help
---

### Post by paulg on 2007-01-25
OK, the story starts with Alsa not working properly with my system after the upgrade to Ubuntu 6.10 from 6.06. Due to certain events in my personal life I have not had time to trouble shoot nor really cared as I was using the computer less.

I thought that perhaps installing Kubuntu would be the solution to my problems, perhaps forcing some software to do a fresh configuration, magically restoring my systems operations. Well, it didn't. But this post isn't about my problems with Alsa...

So I decided I liked the Gnome/Ubuntu interface better (familiar with it and the Gnome programs) and wanted to switch back as my _brilliant_ plan to use Kubuntu to return my audio functionality did not pan out. Well, selecting Gnome as my window manager at login was easy enough. Getting rid of KDM (and the rest of Kubuntu), however turns out to be a little more tricky - but again, that will be another post. Searching the forums, someone had posted a command to change the default login manager to GDM, which I did, and it worked! Then I turned my attention toward Alsa putting the Kubuntu removal to the back burner figuring with my new brilliant plan I had it beat this time. I would do an uninstall and then a complete re-install! Well that didn't work. I am positive I _watched_ GDM get uninstalled along with alsa-utils during my uninstall escapade, and now for the foolish part, I rebooted. 

So what happens now, when I boot I get the Kubuntu startup screen (the blue Kubuntu text and logo with progress bar) and then no login (shell nor gui). Now I realize this is because my system is still configured to display GDM which, apparently I uninstalled. I have tried to find a shell using ctrl+alt+F1 through F12 to no avail.

To fix it I figure I can do one of two things: 

[LIST]
[*]Somehow boot to a shell login so I can reinstall GDM; or

[*]Change the appropriate configuration file to use KDM (which is still installed). I have a copy of the 6.06 Live Ubuntu disk from which I think it should be possible to mount my hard drive and change the configuration file to use KDM so I can get a display manager but I am not sure which file I would need to change.
[/LIST]

Any direction with either of these problems would be greatly appreciated.

I guess a third option would be to re-install but that seems like the "quitters" way out =)

~pAul.

all good things, all in good time

---

### Post by IntuitiveNipple on 2007-01-25
First thing you need to do is boot into recovery mode.

If you haven't also *played* with the GRUB boot menu, you should have a recovery option that you can try.

When the PC boots, just after the BIOS displays the system summary, you should see a message similar to "Press Esc for the boot menu". By default that menu is hidden at boot-time. Press Escape at that point.

On the boot menu you should see at least 3 options, possibly more.

Choose one that is labeled "Recovery" that matches what you think is the best kernel profile and press Enter to start with that kernel.

If that doesn't help, you need to force the kernel to boot to a command line. You can do that by following the same procedure as above, but instead of pressing Enter to boot that kernel, you press "e" to *edit* it.

You'll see the kernel's command-line.

You should add **init=/bin/sh** to the end then press Enter to approve the change, then "b" to boot that kernel.

This will boot the kernel to a shell without running all the usual *init* scripts. That should put you in a position to use the command line to sort things out.

---

### Post by paulg on 2007-01-25
Thanks TJ,

The recovery mode kernel is available but I have never tried it and did not know what it was for. I will try it out tonight.

---

### Post by paulg on 2007-01-25
Worked, thanks again TJ.

~pAul.

---

