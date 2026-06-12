---
title: "Text Terminal Problem"
date: 2006-08-14
forum: General Help
---

### Post by SteveF on 2006-08-14
I asked this once before and did not get a solution, so I'm going to try to reword what I wrote to hopefully make it clearer.

I am running both Kubuntu and Ubuntu Dapper and have the same problem with both.  I am running on a Dell with a NVidia Geforce 2 MX graphics card and a Dell M991 Monitor.

When Dapper begins, it displays some messages on the text screen without any problems.  It then switches to its graphical mode to display the logo and the rest of the messages.  From this point on (including the messages displayed here), the text is not fitting on the screen.  This carries over to terminal screens (CTRL-ALT-F1 etc).  For the terminal screens, text on the left is chopped off (looks like half the character, though I could be missing one more character).  On the bottom of the screen, I am missing one or more lines (tough to tell) and one more line is chopped in half.

KDE or Gnome begins and my session is fine for that screen, but the rest of the terminals (CTRL-Alt-F1 etc) have the problem.  This means I can not do any work without being in X.

If I am having problems in X, my only solutios are to either reboot in recovery mode (which shows a normal terminal) or to guess what I am typing.

My guess is the graphics mode being used is not correct for my graphics card/monitor combination.  Is there anything I can change that will modify the graphics mode used or that will turn off Dapper from using graphics mode during startup.  Or, is there a command I can type, once in the terminal, to change the graphics back to text?

Thanks,

Steve

---

### Post by hanzomon4 on 2006-08-14
You can change the resolution by adding vga=XXX something to the kernel command in the /boot/grub/menu.list
Something like this
```
  /boot/vmlinuz-2.6.16-rt29 root=/dev/sda2 ro quiet splash vga=791
```

---

### Post by SteveF on 2006-08-14
Thank you for the example.  I got a similar response before but I had know knowledge of where or how to place the vga setting.

I tried your example and when I reboot, I get a message that the vga mode is not valid, press return or wait 30 seconds.  If I press return I get a list of valid modes.  If I use one of those modes (either by selecting from the list or modifying vga= to use one of them), I'm back to a text terminal and I no longer get a graphical start.  If instead I wait the 30 seconds, then I get a graphical start (though much smaller than usual) and an even better terminal (not sure what size it is using, but I can fit a lot more on screen).

Any idea why I lose the graphical install using vga= or what is happening when I wait the 30 seconds to get the better result?

Thanks,

Steve

---

### Post by SteveF on 2006-08-14
Sorry.  I now want to change my response.  Turns out, I had a typo when I entered 791 and that's why the mode failed.  Putting 791 in correctly gave me the correct results.  Took a while to verify what should be entered using Google.  I guess the values are either text mode 1 - A (which shows on the menu when you hit return) or some numbers in the 600 and 700s that represent graphic screen resolutions (I'm guessing).

Thanks, I have my solution.

Steve

---

### Post by Anduu on 2006-08-15
For future reference...

---

### Post by SteveF on 2006-08-15
Thanks, that will definitely come in handy.

Steve

---

