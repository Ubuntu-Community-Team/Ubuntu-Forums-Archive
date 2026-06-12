---
title: "&quot;The system is running in low graphics mode&quot;"
date: 2013-04-03
forum: General Help
---

### Post by chk1827 on 2013-04-03
I am using Ubuntu 12.04(fresh install), installed on an external HDD.

I accidently brushed against my external HDD while using it; its connection is very sensitive so it got disconnected while logged on in ubuntu and i had to force shut the system.

When i restarted the "Your drives need to be checked for errors" came up and checked the whole disk and said errors were found with your / drive, press F to fix them or M for manual recovery..i pressed F it did something and then restarted.

After that i got the "The system is running in low graphics mode" 'Your screen,graphics card and input device settings could not be detected correctly.You will have to configure these yourself.'

Tired configuring the graphics,but both the 'use generic configuration' and 'use backed up' configuration did'nt work..

Tried 'troubleshoot the error', can 'review xserver log' file but cant review 'startup errors' or 'edit configuration file'

Tried 'run in low graphics mode for just one session' it shows 'Please wait a minute for the display to restart' i press Ok...then it takes upto a black screen with a no of messages. the last of which is 'Stopping System V runlevel compatibility'
..its struck on this screen for a very long time with intermediate messages of 'device sdb6 asking for cache data failed,assuming write through'(the messages sometimes appear in terminal also so its normal for my system)...so i press the power off button and it stops all processes and shuts down...tried this many times but same result.

Then i tried booting into recovery mode,
and tried 'Fix broken packages' it installed some small size packages,..but it made no difference.
Then i tried 'FailsafeX' mode in the recovery options, it showed 'Root contains a file system with errors,check forced' boot and home are clean...then it checks the drive and window with "The system is running in low graphics mode"..on trying 'run in low graphics for just one session', it takes me back to the recovery menu..for the other options its same as whats described before.

This same problem happened before also, but then i had reinstalled, but now i don't want to...how to fix it?

my VGA controller is(lspci | grep VGA)
VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

 and i am using acer aspire 6930 laptop.

---

