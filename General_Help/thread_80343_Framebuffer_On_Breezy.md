---
title: "Framebuffer On Breezy"
date: 2005-10-22
forum: General Help
---

### Post by br00tal on 2005-10-22
Hello,
I'm having some issues getting framebuffer to function in Breezy.  It was very simple to get goin in Hoary, but I think that the usplash have mucked it up a bit.  Does anyone know how to et this working?

Thanks,
Jesse

---

### Post by br00tal on 2005-10-23
Anyone on this?

---

### Post by Joe_lurker on 2005-10-23
I think you need to post a bit more information.  What exactly is not working that worked before?  What have you tried?

-Joe

---

### Post by br00tal on 2005-10-23
On Hoary, all that I needed to do was add "vga=791" to the menu.lst file after the kernel specifications.  It was that simple.  When I do that in Breezy, the monitor clicks over to the specified framebuffer resolution for a split second, but when the usplash begins to run, it switches back.  Then, once fully booted, I switch to some of my tty's and there running in "normal" mode, but "791".  So, I think something with the graphical boot is mucking this up.  How can I disable the graphical boot?

---

### Post by 23meg on 2005-10-23
i'm also interested in temporarily disabling usplash, since my virtual terminals are completely gone in breezy. whenever i hit ctrl+alt+f(x) i just get a blank screen.

---

### Post by Joe_lurker on 2005-10-23
To temporarily edit the command line in the GRUB boot screen.  When you see the menu of boot options press the 'e' key in the item you are going to boot.  Press the 'e' key again on the kernel line.  This will allow you to edit the boot parameters.  Delete the words 'quiet' and 'splash'.

To permanantly remove the quiet and splash options edit the file /boot/grub/menu.lst.  Find the line '# nonaltoptions=quiet splash' (about line 89) and delete everything after the '='.  The line should read '# nonaltoptions='

Next run 'sudo update-grub'.  This will reconfigure the file for grub to boot.

-Joe

---

