---
title: "Need to edit file without fully booting, Gutsy"
date: 2007-11-09
forum: General Help
---

### Post by Poliwop on 2007-11-09
I'm very new to Linux and recently installed Gutsy Gibbon on my new Gateway laptop (AMD dual 64).  It installed fine and I was liking it very much, but I tried to edit a file I apparently should not have edited (after I read this: [https://launchpad.net/bug59695.html](https://launchpad.net/bug59695.html) ) and now the laptop will not boot fully.  How far it gets varies.  Sometimes it barely gets into the loading screen (where it shows "Ubuntu" and the loading bar) and sometimes it finishes that and doesn't freeze until right before it should show the login screen.

This did not start until a few days after the edit, but during those days it started freezing some, which was unusual.

What I want to do then is to just go back and edit the file, if possible.  I've got the Gutsy disc and have tried a few different things but my knowledge of Linux is very limited.

In case it matters (and it probably does) the file I edited was /etc/laptop-mode/laptop-mode.conf.
I set:
CONTROL_HD_POWERMGMT=1

Thanks in advance for any help, I'd love to get Ubuntu back up and running.

---

### Post by Metacarpal on 2007-11-10
Try this:

Cold-start your computer (that is, start with it completely off)

When you see the message that Grub is loading, then a countdown starts, hit Esc

Select "recovery mode" for your current kernel (should be the second one down)

If the Ubuntu gods are not entirely angry with the change you have made, this will take you to a text-only command-line interface.

Once there, type:
```
vim /etc/laptop-mode/laptop-mode.conf
```

You should now see the contents of that file on your screen.  Then hit
```
a
```

Yes, that's a literal, single, lower-case 'a'.  You should now see "INSERT" at the bottom-left of the screen.

Use your arrow keys to scroll down to the line you changed, and change it back.

Then hit
```
Ctrl+w
``` (Ctrl and w at the same time)
Then
```
Ctrl+q
```

That will save and exit from the file.
Then type
```
shutdown -r now
```

which will reboot your system.


If you can't get to the command-line using recovery mode, you'll be needing to boot from the LiveCD, mount your hard disk, and edit the files there.

---

### Post by Maestro23 on 2007-11-10
If using **vim** is too hard for you in the steps posted above, you can use the **nano** text editor.

---

### Post by Poliwop on 2007-11-14
Thanks for the help.

I tried using the live CD to edit it.  I figured out how to mount the hard disk and I found the file, but it won't let me edit it.  How can I log in as root?

It won't let me edit it the other way because every time I boot I have to edit the boot menu commands and add the "noapic" command, or I get an error message.  For some reason it doesn't work in recovery mode.

Thanks,

---

