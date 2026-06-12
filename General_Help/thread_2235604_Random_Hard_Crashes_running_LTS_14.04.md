---
title: "Random Hard Crashes running LTS 14.04"
date: 2014-07-22
forum: General Help
---

### Post by brickbat on 2014-07-22
Hi,

I would like some help to hopefully diagnose and fix some hard crashes I am getting.  They seem to happen any time - sometimes 2 or 3 hours after boot and sometimes 3 or 4 days.  When the system crashes, even reset doesnt work.  I have to hold the power button down to shut down the system and then press it again to turn it on.  My hardware is ;

Intel 4771 processor
Gigabtye Z87X-UD5H motherboard
Corsair 16GB ram

Here are the last few lines of the systemlog before the crash.  I have no idea what that cron job is.  I assume it is doing some sort of housecleaning.


```

Jul 22 02:10:43 lserver2 kernel: [49967.605771] Peer 109.190.114.220:51413/45987 unexpectedly shrunk window 664127045:664128493 (repaired)
Jul 22 02:10:44 lserver2 kernel: [49968.575198] Peer 109.190.114.220:51413/45987 unexpectedly shrunk window 664127045:664128493 (repaired)
Jul 22 02:11:40 lserver2 kernel: [50024.861454] Peer 109.190.114.220:51413/45987 unexpectedly shrunk window 664248123:664249571 (repaired)
Jul 22 02:11:41 lserver2 kernel: [50026.043184] Peer 109.190.114.220:51413/45987 unexpectedly shrunk window 664248123:664249571 (repaired)
Jul 22 02:17:01 lserver2 CRON[7873]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 22 02:39:01 lserver2 CRON[8735]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))

```


And here are the last few lines of the kernel log before it crashes.  I have no idea what this is.

```

Jul 22 01:26:37 lserver2 kernel: [47317.232212] Peer 109.190.114.220:51413/34786 unexpectedly shrunk window 2069373254:2069380494 (repaired)
Jul 22 01:30:02 lserver2 kernel: [47523.321408] Peer 109.190.114.220:51413/34786 unexpectedly shrunk window 2069640484:2069643380 (repaired)
Jul 22 01:30:03 lserver2 kernel: [47524.058501] Peer 109.190.114.220:51413/34786 unexpectedly shrunk window 2069640484:2069643380 (repaired)
Jul 22 02:10:43 lserver2 kernel: [49967.605771] Peer 109.190.114.220:51413/45987 unexpectedly shrunk window 664127045:664128493 (repaired)
Jul 22 02:10:44 lserver2 kernel: [49968.575198] Peer 109.190.114.220:51413/45987 unexpectedly shrunk window 664127045:664128493 (repaired)
Jul 22 02:11:40 lserver2 kernel: [50024.861454] Peer 109.190.114.220:51413/45987 unexpectedly shrunk window 664248123:664249571 (repaired)
Jul 22 02:11:41 lserver2 kernel: [50026.043184] Peer 109.190.114.220:51413/45987 unexpectedly shrunk window 664248123:664249571 (repaired)

```

That IP adress means nothing to me.  It is not mine.  In any case, I don;t think it's crashing from this.

---

### Post by Jonor on 2014-07-22
I have the same CPU and mobo.
There were crashes while overclocking the CPU but it never happened at standard 3.5GHZ 
although i also made adjustments in the BIOS at the same time so the cure could have been there.
It would be helpful to know what changes if any, were made to the BIOS, including effects on the CPU and RAM.
The logs i would have to google which presumably you have already done.

---

### Post by brickbat on 2014-07-22
You can't overclock this processor.

I have googled them.  Thats why I said I didn't think they were the culprit.  I've made very few changes to the BIOS.  The main change was enabling hotswapping on all disks and changing memory to profile 1 so that it picks up the correct speed.

---

### Post by Jonor on 2014-07-22
Here is the essence of my BIOS tinkering should you be interested.
Notes were not made at the time this was done so some of these may be the default anyway 
and i dare say there will be a few harmless mistakes here too.
Thanks for the hotplugging tip which i have incorporated in the hope of helping to fix some auto-mount problems here ;)

M.I.T. BIOS version F5
M.I.T. > Current status > Extreme memory profile > Profile 1
M.I.T. > Advanced memory settings > CPU base clock > manual
  "                          "                       > Performance enhance > normal
  "                          "                       > DRAM timing selectable > auto
  "      > Advanced frequency settings > Advanced CPU core features > Intel turbo boost technology > disabled
  "      > Advanced voltage settings > 3D power control > set to normal where possible
  "      >                  "                     > CPU core voltage control > set to normal where possible
BIOS features > Fast boot > disabled
        "            > Limit CPUID maximum > disabled
        "            > Execute disable bit > disabled
        "            > Intel virtualization technology > disabled
        "            > Intel txt support > disabled
        "            > Dynamic storage accelerator > disabled
        "            > vt-d > disabled
Peripherals > via 1394 controller > disabled
       "         > PCH LAN controller > enabled
       "         > XHCI mode > enabled
       "         > Intel rapid start tech > disabled
       "         > Legacy USB support > enabled
       "         > XHCI hand-off > enabled
       "         > EHCI hand-off > enabled
       "         > On-board LAN controller #1 > enabled
       "         > Sata mode selection > have all with hotplug enabled

---

