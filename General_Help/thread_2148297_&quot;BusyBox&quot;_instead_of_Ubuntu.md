---
title: "&quot;BusyBox&quot; instead of Ubuntu?"
date: 2013-05-24
forum: General Help
---

### Post by Cliffer on 2013-05-24
HELP!

I have no idea what this is, or how to get away from it lol
When starting up my computer today, instead of my beloved Ubuntu (12.10), I was presented with a black screen with white lettering.
All it says is

[INDENT][I]     BusyBoxv1.19.3 (Ubuntu 1:1.19.3-7ubuntu1.1) built-in shell (ash)
     Enter 'help' for a list of built-in commands[/I]
[/INDENT]
 
I tried typing 'exit' but it gave me

[INDENT][I]     (initramfs) exit
     /init: line 352: can't open /root/dev/console: no such file
     [ 2366.718769]  Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000200
     [ 2366.718769]
     [ 2366.718783]  Pid: 1, comm: init Not tainted 3.5.0-30-generic #51-Ubuntu
     [ 2366.718789]  Call Trace:[/I][I]
     [...800]   [<ffffffff816747b4>]  panic+0xba/0x1c9
     [...808]   [<ffffffff81357f5e>]  do_exit+0x81e/0x8e0
     [...816]   [<ffffffff8105837f>]  do_group_exit+03f/0xa0
     [...823]   [<ffffffff810583f7>]  sys_exit_group+0x17/0x20
     [...831]   [<ffffffff8168a029>]  system_call_fastpath+0x16/0x1b
     [...848]  panic occurred, switching back to text console
[/I][/INDENT]

What happened?
Is my HD corrupted or something?
If there's a way to fix it, I'd appreciate knowing. I just backed up all my photos, music, tax stuff, etc. onto this drive a few days ago. go figure lol

Thanks

---

### Post by galgalesh on 2013-05-24
From an older thread ([http://ubuntuforums.org/showthread.php?t=1702818](http://ubuntuforums.org/showthread.php?t=1702818)):

Busybox is a simple "shell" included in the initramfs and is used as a fall back if your system does not boot. Busybox says that your kernel is not being found on the hard drive. Could be anything from faulty hardware to a bad kernel or initramfs.

Normally you should be getting some messages before dropping into busybox. What are they?


You can do two things:
1) Boot into a live cd and try to find out if it is a hardware problem
2) Boot an older kernel and see if that works

---

### Post by Cliffer on 2013-05-26
I don't remember seeing anything before; error messages, etc.
I'm traveling at the moment, but I'll follow your advice tomorrow, and get back here.
Thanks for your response :)

---

