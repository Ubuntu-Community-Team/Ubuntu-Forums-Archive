---
title: "dapper more and more unstable.."
date: 2006-07-03
forum: General Help
---

### Post by Ramses de Norre on 2006-07-03
Man what is going on with ubuntu?? Dapper crashes more and more.. firefox crashes a few times a day, I had two system hang ups (needed hard reboot) and one kernel panic today, a couple of days ago suddenly I couldn't open any program, all gave 'segmentation fault' untill I rebooted and a lot of things were set back to default settings.. I don't know where to start looking for the problem (/var/log/messages nor /var/log/Xorg.0.log[.old] showed me useful info) 
I'll include the lines from /var/log/messages that were saved just before the kernel panic: ```
Jul  3 13:54:41 localhost kernel: [17179648.240000] Inbound IN=ath0 OUT= MAC=00:11:6b:60:27:11:00:11:6b:21:b8:66:08:00 SRC=207.46.2.73 DST=192.168.123.106 LEN=80 TOS=0x00 PREC=0x00 TTL=113 ID=28848 PROTO=TCP SPT=1863 DPT=43164 WINDOW=65301 RES=0x00 ACK PSH URGP=0
Jul  3 14:14:05 localhost -- MARK --
Jul  3 14:34:06 localhost -- MARK --
Jul  3 14:54:06 localhost -- MARK --
Jul  3 15:14:06 localhost -- MARK --
Jul  3 15:34:06 localhost -- MARK --
Jul  3 15:54:07 localhost -- MARK --
Jul  3 16:14:07 localhost -- MARK --
Jul  3 16:34:07 localhost -- MARK --
Jul  3 16:54:07 localhost -- MARK --
Jul  3 17:14:08 localhost -- MARK --
Jul  3 17:34:08 localhost -- MARK --
Jul  3 17:54:08 localhost -- MARK --
Jul  3 18:07:55 localhost kernel: [17194842.380000] Inbound IN=ath0 OUT= MAC=00:11:6b:60:27:11:00:11:6b:21:b8:66:08:00 SRC=195.177.246.68 DST=192.168.123.106 LEN=1420 TOS=0x00 PREC=0x00 TTL=56 ID=50835 DF PROTO=TCP SPT=80 DPT=54045 WINDOW=24840 RES=0x00 ACK URGP=0
Jul  3 18:08:15 localhost kernel: [17194861.728000] Inbound IN=ath0 OUT= MAC=00:11:6b:60:27:11:00:11:6b:21:b8:66:08:00 SRC=195.177.246.68 DST=192.168.123.106 LEN=1420 TOS=0x00 PREC=0x00 TTL=56 ID=13833 DF PROTO=TCP SPT=80 DPT=54045 WINDOW=24840 RES=0x00 ACK URGP=0
Jul  3 18:08:38 localhost kernel: [17194885.028000] Inbound IN=ath0 OUT= MAC=00:11:6b:60:27:11:00:11:6b:21:b8:66:08:00 SRC=195.177.246.68 DST=192.168.123.106 LEN=1420 TOS=0x00 PREC=0x00 TTL=56 ID=13874 DF PROTO=TCP SPT=80 DPT=54065 WINDOW=24840 RES=0x00 ACK URGP=0
Jul  3 18:08:57 localhost kernel: [17194904.380000] Inbound IN=ath0 OUT= MAC=00:11:6b:60:27:11:00:11:6b:21:b8:66:08:00 SRC=195.177.246.68 DST=192.168.123.106 LEN=1420 TOS=0x00 PREC=0x00 TTL=56 ID=56483 DF PROTO=TCP SPT=80 DPT=54065 WINDOW=24840 RES=0x00 ACK URGP=0
Jul  3 20:22:48 localhost syslogd 1.4.1#17ubuntu7: restart.

```
I have no clue on how to solve all this but my system is getting more unstable by the day it seems..
(and I ran memtest and it finished without any error..)

---

### Post by Zyphrexi on 2006-07-03
I'm feeling ya, i've had a few apps crash, no hard reboot though. I'm thinking of switching to debian. There are only a few apps I can't live without, and now they don't work...

---

### Post by atoponce on 2006-07-03
[quote=Ramses de Norre]Man what is going on with ubuntu?? Dapper crashes more and more.. firefox crashes a few times a day, I had two system hang ups (needed hard reboot) and one kernel panic today, a couple of days ago suddenly I couldn't open any program, all gave 'segmentation fault' untill I rebooted and a lot of things were set back to default settings..

I have no clue on how to solve all this but my system is getting more unstable by the day it seems..
(and I ran memtest and it finished without any error..)[/quote] It seems to be quite the opposite for me.  When I was running Dapper testing, it would crash regularly, almost always directly related to Firefox accessing Java or Flash.  I went back to Breezy, and waited about a week after initial release before upgrading again.  I haven't had a crash yet, and I love it!

---

### Post by Rui Pais on 2006-07-03
[QUOTE=Ramses de Norre]Man what is going on with ubuntu?? Dapper crashes more and more.. firefox crashes a few times a day, I had two system hang ups (needed hard reboot) and one kernel panic today, a couple of days ago suddenly I couldn't open any program, all gave 'segmentation fault' untill I rebooted and a lot of things were set back to default settings.. [/QUOTE]

Hi, those things seems all related with the kernel (and bad looking, btw).
Have these starts after un upgrade of kernel? (last default seems to be a little naughty) 

Maybe try to use an old version, one that you know it worked in the past, and see if problems persist...

i'm assuming you use ubuntu defaults kernel, since you not mention others. Maybe manually compile other version, 2.6.15 starts to look a little old. And maybe you hit some hardware issue that as been solved on later sources...

---

### Post by JamesB on 2006-07-03
[QUOTE=Ramses de Norre]Man what is going on with ubuntu?? Dapper crashes more and more.. firefox crashes a few times a day, I had two system hang ups (needed hard reboot) and one kernel panic today, a couple of days ago suddenly I couldn't open any program, all gave 'segmentation fault' untill I rebooted and a lot of things were set back to default settings.. I don't know where to start looking for the problem (/var/log/messages nor /var/log/Xorg.0.log[.old] showed me useful info) 
I have no clue on how to solve all this but my system is getting more unstable by the day it seems..
(and I ran memtest and it finished without any error..)[/QUOTE]

I've run dapper flight 4 with all updates and haven't had one crash yet. I had a few problems with the '25 kernal so went back to the '23 and have had no problems. Maybe a fresh install would help??

---

### Post by nix4me on 2006-07-03
Ive not had any major crashes at all on 2 ubuntu machines.  The only problem is firefox.  It is crap as usual.  It disappears about once or twice a week while browsing.

nix4me

---

### Post by Ramses de Norre on 2006-07-04
Firefox does this like once or twice a day here.. and I'll try the 2.6.23 kernel. I don't understand how the kernel can be so unstable..

Ow and now I recall: I can't boot the 2.6.23-k7 kernel, it stopped working one day and no one knew a reason/solution..
I'm getting pretty disappointed in all this..

---

### Post by mlind on 2006-07-04
[QUOTE=Ramses de Norre]Firefox does this like once or twice a day here.. and I'll try the 2.6.23 kernel. I don't understand how the kernel can be so unstable..

Ow and now I recall: I can't boot the 2.6.23-k7 kernel, it stopped working one day and no one knew a reason/solution..
I'm getting pretty disappointed in all this..[/QUOTE]

I think you should either try older kernel, or make one yourself using newest stable upstream kernel,
but with Ubuntu defaults. It's worth a try! (make oldconfig will apply settings from previous .config file)

---

