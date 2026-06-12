---
title: "Boot problem -  'loadkeys' hangs"
date: 2007-09-11
forum: General Help
---

### Post by pandu.rs on 2007-09-11
I am using ubuntu 7.04 (feisty fawn) at home. My ubuntu installation does not boot for the past 3 days (but i am able to successfully boot using the LiveCD).

When booting ubuntu from the hard disk (recovery mode), the system is getting hung after printing 'Setting preliminary keymap ...'

On debugging, i figured out the following items
1. /etc/init.d/keyboard-setup is invoked from runlevel S (rcS.d)
2. This invokes 'setupcon'
3. setupcon invokes ckbcomp and then loadkeys (and it is stuck after this)

In /etc/default/console-setup i have 
XKBMODEL=pc105
XKBLAYOUT=us

I could not figure out why the system hangs while running loadkeys. May be strace might help, but strace output file does not seem to be created (probably the system hangs and is unable to complete the file I/O operations?)

Any ideas/suggestions to solve this problem will be of great help to me. Thanks in advance.

---

### Post by pandu.rs on 2007-09-11
I am still stuck with this issue :(
Can anyone please help me?

---

