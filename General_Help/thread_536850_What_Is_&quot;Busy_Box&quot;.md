---
title: "What Is &quot;Busy Box&quot;?"
date: 2007-08-28
forum: General Help
---

### Post by jlacroix on 2007-08-28
I left my webserver on last night because I was working on some text files. When I came in today, the Gnome GUI was gone and I was dumped to some sort of command line with the words "Busy Box". Any idea why this would happen? This is the second time this happened, when I reboot its fine and I can't seem to reproduce this on my own.

---

### Post by Wolki on 2007-08-28
> **jlacroix said:**
> I left my webserver on last night because I was working on some text files. When I came in today, the Gnome GUI was gone and I was dumped to some sort of command line with the words "Busy Box". Any idea why this would happen? This is the second time this happened, when I reboot its fine and I can't seem to reproduce this on my own.

Busybox is a minimal shell, like bash but much less featureful and with less requirements. It's often used as an emergency shell in placed where loading a full bash is not yet possible. I'd assume your computer crashed, and during the restart a problem was found that made your computer start a busybox shell instead of completing the booting process.

---

### Post by jlacroix on 2007-08-28
Thanks for the info, that makes sense now.

Is there any way I can find out what caused it to happen?

---

### Post by Wolki on 2007-08-28
> **jlacroix said:**
> Thanks for the info, that makes sense now.

Is there any way I can find out what caused it to happen?

Maybe checking dmesg after exiting the busybox shell and finishing the boot process will provide some interesting information. I don't remember right now, but maybe a filesystem error during boot (such as from not unmounting the disk correctly) will drop you to a busybox shell? I think I recall it at least shows you some information about what happened.

To be honest, I don't know. Might be a hardware-related failure.

---

### Post by raijinsetsu on 2007-08-28
Usually it's something real bad if it dumps you to a recovery shell. For instance: if root is unmountable.
Try running "tail /var/log/messages" and "tail /var/log/dmesg" to see what's going on.

---

### Post by jlacroix on 2007-08-28
Thanks for the input guys, I looked at the messages and I'm not 100% sure what caused it. I can tell you some things that may or may not point us to an answer:

1.) The server is using the ubuntu-server kernel.
2.) Ubuntu is installed on a software-raid array for mirroring.
3.) It seems to happen every few reboots, although as of right now I can't reproduce it.

So I wonder, should I be using the ubuntu-server kernel? I am using it as a webserver, but it doesn't serve anything else. I never had a problem like this on any PC that I've installed feisty on, so I don't know if the kernel should be switched to generic or not, or if that would kill serving web pages.

---

### Post by BlackWater1 on 2008-05-03
I had the same issue. Upgraded to Hardy Heron from Gutsy. Upon booting I was thrown to the Busybox 1.1.3 light weight shell. If your stuck at this screen do the following:

Reboot, upon the GRUB boot screen select the 8.04 Hardy Heron entry and press `e'. You should come to another screen with some text on it. There is a line that states the following:

```
Kernel /boot/vmlinuz-2.6.24-16-generic root=SOME STUFF
```

Select that line and press the `e' key again. You should see this:

```
<b-09f2-4836-93ad-e5a70566438d ro quiet splash
```

Remove `quiet splash' and replace it with `all_generic_ide' and then press enter. You should be at the previous screen. Now press `b' to boot. There will be no graphical boot, with the load bar, you will soon be presented with the login screen.

Login, then open a terminal and type this:

```
~$ gksu /boot/grub/menu.lst
```

On the screen you will see all of the entries that are in the GRUB boot loader. Assuming you just installed Hardy the entry you will want will be the first one past all of the comments. You want to find the exact same line that you edited from GRUB. When you find it again replace `quiet splash' with `all_generic_ide'

If your not sure which line to edit, backup your menu.lst before you go ahead with:

```
~$ cp /boot/grub/menu_bckup.lst /boot/grub/menu.lst
```

Now save the menu.lst file and you should be able to boot into Hardy without having to constantly edit the GRUB entry during boot. I know that you will no longer get the Ubuntu Load screen with this method. But doing this allows you to play with your Hardy install until they fix the issue.

Questions message me or post here.

BlackWater

---

