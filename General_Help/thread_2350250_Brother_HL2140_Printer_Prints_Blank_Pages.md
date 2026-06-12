---
title: "Brother HL2140 Printer Prints Blank Pages"
date: 2017-01-22
forum: General Help
---

### Post by tpelle2 on 2017-01-22
OK, I'm back with my next problem. My home network has a Brother HL2140 on the network.  My new installation of Ubuntu 16.04.1 detects the printer, and if I send a test page to it from the Printers part of the Settings page, the printer wakes up and feeds the page, but the page comes out blank.  The Windows machines can print to the printer just fine.

Just now I got the bright idea to type a printer test page in AbiWord, and sent it to the printer, but it also produced blank pages, and the printer just kept feeding paper until I finally just shut it off!

The printer is hooked to a WiFi network print adapter, by the way.

You guys did so well on my Ubuntu Software utility issue, that I have great confidence in you.  Can anyone shed any light on this issue?

---

### Post by tpelle2 on 2017-01-29
Got it working.  First, since we have a newer network printer that my wife uses (rendering this Brother HL-2140 as surplus to her needs), I moved the printer down next to my Linux Desktop and connected it locally via a USB cable.  Then I just kept hammering at it, using all sorts of "solutions" that I found on various discussion groups.  Finally I simply changed, In System Settings/Printer Properties, the Make and Model of the printer to Brother HL2140 for CUPS.  Simple as that - but it did the trick!

---

### Post by x-ge-u on 2017-11-02
Thanks for providing this information - it covers exactly my situation, and the solution you suggest works like a charm, also for me!  It saves me a lot of hassle.  Thank you!

---

