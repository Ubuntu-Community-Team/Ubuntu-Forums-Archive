---
title: "Printing jobs reports: Stopped &quot;Filter Failed&quot;"
date: 2018-07-02
forum: General Help
---

### Post by jerome1232 on 2018-07-02
I have two desktops both running 18.04

Mine and Wifes.

Mine has a Brother HL-2140 connected via usb.

Wifes prints to this printer via cups.

She was printing fine last night. Today every print job from her computer results with the printer turning on for a second then just not printing. Poking around I was able to see that from the cups web admin page the job show a status of > stopped 
"Filter failed"

Click the teeny tiny image below to see a blown up version of what cups shows.
[ATTACH=CONFIG]280269[/ATTACH]

Print jobs coming from my computer print fine.

What gives?

---

### Post by jerome1232 on 2018-08-05
For reference, I figured out the issue :p

I have a brother 2140. For some reason Ubuntu by default chooses a driver that doesn't work correctly, it prints endless blank pages. So I have to download a .deb from brother, which installs the correct driver for cups. Then after the printer has already been installed I have to go into printer settings and select "brother hl-2140 for cups" instead of "brother hl-2140 foomatic".

Somehow, my wife had added the printer twice, once when the driver for cups was selected and once while the non-working foomatic driver was selected and she had the foomatic version selected as her default. I guess cups was rejecting her print jobs because I had already deleted that version.

Problem solved, them user issues will get you everytime.

---

### Post by emnipetro on 2018-08-07
I brought the Epson printer when I trying to print the page its show an error that [printer in an error state]("https://www.printererrorrepair.com/blog/how-to-fix-epson-printer-in-error-state-issue/"). to resolve the issue I uninstall or reinstall the software. Then also it shows an error. tell me what I do to solve the issue related to it.

---

