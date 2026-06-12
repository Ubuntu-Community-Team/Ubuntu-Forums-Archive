---
title: "SysRq woes under Hoary"
date: 2007-08-30
forum: General Help
---

### Post by Blueshell on 2007-08-30
I've suddenly started having random machine freezes under Hoary and I'm trying to track them down.  (Yes, I know this release is ancient, but it's not going to be updated today---especially with the freezes.)  I have -one- suggestive possibly-memory-related entry in a logfile which I can attach to this (out of several freezes) if anyone wants to try diagnosing it, but I'd like to actually be able to use SysRq to debug this---especially since six hours of MemTest86 hasn't shown a single error  But so far, I can't, because I can't get SysRq to work.  Here are the problems:

I added this to /boot/grub/menu.lst:

serial --unit=0 --speed=115200 --word=8 --parity=no --stop=1
terminal --timeout=5 serial console

Using -this-

  kernel        /boot/vmlinuz-2.6.10-5-k7 root=/dev/hda2 ro quiet splash console=tty0 console=ttyS0,115200n8

instead of this

  kernel        /boot/vmlinuz-2.6.10-5-k7 root=/dev/hda2 ro quiet splash

locks me out of X (nothing echoes when I type my username), whether or not I've hit a key on either the real keyboard or the serial console at the start of boot when it's saying "Hit any key to continue".

Using minicom on the serial terminal, doing C-A F (to send a break)  and then typing any SysRq command key appears ignored; the character just echoes.  I found a single web page of someone else complaining about this, with no answer to him.  Trying to type [Alt][Shift][PrtSc|SysRq]<key> does nothing, and doing <key> separately just echoes that key.  (The [Shift] there is because SysRq is a shifted character on my laptop's keyboard.)

Assuming I don't have the console=tty0 line above, even if I hit return in the minicom window, it isn't treated as the console once the kernel boots.  I can't actually -see- any kernel output on my main screen unless I -do not- log into X!  If I just C-A-F1 -before- I log in, it leaves that screen in textmode, so I can see what I'm doing.  If I've already logged in,C-A-F1 shows garbage 'cause it's no longer in textmode.  Once I can see what I'm doing, "echo 9 > /proc/sysrq-trigger" (documented only in a single IRC page!) will allow a later "echo t > /proc/sysrq-trigger" to actually print a tasklist dump (instead of just saying "Show Tasks"), -but- "echo p" does -not- print a regdump and instead just says "Show Regs"!

But all of these go to the LCD, -not- to the serial console.  If I use the "console=tty0" line above, they -do- go to the serial console, but then I can't actually -use- the machine's primary console under X!  The keyboard (ordinary PS2 keyboard) is just completely ignored, which means I can't log in, I can't use C-A-F1 to switch to another VT, nothing.

If I could just get the main keyboard to be recognized if booting w/the "console=tty0" kernel line, then I could hit return at the start of boot on the serial console and at least have a chance in hell of seeing whatever kernel oops is killing the machine.  But since I can't -use- the machine in that state, it's pointless.

All in all, a huge steaming pile of horrible bugginess.

Do these bugs sound familiar to anyone?  If they're fixed in later releases, then maybe upgrading will help me, but I'd rather not upgrade right this second on this machine (and a failure in the middle will screw me pretty badly).  Is there some undocumented setting or two that I should be using to get X unwedged when using the serial console?

---

