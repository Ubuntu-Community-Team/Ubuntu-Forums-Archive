---
title: "trouble understanding journalctl boot selection"
date: 2023-09-01
forum: General Help
---

### Post by clepsdyrae on 2023-09-01
I'm trying to grasp the basics of journalctl...

I have SystemMaxUse=200M in /etc/systemd/journald.conf and it seems to be working fine.

If I do:

```
# journalctl --list-boots
```

I see:

```
# journalctl --list-boots
IDX BOOT ID                          FIRST ENTRY                 LAST ENTRY
 -4 1d9c21ed87a54cec81116a3b4c91d72c Wed 2023-08-23 11:42:35 PDT Wed 2023-08-23 12:10:30 PDT
 -3 35dc89cc179f425289dccb2049668fe3 Wed 2023-08-23 13:15:02 PDT Wed 2023-08-23 16:53:28 PDT
 -2 811261b05fc54099847fcc35378eda89 Thu 2023-08-24 00:23:39 PDT Wed 2023-08-23 17:33:38 PDT
 -1 446b22a0dc9a456aa4ddbaf1f4ef03c3 Wed 2023-08-23 17:34:38 PDT Wed 2023-08-23 19:52:24 PDT
  0 820d582bec84443f9b7f0fa7993ff571 Wed 2023-08-23 20:07:30 PDT Wed 2023-08-23 21:52:14 PDT
```

...these are all like a week old, despite me having used the computer every day. Where are the more recent boots?

Also, boot index -2 starts at Aug 24 12:23 AM and ends on Aug 23rd at 5:33 pm, the day before? Can that happen if the system clock is getting yanked around while logging? (I dual boot and sometimes Windows messes things up...)

Furthermore:

```
# cat /proc/sys/kernel/random/boot_id
1be56922-cd0b-45ea-b9bc-ed1790eb712d
```

...the current boot ID is not shown in the list at --list-boots, which confuses me.

Futhermore:

```
# journalctl -xb 0 | head -n 1 

```
...shows Sep 01 16:34:34 as the first line timestamp (which seems accurate if interpreted as UTC; maybe the system doesn't adjust for local time until later).

```
# journalctl -xb -1 | head -n 1 

```
...shows Sep 01 16:00:52, which might be accurate (I might have booted and then rebooted for some reason, don't recall.)

However:

```
# journalctl -xb -2 | head -n 1 

```
...again shows Sep 01 16:34:34. "-xb -3" again shows Sep 01 16:00:52, and on and on. It's as if it is doing a modulo N where N is the # of boots, which seems bizarre. E.g. "-xb -7000" shows Sep 01 16:34:34.

And again, none of these Sep 01 boots, or any of the boots since the 23rd, show up in --list-boots.

```
# journalctl --verify

```
...shows everything passing. What am I missing?

(Note: I recently moved my / and /home to new partitions, which involved cloning them and so forth, but everything went fine, and at any rate I've been running normally for 5 or 6 days at this point.)

Thanks for any insight!

---

### Post by TheFu on 2023-09-01
Do you use hibernation or standby? Could that explain no reboots seen?

When I look at my old boots, it all seems reasonable.  I tend to reboot only when there's a new kernel/libc ... there's a file in /var/run/reboot-needed that should recommend when a reboot is needed.  Otherwise, I don't reboot or power off my systems ... at least not except a laptop.

---

### Post by clepsdyrae on 2023-09-01
Thanks -- I only ever reboot; no hibernation or sleep of any kind. And I shutdown at least once a day...

---

### Post by clepsdyrae on 2023-09-15
This problem persists... now the journalctl --list-boots again shows old boots from about a week ago:

```
$ journalctl --list-boots
IDX BOOT ID                          FIRST ENTRY                 LAST ENTRY
 -7 a93874554d4b4d84bff17896d82d92dc Sun 2023-09-03 12:41:07 PDT Sun 2023-09-03 12:44:58 PDT
 -6 7e1d1943870843c683c0f857cf6dfad3 Sun 2023-09-03 13:16:48 PDT Sun 2023-09-03 13:20:56 PDT
 -5 6c542d02b15249afa2924b7f4639e7bc Sun 2023-09-03 14:35:28 PDT Sun 2023-09-03 14:36:59 PDT
 -4 6227350d0278426e8b094c8ac0b7c6e7 Sun 2023-09-03 14:42:22 PDT Sun 2023-09-03 21:47:05 PDT
 -3 3ea9eecb52da45208b8eb9871de45033 Mon 2023-09-04 15:42:18 PDT Mon 2023-09-04 15:06:22 PDT
 -2 7749694b83884c80b0a4794fc079fd28 Tue 2023-09-05 00:20:34 PDT Mon 2023-09-04 22:15:46 PDT
 -1 9dc6943717774807b1611cc4c40516e3 Tue 2023-09-05 08:00:55 PDT Tue 2023-09-05 11:42:09 PDT
  0 7a9887ab6ecd47b7854154ff8ad37c23 Tue 2023-09-05 11:43:03 PDT Tue 2023-09-05 11:46:09 PDT
```

...so it seems like these are getting updated but at a long delay... implying to me that the boots between Sep 3 and today are somewhere, just not showing up in the list.

And as before the current boot ID is not listed there.

And if I run "journalctl -xb -1 | head -n 1" I get the real previous boot. I get up to -xb -5 and it shows real boots. At -6 it modulo's around back to the equivalent of -1.

Using positive values for -b "journalctl -xb 1 | head -n 1" I get the boots shown by --list-boots up through -b 6. At -b 7 the first line does not match the datestamp in any of --list-boots (though it is from Sep 5).

I can't understand wtf is going on here... maybe there is a bug in how it rotates old journal entries or something.

I've just run:
```
sudo journalctl --rotate
sudo journalctl --vacuum-time=1s
```
...and will report on whether that helps.

---

### Post by clepsdyrae on 2023-09-25
Well, doing the rotate/vacuum seems to have cured whatever the bug was. Now the list of boots is sane, and includes the current boot.

---

