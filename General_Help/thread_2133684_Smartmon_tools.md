---
title: "Smartmon tools"
date: 2013-04-08
forum: General Help
---

### Post by DevgruSeal on 2013-04-08
Hey all,
Smartmon is showing "197 Current_Pending_Sector 0x0032 184 172 0000 Old_age Always - 871" from what I gather this means there are bad blocks on the hard-drive and I should replace it, correct?

---

### Post by kclark on 2013-04-08
I never trust the "old age" or "pre-fail" flags.

What's the output of 

```

$ sudo smartctl -H /dev/sdX

```

---

### Post by DevgruSeal on 2013-04-08
> **kclark said:**
> I never trust the "old age" or "pre-fail" flags.

What's the output of 

```

$ sudo smartctl -H /dev/sdX

```

```
**smartctl -H /dev/sda**
smartctl 6.0 2012-10-10 r3643 [i686-linux-3.7.5-pmagic] (local build)
Copyright (C) 2002-12, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
```

However...

```
**smartctl -l selftest /dev/sda**
smartctl 6.0 2012-10-10 r3643 [i686-linux-3.7.5-pmagic] (local build)
Copyright (C) 2002-12, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%     15931         79907672
# 2  Short offline       Completed: read failure       90%     15930         79907672
# 3  Short offline       Completed: read failure       90%     15930         79907563
# 4  Short offline       Completed: read failure       10%     15930         79907672
# 5  Short offline       Completed: read failure       90%     15929         79907811
# 6  Short offline       Completed: read failure       90%     15929         79907672
# 7  Short offline       Completed: read failure       90%     15929         79907672
# 8  Short offline       Completed: read failure       90%     15929         79907563
# 9  Short offline       Completed: read failure       90%     15928         15785181
#10  Short offline       Completed: read failure       90%     15928         15787126

```

I am having to use a LiveCD at the moment to look at the hard-drive which contains my ubuntu installation, by the way.

---

