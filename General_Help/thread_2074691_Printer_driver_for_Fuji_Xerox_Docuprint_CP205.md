---
title: "Printer driver for Fuji Xerox Docuprint CP205"
date: 2012-10-22
forum: General Help
---

### Post by Stolea on 2012-10-22
I have asked this question on the hardware forum but had no response. So now I try here.

I just installed 12.04 on my wife's computer. Everything works well, but I can't seem to be able to find a printer driver for her Fuji Xerox CP205 colour laser printer. I have been to their website, but they only list drivers for Windoze and Mac
Any ideas how to make the printer work?

---

### Post by Azdour on 2012-10-22
Hi,

I found this old thread, maybe it will be helpful?

[http://ubuntuforums.org/showthread.php?t=1144823](http://ubuntuforums.org/showthread.php?t=1144823)

---

### Post by bottomtop on 2013-02-22
Get the driver for the Phaser 6000 from here:

[http://www.support.xerox.com/support/phaser-6000/downloads/engb.html?operatingSystem=linux&fileLanguage=en_GB](http://www.support.xerox.com/support/phaser-6000/downloads/engb.html?operatingSystem=linux&fileLanguage=en_GB)

Ignore the message you get about a "Poor Quality Package"

When setting up in CUPS, choose the manufacturer Xerox and the driver described as "Xerox Phaser 6000B v1.0" or similar.

It seems to work ok for me.

---

### Post by heavenhell5 on 2013-02-26
[LEFT]Thanks bottomtop, it works for me too. Finally able to print directly from Ubuntu instead of using a windows virtual machine.
[/LEFT]

---

### Post by Anthony Fok on 2013-09-01
Hello,

You might also like to read this thread:
[LIST]
[*]Fuji Xerox DPCM205FW laser multifunction: [http://forums.whirlpool.net.au/archive/1792647](http://forums.whirlpool.net.au/archive/1792647)
[/LIST]
And search for either "CP205" or "foo2hbpl".  It turns out that, in Ubuntu 13.04, the **printer-driver-foo2zjs** package comes with **/usr/bin/foo2hbpl2** and has experimental support for CP205 (and presumably CP205w too).

See also the upload to Debian (hence Ubuntu) for CP205 support:
[LIST]
[*][http://lists.debian.org/debian-printing/2013/03/msg00030.html](http://lists.debian.org/debian-printing/2013/03/msg00030.html)
[/LIST]
Cheers,
Anthony

---

### Post by mike40033 on 2013-10-22
> **Anthony Fok said:**
> Hello,

You might also like to read this thread:
[LIST]
[*]Fuji Xerox DPCM205FW laser multifunction: [http://forums.whirlpool.net.au/archive/1792647](http://forums.whirlpool.net.au/archive/1792647) 
[/LIST]
And search for either "CP205" or "foo2hbpl".  It turns out that, in Ubuntu 13.04, the **printer-driver-foo2zjs** package comes with **/usr/bin/foo2hbpl2** and has experimental support for CP205 (and presumably CP205w too).

See also the upload to Debian (hence Ubuntu) for CP205 support:
[LIST]
[*][http://lists.debian.org/debian-printing/2013/03/msg00030.html](http://lists.debian.org/debian-printing/2013/03/msg00030.html) 
[/LIST]
Cheers,
Anthony

I have 13.04 and I've installed these packages, but how do I install my CP205w as a printer?

Ubuntu 13.04 auto-discovered the printer as a shared printer on my MacBook, so I can print from Ubuntu only if the MacBook is switched on.

The whirlpool forum link hinted that 13.10RC will auto-discover the printer, if I assign it a static IP address. Should I just do that, then wait for 13.10 to be released?

Thanks!

---

