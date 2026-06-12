---
title: "Crash x3"
date: 2007-12-24
forum: General Help
---

### Post by DonDodge on 2007-12-24
Very new installation here.

I've had this particular crash three times now. When it happens, my screen goes black and the monitor message that says it's going into power off mode flashes up. After this, all display functions are finished. No way to get any type of video to display again (that I can find) and the only way out seems to be a hard reset.

Here's what I know about it so far. Every time it happens, Firefox is running. The first two times I was doing huge system download/updates with Update Manager. The crash came when I told Firefox to do something. It started after I upgraded to 2.0.0.11.

This latest time it happened, there was no updating going on and no activity in Firefox and no internet connection. It happened when I pushed the "Switch User" button to restart the computer.

Every time it happens I find similar lines in my system log:
--------------------------------
Dec 24 08:45:59 d-desktop kernel: [ 5906.317751] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 24 08:45:59 d-desktop kernel: [ 5906.317765] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 24 08:45:59 d-desktop kernel: [ 5906.321399] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 24 08:45:59 d-desktop kernel: [ 5906.321408] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
---------------------------------
Anyone know what may be causing this and how I can fix it? I suspect Firefox but it does no good to run Firefox from a terminal to check for errors because I'd never get to see the terminal output after the crash occurred.unless I can regain display function.

---

### Post by ayoli on 2007-12-24
Did you try to boot with noacpi or nopic options ? sometimes it can avoid this kind of problem.
find in /boot/rgub/menu.lst a line like this (inthe block taht b oot the kernel you use)
```
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=fd99bc57-4875-467e-94e8-ff583b97d3c9 ro quiet splash
```
and add at the end this:
```
noapic
```
or this:
```
noacpi
```

---

### Post by DonDodge on 2007-12-24
I'm trying the noapic first.

I've seen these parameters discussed a lot, mostly in conjunction with installing from the live cd, etc. but I don't know what they do. Can you please tell me?

---

### Post by ayoli on 2007-12-24
To be (very) simple, sometimes it resolves some IRQ problems and some hardware problems.

---

### Post by DonDodge on 2007-12-24
Well, noapic didn't work.. I added that parameter and rebooted after I read your post. It didn't crash until just now after I read your latest post. I'll try noacpi now.

---

### Post by DonDodge on 2007-12-24
noacpi didn't work either. The computer stayed functional for a few hours and got about 30 mb of packages downloaded before it crashed in the exact same manner.

Are there any other log files that would help diagnose this problem?

---

### Post by DonDodge on 2007-12-26
Bump

This ubuntu is about as stable and reliable as a pocket full of water. I've had six of these crashes in the last few days which is about six more crashes than I've had in the 4+ years I've been running XP on this computer.. 

Is there any way to trap an error and figure our what causes this thing to continually crash like this? Are there any crash logs or bug traps hidden away somewhere? I can't really find squat in the system logs and there's no way to examine errors in a terminal after you have to do a hard reset.

Any help from the wizards around here now that Christmas is over?

---

### Post by tgalati4 on 2007-12-26
Do you have a wonky joystick plugged into the computer?  Or perhaps a multi-media keyboard?  Those keycode errors normally aren't serious.  You just need to discover what those keycodes are and reprogram them.  I had to do that with an HP multimedia keyboard that had a volume dial and 21 additional keys.

Gutsy is running OK on my Pentium D (2 core), 2.9 GHz machine with i945gm graphics chipset.  No strange crashes yet.

I assume that you ran memtest for 30 passes?

Did you perform an upgrade install or a fresh install?

---

### Post by DonDodge on 2007-12-27
No joystick at all. I have a M$ wireless keyboard and mouse that I've been using for a few years now. I don't use the multimedia or special function keys and rarely use any of the "F" keys, even in windoze. I don't need any of them in Ubuntu. The only thing I'm using in Ubuntu are the QWERTY keys and the numeric keypad. I don't know that any of those are even programmable.

I left the boot up memtest running for about 6 hours Tuesday. When I turned the monitor back on to see about it, it was still running tests. I left it going for a while and it just kept running test after test with no indication of errors. Out of curiosity, I pushed (c)configuration and the system rebooted.

I did a fresh install on a brand new partition of a 160 gb WD hdd that's only a few months old. 

The only problem I ever have with this computer is I customarily reboot every week or two when windoze increases the size of my swap file. 

The mobo is an Aopen AX3S with a PIII 933 Mhz and Intel 815 chipset with 256 mb of ram. I upgrade the main hdd every few years and move the ex-main down to a slave. Otherwise, the computer is the same as it's been for many years.

I looked back through old syslog files and can't really find any common denominator leading to the crashes. Even though I always see instances of the "atkbd.c: Unknown key released" lines before a crash, I've learned they do not necessarily precede a crash. I searched syslog(0) from yesterday and found 48 instances of that line but I had no crashes over the 24 hour span covered by that log.

I wish I'd recorded all the actual crash times so I could go back to them in the logs but I see this prior to what I believe to be some of the crashes:

Dec 24 20:55:25 d-desktop exiting on signal 15

But then again, I see many instances of that line that don't precede a crash.

I also see this prior to what may be crashes but then again, I see it scattereed throughout the logs, same as the other stuff.

Dec 27 07:34:40 d-desktop dhclient: No DHCPOFFERS received.
Dec 27 07:34:40 d-desktop dhclient: No working leases in persistent database - sleeping.

These are the syslog entries of the 5 minutes leading up to the most recent crash which occurred earlier this morning when I was typing out the original iteration of this post. Following this will be the minutes leading up to the positively identified crash I reference in my original post.

Dec 27 07:29:22 d-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 27 07:29:30 d-desktop dhclient: No DHCPOFFERS received.
Dec 27 07:29:30 d-desktop dhclient: No working leases in persistent database - sleeping.
Dec 27 07:30:01 d-desktop /USR/SBIN/CRON[8754]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Dec 27 07:30:03 d-desktop anacron[8778]: Anacron 2.3 started on 2007-12-27
Dec 27 07:30:03 d-desktop anacron[8778]: Normal exit (0 jobs run)
Dec 27 07:30:22 d-desktop kernel: [ 2093.119892] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 27 07:30:22 d-desktop kernel: [ 2093.119905] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 27 07:30:28 d-desktop kernel: [ 2098.653575] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:30:28 d-desktop kernel: [ 2098.653589] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:30:34 d-desktop kernel: [ 2105.138800] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:30:34 d-desktop kernel: [ 2105.138816] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:30:44 d-desktop kernel: [ 2115.307372] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:30:44 d-desktop kernel: [ 2115.307385] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:30:58 d-desktop kernel: [ 2128.996611] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:30:58 d-desktop kernel: [ 2128.996626] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:31:04 d-desktop kernel: [ 2135.456814] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:31:04 d-desktop kernel: [ 2135.456828] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:31:19 d-desktop kernel: [ 2150.453247] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:31:19 d-desktop kernel: [ 2150.453262] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:31:22 d-desktop kernel: [ 2153.272694] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 27 07:31:22 d-desktop kernel: [ 2153.272710] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 27 07:31:26 d-desktop kernel: [ 2156.596009] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:31:26 d-desktop kernel: [ 2156.596023] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:31:34 d-desktop kernel: [ 2165.546090] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:31:34 d-desktop kernel: [ 2165.546103] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:31:42 d-desktop kernel: [ 2172.745613] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:31:42 d-desktop kernel: [ 2172.745627] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:31:51 d-desktop kernel: [ 2182.150538] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:31:51 d-desktop kernel: [ 2182.150554] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:31:56 d-desktop kernel: [ 2187.444449] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:31:56 d-desktop kernel: [ 2187.444464] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:32:05 d-desktop kernel: [ 2196.252000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:32:05 d-desktop kernel: [ 2196.252016] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:32:15 d-desktop kernel: [ 2206.219877] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:32:15 d-desktop kernel: [ 2206.219891] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:32:32 d-desktop kernel: [ 2223.156570] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 27 07:32:32 d-desktop kernel: [ 2223.156584] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 27 07:32:32 d-desktop kernel: [ 2223.160869] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:32:32 d-desktop kernel: [ 2223.160882] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:32:56 d-desktop kernel: [ 2247.309001] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:32:56 d-desktop kernel: [ 2247.309015] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:33:01 d-desktop kernel: [ 2251.934307] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:33:01 d-desktop kernel: [ 2251.934320] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:33:10 d-desktop kernel: [ 2261.023341] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:33:10 d-desktop kernel: [ 2261.023355] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:33:21 d-desktop kernel: [ 2272.059332] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:33:21 d-desktop kernel: [ 2272.059346] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:33:26 d-desktop kernel: [ 2277.343025] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:33:26 d-desktop kernel: [ 2277.343038] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:33:35 d-desktop kernel: [ 2286.034354] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 27 07:33:35 d-desktop kernel: [ 2286.034368] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 27 07:33:38 d-desktop kernel: [ 2288.647507] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:33:38 d-desktop kernel: [ 2288.647524] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:33:44 d-desktop kernel: [ 2294.934714] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:33:44 d-desktop kernel: [ 2294.934729] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:34:09 d-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Dec 27 07:34:13 d-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Dec 27 07:34:14 d-desktop kernel: [ 2325.209067] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:34:14 d-desktop kernel: [ 2325.209081] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:34:20 d-desktop kernel: [ 2331.411565] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 07:34:20 d-desktop kernel: [ 2331.411580] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 07:34:22 d-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Dec 27 07:34:40 d-desktop dhclient: No DHCPOFFERS received.
Dec 27 07:34:40 d-desktop dhclient: No working leases in persistent database - sleeping.
Dec 27 07:37:22 d-desktop syslogd 1.4.1#21ubuntu3: restart.

----------------------------------------------------------------------
Dec 24 08:39:43 d-desktop kernel: [ 5531.075737] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 24 08:39:43 d-desktop kernel: [ 5531.075750] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 24 08:42:39 d-desktop kernel: [ 5707.204548] Inbound IN=ppp0 OUT= MAC= SRC=221.208.208.83 DST=4.254.144.214 LEN=486 TOS=0x00 PREC=0x00 TTL=45 ID=0 DF PROTO=UDP SPT=46580 DPT=1027 LEN=466 
Dec 24 08:43:12 d-desktop kernel: [ 5739.338631] Inbound IN=ppp0 OUT= MAC= SRC=213.45.40.138 DST=4.254.144.214 LEN=378 TOS=0x00 PREC=0x00 TTL=55 ID=36841 PROTO=UDP SPT=30851 DPT=1026 LEN=358 
Dec 24 08:45:05 d-desktop pppd[7270]: Terminating on signal 15
Dec 24 08:45:05 d-desktop pppd[7270]: Connect time 10.2 minutes.
Dec 24 08:45:05 d-desktop pppd[7270]: Sent 74124 bytes, received 698130 bytes.
Dec 24 08:45:59 d-desktop kernel: [ 5906.317751] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 24 08:45:59 d-desktop kernel: [ 5906.317765] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 24 08:45:59 d-desktop kernel: [ 5906.321399] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 24 08:45:59 d-desktop kernel: [ 5906.321408] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 24 09:09:04 d-desktop syslogd 1.4.1#21ubuntu3: restart.

---

### Post by DonDodge on 2007-12-27
Just after I pushed the "Submit Reply" button for my previous post, the thing crashed again before the forum page completed loading. The very last input to the computer was a left click of the mouse. Previous to that was another left click on the "Preview Post" button.

I think maybe I should reinstall Firefox or try to revert to the version that came on the Ubuntu Live CD. It all seems to have something to do with Firefox and didn't begin until I did the upgrade.

Here are the syslog lines for the minutes leading up to that event and ending with my push of the reset button.
-------------------------------------------
Dec 27 09:53:29 d-desktop kernel: [ 8229.153212] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 09:53:29 d-desktop kernel: [ 8229.153226] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 09:53:36 d-desktop kernel: [ 8236.149466] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 09:53:36 d-desktop kernel: [ 8236.149480] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 09:53:41 d-desktop kernel: [ 8241.579232] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 09:53:41 d-desktop kernel: [ 8241.579246] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 09:53:59 d-desktop kernel: [ 8259.469795] Inbound IN=ppp0 OUT= MAC= SRC=218.10.137.139 DST=4.235.90.244 LEN=485 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=33856 DPT=1027 LEN=465 
Dec 27 09:55:02 d-desktop kernel: [ 8322.773867] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 27 09:55:02 d-desktop kernel: [ 8322.773881] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 27 09:56:18 d-desktop kernel: [ 8398.078694] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 27 09:56:18 d-desktop kernel: [ 8398.078708] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 27 09:56:23 d-desktop kernel: [ 8403.412958] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 09:56:23 d-desktop kernel: [ 8403.412973] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 09:56:27 d-desktop kernel: [ 8407.534131] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 09:56:27 d-desktop kernel: [ 8407.534144] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 09:56:32 d-desktop kernel: [ 8411.917031] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.198 DST=4.235.90.244 LEN=485 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=54899 DPT=1026 LEN=465 
Dec 27 09:56:32 d-desktop kernel: [ 8412.332321] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 09:56:32 d-desktop kernel: [ 8412.332334] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 09:56:40 d-desktop kernel: [ 8420.823358] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Dec 27 09:56:40 d-desktop kernel: [ 8420.823371] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Dec 27 09:56:45 d-desktop kernel: [ 8425.586573] Inbound IN=ppp0 OUT= MAC= SRC=24.64.191.243 DST=4.235.90.244 LEN=512 TOS=0x00 PREC=0x00 TTL=71 ID=966 PROTO=UDP SPT=18723 DPT=1026 LEN=492 
Dec 27 09:56:45 d-desktop kernel: [ 8425.642553] Inbound IN=ppp0 OUT= MAC= SRC=24.64.191.243 DST=4.235.90.244 LEN=512 TOS=0x00 PREC=0x00 TTL=71 ID=967 PROTO=UDP SPT=18723 DPT=1027 LEN=492 
Dec 27 09:56:45 d-desktop kernel: [ 8425.690528] Inbound IN=ppp0 OUT= MAC= SRC=24.64.191.243 DST=4.235.90.244 LEN=512 TOS=0x00 PREC=0x00 TTL=71 ID=968 PROTO=UDP SPT=18723 DPT=1028 LEN=492 
Dec 27 09:57:00 d-desktop kernel: [ 8440.255904] Inbound IN=ppp0 OUT= MAC= SRC=221.208.208.104 DST=4.235.90.244 LEN=486 TOS=0x00 PREC=0x00 TTL=45 ID=0 DF PROTO=UDP SPT=40914 DPT=1026 LEN=466 
Dec 27 09:57:31 d-desktop kernel: [ 8471.395268] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 27 09:57:31 d-desktop kernel: [ 8471.395281] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 27 09:58:55 d-desktop kernel: [ 8555.663004] Inbound IN=ppp0 OUT= MAC= SRC=221.208.208.104 DST=4.235.90.244 LEN=486 TOS=0x00 PREC=0x00 TTL=45 ID=0 DF PROTO=UDP SPT=41530 DPT=1027 LEN=466 
Dec 27 09:59:22 d-desktop kernel: [ 8582.770125] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.196 DST=4.235.90.244 LEN=485 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=59663 DPT=1026 LEN=465 
Dec 27 10:00:21 d-desktop kernel: [ 8640.887566] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.196 DST=4.235.90.244 LEN=485 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=60028 DPT=1027 LEN=465 
Dec 27 10:01:07 d-desktop syslogd 1.4.1#21ubuntu3: restart.

---

### Post by tgalati4 on 2007-12-27
Perhaps your wireless keyboard is not playing nice with Ubuntu.  Try a standard, wired keyboard and mouse.  Are the batteries weak in your keyboard/mouse?  They could be sending spurious signals that are upsetting the keyboard scan.

If the keyboard scan chip loses syncronization, it can often crash the computer.  Try removing your keyboard or mouse in Windows and see what happens.

Linux can sometimes recover from a mouse or keyboard removal, but it can also lockup.  The serial bus that these devices run on are not hot-plug devices.  Any disruption can cause serious problems.

Try declocking your Aopen motherboard.  Go for half speed.  Aopen are not the best quality.  (I'm using one right now, i945gm chipset).  Aopen tends to undercool their support chips and when they get toasty they get wonky.  Put your finger on either the north or southbridge and tell me it's not toasty.  See if you can keep it on the chip for 30 seconds.  If not then it's toasty.

---

### Post by DonDodge on 2007-12-27
Thanks for the ideas.

I can disconnect the receiver from the PS2 ports on the computer either in windoze or ubuntu and reconnect them after a while with no problems at all. I always run the mouse until the batteries are dead, then I take it out to my shop and replace them with freshly recharged batteries. Upon return, the mouse works again. I can also remove the keyboard in and out of range while holding down a key to type characters. Same with the mouse. I can leave them both in another room and bring them back in and they both begin functioning as soon as they get within 8-10' of the receiver.

My system temp runs 82-84 ° F and CPU temp 77-78° F when it's 75° in my office. The hottest chip I can find on the motherboard (with an infrared gun)  is 106° Most are in the mid- 80's.

I don't think this is anything like a hardware problem. I think it's a ubuntu/Firefox  mental instability problem :) I reinstalled Firefox today and haven't had another crash since then but I've been back into windoze several times to get some real work done. 

Declocking a computer to make it run an OS just seems silly. I really wonder if this ubuntu is really ready for primetime. It'is definitely a lot better and more user friendly than the old redhat and mandrake distros but after reading hundreds or posts that are largely about nothing but problems from here to the moon and  back, it still appears to be an OS destined to fit into a very tiny niche. 

I can't believe Dell has the stones to sell ubuntu computers on the open market. Especially with the level of expertise in their tech support branch. Hopefully, they have a special division for ubuntu sales.

---

### Post by DonDodge on 2007-12-28
Funny thing about these crashes: Eight out of nine have occurred when I executed an action on this website. The other one happened as I tried to restart the computer after disconnecting from ubuntuforums.

It just crashed again when I executed a search here.

---

