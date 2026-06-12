---
title: "LibreOffice envelope printing error on Lexmark laser"
date: 2015-12-22
forum: General Help
---

### Post by efflandt on 2015-12-22
Apparently LibreOffice has had issues trying to print envelopes in the past judging from old posts, but has that ever been resolved (currently 4.2.8.2 in Ubuntu 14.04)? I figured out how to Insert > Envelope, configure it for #10 envelope, and save that to a new document. But no matter how I tried to print to a #10 envelope (which works in MS Word), nothing would print on the envelope and when I printed it to US Letter size paper it printed the following error (which I could not see on just an envelope in the center):```
ERROR
configurationerror
OFFENDING COMMAND:
setpagedevice
STACK:
--nostringval--
false
684
297
0
0
684
297
--nostringval--
5
```This happens for both a Lexmark X204n (all-in-one, incl network scanning w/sane) and C543dn (color duplex) network laser printers which both do postscript (or HP PCL). The X204n actually substituted for a broken HP network printer at our office (same 1200 dpi) just by using its IP address (no driver changes) until we got a new HP printer.

When I export the #10 envelope from LibreOffice as pdf, it properly prints landscape on US Letter paper, but gives the same error above if I set the printer driver to #10 envelope. So I had to set the envelope in LibreOffice to be landscape in the middle, then after creating a document from that which left a big top margin, I reformatted that page to letter size. When I print that and just leave the printer set for letter size landscape it prints fine on a #10 envelope inserted in the center of manual feed. It is upside down from MS Word envelope printing (not a big deal). So I saved that page as a LibreOffice template for single envelopes, but not sure how things would work out if I need to use mailmerge.

Any idea if the above error is related to LibreOffice or Lexmark's interpretation of postscript? Envelope printing works fine in Windows which likely uses HP PCL, in fact the Lexmark worked better for printing different size envelopes from stamps.com software than a real HP printer (which would shrink print on envelopes larger than #10 down to postcard size).

PS: I thought I had it at least printing formatted as letter size, but not quite. I had to format the page as 8.5" x 9.5" (length of envelope), move the boxes for return and to addresses up 0.5", and in Landscape told the driver that paper was "other envelope". Then I was able to print on a centered #10 envelope with its top to the right.

---

