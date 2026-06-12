---
title: "Ubuntu 14.10 long boot after upgrade from 14.04."
date: 2015-02-13
forum: General Help
---

### Post by Silneus on 2015-02-13
Recently I've upgraded from 14.04 and my boot time grew upt to over 80 s!

It's even longer than windows 7!

My bootchart:
[http://s7.postimg.org/6udl4q0ob/bootchart.png](http://s7.postimg.org/6udl4q0ob/bootchart.png)

My dmesg:
[http://speedy.sh/3Eqkz/boot](http://speedy.sh/3Eqkz/boot)


Sometimes during boot I see and error like this:
[   40.391853] init: Error while reading from descriptor: Broken pipe

And when I log out:
Feb 13 01:38:51 rafal-K53TK kernel: [   68.116627] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
Feb 13 01:38:51 rafal-K53TK kernel: [   68.116635] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CE9C (len 62, WS 0, PS 0) @ 0xCEB8
Feb 13 01:38:56 rafal-K53TK kernel: [   73.118798] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
Feb 13 01:38:56 rafal-K53TK kernel: [   73.118806] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CE9C (len 62, WS 0, PS 0) @ 0xCEB8
Feb 13 01:38:57 rafal-K53TK NetworkManager[1211]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Feb 13 01:39:01 rafal-K53TK kernel: [   78.120967] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
Feb 13 01:39:01 rafal-K53TK kernel: [   78.120976] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CE9C (len 62, WS 0, PS 0) @ 0xCEB8
Feb 13 01:39:06 rafal-K53TK kernel: [   83.123139] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
Feb 13 01:39:06 rafal-K53TK kernel: [   83.123147] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CE9C (len 62, WS 0, PS 0) @

---

