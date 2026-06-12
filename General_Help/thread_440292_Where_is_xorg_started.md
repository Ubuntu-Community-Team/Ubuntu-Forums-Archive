---
title: "Where is xorg started?"
date: 2007-05-11
forum: General Help
---

### Post by juvan on 2007-05-11
I have the commonly known problematic HW setup with Intel 915 Graphic chip and 1440x900 resolution monitor. I used to have Mandriva 2006 running with 915resolution patch set up as it is instructed in [http://mandrivaonadellx1.50webs.com/display.htm](http://mandrivaonadellx1.50webs.com/display.htm).

Yesterday I installed Ubuntu 7.04 and I have spent a few hours trying to get the new intel driver working in 1440x900 mode without any success. I decided to revert back to i810 driver and 915resolution trick, which does work OK if I run it from command line and restart the X server. The problem is that adding the 915resolution command to rc.local and renaming the symlink in rc5.d to S01rc.local does not seem to run early enough the script and as a result I Xorg does not see the 1440x900 mode when it is starting. 

By the time I have logged in the patch has run and I can see the patched resolution in Video bios. Restarting X-server with ctrl-alt-bkspace brings the much needed 1440x900 resolution into the display resolutino menu, and everything works from then on just fine.

The question is, where should I put the initial 915resolution patch to make it run early enough?

---

### Post by ajgreeny on 2007-05-11
I assume you have the **915resolution** package installed.  I know it is needed in dapper but not sure about feisty, though worth mentioning, just in case.

---

