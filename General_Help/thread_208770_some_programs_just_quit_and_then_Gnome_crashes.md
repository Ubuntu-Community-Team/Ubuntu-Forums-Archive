---
title: "some programs just quit and then Gnome crashes"
date: 2006-07-04
forum: General Help
---

### Post by will1384 on 2006-07-04
It started a few day ago - It told me I had some up dates, so
I installed them  - when I rebooted it acted like the hard disk was bad 
and just stop at the boot manager - so I shut it off and restarded it
and it worked just fine, did not think about it much after that - untill 
the trash can crashed - it poped up a window telling me it crashed,
I tell it not to reload it, and bam, every thing on the screen is gone,
except the wall paper, I have to hold the power button down for a
few seconds for it to shut off, I restart it, and again it acted like the
hard disk was bad and stop at the boot manager, so again, I shut it
off and restarded it and worked just fine, let it run over night

this time it was the sticky notes program, I told it to re load
and it still killed gnome

I can shut it down and restart over and over and it works just fine
- it must be when its running over night

here is some of my system log - or the part I think is odd
- I removed the MAC and IP

Jul  1 00:51:12 localhost syslogd 1.4.1#17ubuntu3: restart.
Jul  1 00:51:12 localhost anacron[7364]: Job `cron.daily' terminated
Jul  1 00:51:12 localhost anacron[7364]: Normal exit (1 job run)
Jul  1 00:51:40 localhost kernel: [4295168.491000] Inbound IN=eth0 OUT= MAC=----------------------------------------- SRC=166.173.157.110 DST=---.---.---.--- LEN=48 TOS=0x08 PREC=0x80 TTL=126 ID=16991 DF PROTO=TCP SPT=4876 DPT=445 WINDOW=33840 RES=0x00 SYN URGP=0 
Jul  1 00:51:42 localhost kernel: [4295170.157000] Inbound IN=eth0 OUT= MAC=----------------------------------------- SRC=166.173.157.110 DST=---.---.---.--- LEN=48 TOS=0x08 PREC=0x80 TTL=126 ID=17059 DF PROTO=TCP SPT=4876 DPT=445 WINDOW=33840 RES=0x00 SYN URGP=0 
Jul  1 00:52:02 localhost kernel: [4295190.097000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jul  1 00:52:02 localhost kernel: [4295190.097000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jul  1 00:52:03 localhost kernel: [4295191.069000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Jul  1 00:52:03 localhost kernel: [4295191.069000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jul  1 00:52:04 localhost kernel: [4295191.925000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jul  1 00:52:04 localhost kernel: [4295191.925000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jul  1 00:52:04 localhost kernel: [4295192.034000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Jul  1 00:52:04 localhost kernel: [4295192.034000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Jul  1 00:52:04 localhost kernel: [4295192.142000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Jul  1 00:52:04 localhost kernel: [4295192.142000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.


that goes on all night


any ideas

sorry if this is a repeat post, a few days ago I tried posting before
I left for the weekend, and it said they were working on the system
or some thing - I looked but could not find my post today

---

### Post by will1384 on 2006-07-06
I had firestarter and had disabled every way to log in remotley,
and had a good password - so I did not think it was a hacker

well I took this linux box off my DMZ - and put it under the router 
firewall and BAM!! it has not happened again


whats up with that

---

