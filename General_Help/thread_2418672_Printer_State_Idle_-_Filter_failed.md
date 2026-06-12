---
title: "Printer State Idle - Filter failed"
date: 2019-05-09
forum: General Help
---

### Post by lsutiger on 2019-05-09
We have a networked printer that two Ubuntu 16.04 computers fail to print to. I have a Win7 VM installed on one of the systems that is able to print to said printer. From the /var/log/cups/error_log:
```
D [09/May/2019:10:29:33 -0500] [Job 1020] GPL Ghostscript 9.26: Unrecoverable error, exit code 1
D [09/May/2019:10:29:33 -0500] [Job 1020] Process is dying with \"Unable to determine number of pages, page count: -1
D [09/May/2019:10:29:33 -0500] [Job 1020] \", exit stat 3
```
I attempted to remove and reinstall ghostscript from [this]("https://askubuntu.com/questions/1081885/printer-stopped-working-after-upgrade-16-04-to-18-04") link, which did not work. I have been searching a lot but there are no new posts that I can find to solve this issue.
Both systems had quite a few updates done yesterday from an apt-get update && apt-get upgrade and the issue started then.
Any suggestions?

Additional info:
Printer is a Brother HL-2270DW and this has been the printer for both the Ubuntu computers for many years.
More. From the /var/log/apt/history.log:```
Start-Date: 2019-05-09  06:12:42
Commandline: /usr/bin/unattended-upgrade
Upgrade: libgs9:amd64 (9.26~dfsg+0-0ubuntu0.16.04.8, 9.26~dfsg+0-0ubuntu0.16.04.9), ghostscript:amd64 (9.26~dfsg+0-0ubuntu0.16.04.8, 9.26~dfsg+0-0ubuntu0.16.04.9), ghostscript-x:amd64 (9.26~dfsg+0-0ubuntu0.16.04.8, 9.26~dfsg+0-0ubuntu0.16.04.9), libgs9-common:amd64 (9.26~dfsg+0-0ubuntu0.16.04.8, 9.26~dfsg+0-0ubuntu0.16.04.9)
End-Date: 2019-05-09  06:12:44

```
So the ghostscript package was updated yesterday.
I solved the issue. I deleted the printer in the System Settings-->Printers module. I then added the printer back, but instead of using the printer that Ubuntu found, I added it via the IP address.

---

### Post by Handssolow on 2019-05-09
Sadly I've got the same problem but as yet no solution. My Brother HL-8L Laser monochrome printer has been used OK for some years with Ubuntu (running 16.04 currently), then yesterday a ghostscript 9.26 update leads to just the same error messages you've reported above, Idle, Stopped Filter failed etc. I've been working on this for a few hours and thinking, surly I can't be the only one this has happened to. My printer's parallel cable is connected to my desktop's PCI parallel card and printer recognised as a Brother HL-820. I've tried different drivers but the standard Foomatic/hl7x0 is the recommended driver.

I am relieved that someone else has had this similar problem but none of the solutions I found through web searches have worked. On the top of the recent Firefox Add-on issue, I could do without another problem brought on by an update.

My printer isn't networked, so presumably it doesn't have an IP address. Ubuntu Settings and CUPS on the browser mostly finds my Brother HL-8L as an HL-820, trying different drivers mostly lead to the same error messages about page count -1 and filter failed etc.

What went wrong in ghostscript and how might this be corrected?

---

### Post by Handssolow on 2019-05-10
Another CUPS related update this morning and I was hopeful my printing would be sorted. But no, I am still getting "Stopped" and "Idle, Filter failed". 
Initially after the update there was no error message on a print job, but the red alarm light on my printer was lit. This had happened yesterday when I was trying different drivers. The red light doesn't come on if no printer was configured in Ubuntu. Phew, my printer is still probably OK.

The path for my Brother HL-8L printer is, parallel:/dev/lp0 and in the past it worked with Ubuntu, recognised it as an HL-820 and assigned the recommended driver, probably Foomatic/hl7x0. In Settings>Printers I see now that I can select HL-8, the recommended driver given for this is Foomatic/ljetplus.

Currently I am out of ideas. A removal and reinstall of CUPS, configuring my printer either as an HL-820 or HL-8 makes no difference. Using Ubuntu System Settings or CUPS via the browser to configure, makes no difference. A concern is that during the process of wanting a working printer back I have altered something.

---

### Post by Handssolow on 2019-05-11
My printer is working again. Yesterday's CUPS related update probably should here have corrected the "Stopped, Filter failed" message which arrived with the previous day's ghostscript update, by then I'd messing with my system.

Today I revisited a webpage on askubuntu.com [here](https://askubuntu.com/questions/1080720/printer-filter-failed). I had previously deleted iccprofiles and it's contents, at /usr/share/ghostscript/9.25/iccprofiles. I'd noticed that a reinstall of CUPS did not regenerate its contents however a reinstall of libgs9-common repopulated the iccprofiles directory, delivering a working printer again.

It's another SOLVED here.

PS. I have stuck with my HL-8L being recognised as a HL-820, with Foomatic/hl7x0 driver because I believe that's what I have been using before.

---

