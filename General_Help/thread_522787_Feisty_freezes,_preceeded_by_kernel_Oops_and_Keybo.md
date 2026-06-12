---
title: "Feisty freezes, preceeded by kernel Oops and Keyboard/Mouse irresponsiveness"
date: 2007-08-11
forum: General Help
---

### Post by TwanGoosen on 2007-08-11
Hi,

I installed Ubuntu 7.04 Feisty Fawn on my Acer TravelMate 2310 notebook which previously contained Windows XP and ran without any (major) problems. Everything seems to be configured fine now, except for the internal WiFi, which is not recognized by HAL.

I'd be quite happy with all this if it weren't for the annoying freezes that seem to happen at random times between five and thirty minutes after startup. 

What happens (always) is the following: 

First, the keyboard is no longer responsive. None of the keys seem to do anything at all, including CTR-ALT-Fx, so I cannot switch between terminals anymore either. 

Then, after a while, the mouse buttons (of my notebook's touchpad) get unresponsive too, so all that can be done is move the cursor around. Finally, after another while, the touchpad is no longer responsive at all. The system as a whole does not seem to freeze.

In addition, the following (or something similar) is dumped to the terminal right before the keyboard stops working:

> 	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000] Oops: 0002 [#1]

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000] SMP 

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000] CPU:    0

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000] EIP:    0060:[free_block+145/304]    Tainted: P      VLI

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000] EFLAGS: 00010082   (2.6.20-16-generic #2)

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000] EIP is at free_block+0x91/0x130

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000] eax: dfc1fbc0   ebx: 00000003   ecx: ed806800   edx: 00000001

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000] esi: f47e7880   edi: dfffd3c0   ebp: dfffc260   esp: c18b1f00

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000] ds: 007b   es: 007b   ss: 0068

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000] Process events/0 (pid: 5, ti=c18b0000 task=c189f560 task.ti=c18b0000)

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000] Stack: 00000001 00000000 00000005 dffff6c0 00000003 dfffc254 dfffc240 00000005 

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000]        dfffd3c0 c01728bf 00000000 dffff6c0 dfffd3c0 dffff6c0 c1787a00 00000292 

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000]        c0173e41 00000000 00000000 c1787a04 c185c5c0 c0137314 00000000 c18b1f88 

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000] Call Trace:

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000]  [drain_array+95/208] drain_array+0x5f/0xd0

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000]  [cache_reap+129/320] cache_reap+0x81/0x140

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000]  [run_workqueue+148/320] run_workqueue+0x94/0x140

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000]  [cache_reap+0/320] cache_reap+0x0/0x140

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000]  [worker_thread+327/368] worker_thread+0x147/0x170

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000]  [default_wake_function+0/16] default_wake_function+0x0/0x10

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000]  [worker_thread+0/368] worker_thread+0x0/0x170

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000]  [kthread+186/240] kthread+0xba/0xf0

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000]  [kthread+0/240] kthread+0x0/0xf0

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000]  =======================

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000] Code: 46 c0 8b 02 f6 c4 40 0f 85 a3 00 00 00 8b 02 84 c0 0f 89 a6 00 00 00 8b 72 1c 8b 44 24 28 8b 54 24 0c 8b 7c 82 34 8b 16 8b 46 04 <89> 42 04 89 10 c7 46 04 00 02 20 00 c7 06 00 01 10 00 8b 5c 24 

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000] EIP: [free_block+145/304] free_block+0x91/0x130 SS:ESP 0068:c18b1f00

	Message from syslogd@acer at Sat Aug 11 07:08:37 2007 ...
	acer kernel: [  206.816000]  [kernel_thread_helper+7/16] kernel_thread_helper+0x7/0x10


Seems to me something goes wrong at kernel level. So, would it be a good idea to go and compile me a new one? If so, are there any specific issues I should focus on while configuring it? Could the problem with the WiFi for example be related?

There are a couple of things I did while trying to localize the problem that did *not* eliminate the freezes:
- Remove one of the memory chips (I had 256MB and 1024MB combined, removed the 256)
- Set display driver for Xorg to VESA instead of SiS
- Use Window Maker instead of Gnome

The installation is as good as fresh, i.e. no kernel upgrades or other major changes. I did let the system execute the automatic updates it suggested and installed some apps (Thunderbird, gmail-notify, and such).

I'd really like to fix this problem, so any help would be greatly appreciated.
Twan Goosen

---

### Post by TwanGoosen on 2007-08-11
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/bugs/12483](https://launchpad.net/bugs/12483) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I think I found its cause: when I remove the battery from the laptop (leaving the laptop connected to the power socket), no freezes occur. Probably [https://launchpad.net/bugs/12483](https://launchpad.net/bugs/12483) , although when the freezes occur the computer is not necessarily 'on battery power', since it was always connected to the socket. I'll go and try to disable laptop mode.

---

