---
title: "Grub, 8800 GTX, and vga modes."
date: 2007-06-01
forum: General Help
---

### Post by verahsa on 2007-06-01
Coming back to Ubuntu, again. I still triple boot to Vista and XP (and until Linux supports the games I play either natively or with something that's significantly easier than Wine or Cedega, it'll stay that way), but I decided, as usual for me, to give a whack at it again. I won't go over the reasons for all of it. :)

Hardware setup, for information purposes.
Core 2 Duo 6300 (1.86 GHz)
EVGA 8800 GTX
2 GB ram, 3 186 GB hdds, 2 dvdrws, Audigy 2, 680i motherboard (ecs).

Running Feisty Fawn with kernel 2.6.20-16-generic, Xorg with the nvidia driver (version 9755). 

I had a few issues getting the system to boot properly, ended up using EasyBCD 1.6, among other things. So, got that done. Had a fun time trying to get my MX Revolution to cooperate (btnx did not cooperate in the least, for whatever reason, so I fell back on the udev event9 solution along with xbindkeys). After that, installing the nvidia driver took a -wee- bit of tweaking, but nothing extremely difficult (three or four restarts, no big deal). There are still a few things I'd like to fix, though. :) 

Here are the issues at hand. 

First, I know I'm forgetting something remarkably simple, but how do I get xbindkeys to run automatically when the system first starts up? 

Second, under ~/.xbindkeysrc, where can I find a listing of what to type under any given xvkbd -xsendevent for keypresses?

Third, During boot time, if I set vga=795, everything's peachy. If I set vga=799, I get the "the vga mode you selected isn't supported, here's a list of -really bad- ones to punish you for not knowing better, pick one." Now, I know for a fact both my monitor & video card support 1600x1200, but for whatever reason grub or initrd or whatever won't accept it. What do I change in grub, or elsewhere, so I get 1600x1200 for my -console- as well as my Xorg desktop? And no, I won't be disabling my splash screen. It's nice, and I know there's got to be a way to get it working. (I'm a very firm believer in getting it working without making sacrifices.)

I think that covers it for the moment. 

Information you guys might want:

The relevant menu.lst entry
```
title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=1d60048f-1616-4a87-aaf4-bd70ab818419 ro quiet splash vga=795
initrd          /initrd.img-2.6.20-16-generic
quiet
savedefault

```

The guessed-at .xbindkeysrc
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9
"/usr/bin/xvkbd -xsendevent -text "\[Ctrl_L]\[PageUp]\""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Ctrl_L]\[PageDown]\""
  m:0x0 + b:7
"/usr/bin/xvkbd -xsendevent -text "\[Ctrl_L]\[Alt_L]\[Left]\""
  m:0x0 + b:15
"/usr/bin/xvkbd -xsendevent -text "\[Ctrl_L]\[Alt_L]\[Left]\""
  m:0x0 + b:13

```

If you need more information, don't hesitate to ask, I'll get back to it as soon as possible. Thanks for your assistance!

---

### Post by MoLE on 2007-06-09
Phew!  Sounds like it was all a bit of a chore.  I must admit I've never had anywhere near the level of difficulty that you seem to have had, but I'm usually several generations behind in the hardware stakes too, so that helps.

I'm pretty sure I can answer your first two questions.

If you go to System --> Preferences --> Sessions, you can add xbindkeys to the startup programs that are already there.

It looks like you're correct with the xbindkeys config file.  All the detail on how to set it up is in the [man page]("http://www.die.net/doc/linux/man/man1/xbindkeys.1.html"), as far as I can see.

```
man xbindkeys
```

---

