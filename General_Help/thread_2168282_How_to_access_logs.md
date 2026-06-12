---
title: "How to access logs"
date: 2013-08-17
forum: General Help
---

### Post by DeanoCYM on 2013-08-17
Hi,

I'm having some pretty bad full system freezes, I think its my hard drives. Where can I find the logs that will confirm/disprove this? SMART is all good but I think something's going on as this happens on two different motherboards with the same HDDs.

Thanks,

Rhys

---

### Post by VMC on 2013-08-17
The system logs can be found here:
```
/var/log
```

I would start with *syslog* and/or *kern.log*

What you can do is open up a terminal and "tail" one of them, like so:
```
tail -f /var/log/syslog
```

---

### Post by zeljkojagust on 2013-08-17
If you suspect your hard drives are bad, you can test them with smartctl. First you need to install smartmontools and lsscsi packages:

sudo apt-get -y -R install smartmontools lsscsi

Now first execute lsscsi (you just enter lsscsi on command prompt), which will list your hard drives. You will get something like this as output:

[0:0:0:0]    disk    ATA      WDC WD2500AAJS-5 01.0  /dev/sda
[1:0:0:0]    disk    ATA      WDC WD2500AAJS-5 01.0  /dev/sdb

What you're interested in is /dev/sda /dev/sdb and similar. When you get that, execute the following on the command prompt:

sudo smartctl -a /dev/sda

This will give you a "health" report for your /dev/sda disk. What you're interested in are values for **Reallocated_Sector_Ct** and **ATA Error Count**. If any of those values are higher than 0, you have a serious disk problems and prooly your disks need to be changed.

---

### Post by DeanoCYM on 2013-08-18
Just what I was looking for, thanks both.

There are no bad SMART attributes that I can see so I will have to wait for another crash and check the logs.

---

### Post by DeanoCYM on 2013-08-18
Hi, just before the freeze my system started acting up (chromium-browser closed and would not re-open and compiz flickered) I grabbed this just before the freeze:

```

Aug 18 14:37:25 rhys-tv kernel: [ 3633.792053] ata1.00: status: { DRDY }
Aug 18 14:37:25 rhys-tv kernel: [ 3633.792057] ata1: hard resetting link
Aug 18 14:37:30 rhys-tv kernel: [ 3639.152020] ata1: link is slow to respond, please be patient (ready=0)
Aug 18 14:37:35 rhys-tv kernel: [ 3643.800015] ata1: COMRESET failed (errno=-16)
Aug 18 14:37:35 rhys-tv kernel: [ 3643.800023] ata1: hard resetting link
Aug 18 14:37:40 rhys-tv kernel: [ 3649.160018] ata1: link is slow to respond, please be patient (ready=0)
Aug 18 14:37:45 rhys-tv kernel: [ 3653.808017] ata1: COMRESET failed (errno=-16)
Aug 18 14:37:45 rhys-tv kernel: [ 3653.808025] ata1: hard resetting link
Aug 18 14:37:50 rhys-tv kernel: [ 3659.168019] ata1: link is slow to respond, please be patient (ready=0)
Aug 18 14:38:20 rhys-tv kernel: [ 3688.848015] ata1: COMRESET failed (errno=-16)

```
Shortly after this the whole GUI freezes and all I can do is drop into a tty.

I enter my username, hit enter and before I can enter my password I get the following message:
```

end_request: I/O error, dev/sda, sector 21662800

```

Any Ideas?

---

### Post by VMC on 2013-08-18
Looks like hard drive problems. It could be just a matter of a lose cable somewhere. Try re-inserting both ends - if your comfortable doing so.

Since its reporting a sector error, it may very well be your drive is dying. Did you try the [COLOR=#000000]*smartctl* command?[/COLOR]

---

### Post by DeanoCYM on 2013-08-18
I have tried two new SATA cables and I'm having the same problem still.
The SMART attributes are all OK as far as I can tell. Here they are for /dev/sda
```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   050    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   100   100   001    Old_age   Always       -       5333
 12 Power_Cycle_Count       0x0032   100   100   001    Old_age   Always       -       561
170 Grown_Failing_Block_Ct  0x0033   100   100   010    Pre-fail  Always       -       0
171 Program_Fail_Count      0x0032   100   100   001    Old_age   Always       -       0
172 Erase_Fail_Count        0x0032   100   100   001    Old_age   Always       -       0
173 Wear_Levelling_Count    0x0033   100   100   010    Pre-fail  Always       -       3
174 Unexpect_Power_Loss_Ct  0x0032   100   100   001    Old_age   Always       -       0
181 Non4k_Aligned_Access    0x0022   100   100   001    Old_age   Always       -       5 0 5
183 SATA_Iface_Downshift    0x0032   100   100   001    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   050    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   001    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   001    Old_age   Always       -       0
189 Factory_Bad_Block_Ct    0x000e   100   100   001    Old_age   Always       -       49
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       0
195 Hardware_ECC_Recovered  0x003a   100   100   001    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   100   100   001    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   001    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   001    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   100   100   001    Old_age   Always       -       0
202 Perc_Rated_Life_Used    0x0018   100   100   001    Old_age   Offline      -       0
206 Write_Error_Rate        0x000e   100   100   001    Old_age   Always       -       0

```

That looks OK to me what do you think?

---

### Post by VMC on 2013-08-18
Then let's go back to that *syslog*. After freeze, and a re-boot you can find *syslog*(current), and *syslog.1*(previous). Look in there for any indications of trouble.

---

### Post by DeanoCYM on 2013-08-18
Ive had a look through the logs and the only other incriminating part I can find is this:
```

Aug 18 18:12:49 rhys-tv kernel: [ 3631.808031] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Aug 18 18:12:49 rhys-tv kernel: [ 3631.808039] ata1.00: failed command: IDENTIFY DEVICE
Aug 18 18:12:49 rhys-tv kernel: [ 3631.808045] ata1.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
Aug 18 18:12:49 rhys-tv kernel: [ 3631.808045]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Aug 18 18:12:49 rhys-tv kernel: [ 3631.808048] ata1.00: status: { DRDY }
Aug 18 18:12:49 rhys-tv kernel: [ 3631.808053] ata1: hard resetting link 
```
Looks like HDD again?

---

### Post by DeanoCYM on 2013-08-18
Also, I just realised that I cannot restart I get this error:
```

Aug 18 20:31:13 rhys-tv gnome-session[1496]: WARNING: Unable to restart system: Not Authorized
Aug 18 20:31:13 rhys-tv gnome-session[1496]: CRITICAL: gsm_manager_set_phase: assertion `GSM_IS_MANAGER (manager)' failed
Aug 18 20:31:13 rhys-tv gnome-session[1496]: Gtk-CRITICAL: gtk_main_quit: assertion `main_loops != NULL' failed
Aug 18 20:31:13 rhys-tv acpid: client 1037[0:0] has disconnected
Aug 18 20:31:13 rhys-tv acpid: client 1037[0:0] has disconnected
```

---

### Post by VMC on 2013-08-18
That report "[COLOR=#000000][FONT=Ubuntu Mono]ata1.00: status: { DRDY }" is an ominous message. Everywhere I have seen that it is either a hardware, hard drive issue.[/FONT][/COLOR]

---

### Post by DeanoCYM on 2013-09-15
Just for anyone who was having this problem: I solved this by backing up then zeroing the entire hard drive using dd from a live CD. Just reinstalling ubuntu didn't work but zeroing the entire disk and reinstalling seems to have sorted it out.

Thanks to everyone for their help.

---

