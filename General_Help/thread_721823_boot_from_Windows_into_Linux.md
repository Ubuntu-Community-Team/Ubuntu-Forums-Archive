---
title: "boot from Windows into Linux"
date: 2008-03-11
forum: General Help
---

### Post by pytheas22 on 2008-03-11
I know that I can easily reboot directly to Windows from Ubuntu with a command like
```

sudo grub reboot 1
```

which neither requires editing of any grub configuration files, nor waiting through the boot menu again.  I'd like to figure out a way to do the same thing just as simply from Windows into Linux.

I've read this thread, [http://ubuntuforums.org/showthread.php?t=465941](http://ubuntuforums.org/showthread.php?t=465941) , which provides a straight-forward way of booting from Windows to Linux, without having to select any boot option manually, by editing /boot/grub/menu.lst from Windows so that the default boot option is the one you want in your next session.  Ideally, however, I'd like a solution where no editing of grub files is necessary, and where Windows will always remain the default boot option (I am trying to apply this in a public lab, and unfortunately, since most patrons want Windows, it has to be the default).  It would also be nice if users didn't have to wait through ten seconds at the boot screen as well.

I'm not sure if there's a way to do this without having to edit grub, but I would be surprised if I'm the first person who wants to.  I did some research and didn't find anything beyond the thread cited above, however.  If anyone has any ideas, please pass them on.

---

### Post by doorknob60 on 2008-03-11
In that thread it talks about how you can use a batch file to automate that process. If you're not famaliar with batch files, they're pretty similar to shell scripts. If you need to know how to use one I can help or Google can :)

---

### Post by Whiffle on 2008-03-11
There is an application for windows that does this actually.  I forgot what it is, but I've posted it on this forum before the last time this came up.  I found it through google.

---

### Post by Whiffle on 2008-03-11
Here ya go:

[http://www.cs.unm.edu/~dmohr/grub.php](http://www.cs.unm.edu/~dmohr/grub.php)

---

### Post by doorknob60 on 2008-03-11
Wow, looks like a nice program (and easier than the batch files for sure). I might have to try that out myself :) Thanks for the find.

---

### Post by pytheas22 on 2008-03-11
Thanks for the link.  It might turn out to be useful, although as I said, I would ideally like to find a solution that doesn't involve changing any grub values if possible.  I am also not sure if the GUI program will be realistic for my needs, because the people using the computers can sometimes be less than competent--it would be better for them to just click something and have the computer automatically reboot to Windows, as asking them to select a partition, even if the names in the menu were explicit, is more than they can be trusted with.  So it might come down to writing a batch script.  For my personal use, however, this GUI looks nice.

In the meantime, I am still open to other methods of rebooting into a specified partition other than changing the default value in grub.

---

### Post by Whiffle on 2008-03-12
Well, that GUI is written in python, so you could modify it to say whatever you want really.

---

