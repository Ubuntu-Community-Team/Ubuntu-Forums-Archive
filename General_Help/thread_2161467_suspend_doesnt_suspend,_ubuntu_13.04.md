---
title: "suspend doesnt suspend, ubuntu 13.04"
date: 2013-07-10
forum: General Help
---

### Post by pretty_whistle on 2013-07-10
The title says it.  The most that happens is the wireless connection will momentarily disconnect only to reconnect again seconds later.

??  Any help appreciated.

---

### Post by Toz on 2013-07-10
Can you provide some more information?

1. What is the make and model of your computer?
2. Can you post your /var/log/pm-suspend.log file like this:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.
3. Post back the results of:
```
cat /var/log/syslog | grep PM:
```

---

### Post by pretty_whistle on 2013-07-10
> **Toz said:**
> Can you provide some more information?

1. What is the make and model of your computer?
2. Can you post your /var/log/pm-suspend.log file like this:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.
3. Post back the results of:
```
cat /var/log/syslog | grep PM:
```

1. Its an HP 650.

2. I think I did this wrong, but pastebinit /var/log/pm-suspend.log gave me this:
```

The program 'pastebinit' can be found in the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selected package>



```

3. The result of cat /var/log/syslog | grep PM:

```

Jul 10 09:58:41 nutin kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jul 10 09:58:41 nutin kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jul 10 09:58:41 nutin kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jul 10 09:58:41 nutin kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jul 10 09:58:41 nutin kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Jul 10 09:58:41 nutin kernel: [    0.236198] PM: Registering ACPI NVS region [mem 0xaaebf000-0xaafbefff] (1048576 bytes)
Jul 10 09:58:41 nutin kernel: [    1.031987] PM: Hibernation image not present or could not be loaded.
Jul 10 16:57:37 nutin kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jul 10 16:57:37 nutin kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jul 10 16:57:37 nutin kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jul 10 16:57:37 nutin kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jul 10 16:57:37 nutin kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Jul 10 16:57:37 nutin kernel: [    0.131368] PM: Registering ACPI NVS region [mem 0xaaebf000-0xaafbefff] (1048576 bytes)
Jul 10 17:04:51 nutin kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jul 10 17:04:51 nutin kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jul 10 17:04:51 nutin kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jul 10 17:04:51 nutin kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jul 10 17:04:51 nutin kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Jul 10 17:04:51 nutin kernel: [    0.130863] PM: Registering ACPI NVS region [mem 0xaaebf000-0xaafbefff] (1048576 bytes)
Jul 10 17:17:39 nutin kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jul 10 17:17:39 nutin kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jul 10 17:17:39 nutin kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jul 10 17:17:39 nutin kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jul 10 17:17:39 nutin kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Jul 10 17:17:39 nutin kernel: [    0.132368] PM: Registering ACPI NVS region [mem 0xaaebf000-0xaafbefff] (1048576 bytes)



```

---

### Post by Toz on 2013-07-10
Nothing in syslog. You need to install the pastebinit program. Its small and posts contents of files up to paste.ubuntu.com so its easier to view those files. Interesting you don't have it installed - I thought it was installed by default.

---

### Post by pretty_whistle on 2013-07-10
> **Toz said:**
> Nothing in syslog. You need to install the pastebinit program. Its small and posts contents of files up to paste.ubuntu.com so its easier to view those files. Interesting you don't have it installed - I thought it was installed by default.
:)

Here you go:

[http://paste.ubuntu.com/5863467/](http://paste.ubuntu.com/5863467/)

---

### Post by Toz on 2013-07-10
> Running hook /etc/pm/sleep.d/20_ralink suspend suspend:
ra0: ERROR while getting interface flags: No such device
FATAL: Module rt3290sta not found.

/etc/pm/sleep.d/20_ralink suspend suspend: Returned exit code 1.
Wed Jul 10 17:10:43 MDT 2013: Inhibit found, will not perform suspend
Guess you must of put that file in for a reason, but the module no longer exists. Try deleting the file (/etc/pm/sleep.d/20_ralink).

---

### Post by pretty_whistle on 2013-07-10
> **Toz said:**
> Guess you must of put that file in for a reason, but the module no longer exists. Try deleting the file (/etc/pm/sleep.d/20_ralink).
I forgot how to delete that.  Using root somehow is all I can recall...

---

### Post by Toz on 2013-07-10
From a terminal:
```
sudo rm /etc/pm/sleep.d/20_ralink
```
(be extra careful executing sudo and rm in the same command).

---

### Post by pretty_whistle on 2013-07-10
It worked.  My suspend has been brought back to life.  :)

Thank you.

---

