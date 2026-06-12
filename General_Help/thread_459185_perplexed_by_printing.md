---
title: "perplexed by printing"
date: 2007-05-30
forum: General Help
---

### Post by the_real_bubba on 2007-05-30
I've got an HP 2200D attached by my freshly installed FFawn box by the parallel port.  The printer worked fine under Fedora.  Using the recommended Postscript printer CUPS sends the job successfully (so it thinks) and the printer's job light blinks for a few minutes, then goes out, nothing is printed.  It seems to me that some sort of "end of job" signal is not being sent.  I can't find any printer driver option that might help here.  When I try using the "hpijs - HPLIP 1.7.3" or the "hpijs" drivers I just get pages of ascii nonsense.  This must be something simple...

---

### Post by MoLE on 2007-06-07
Hi.  According to the [OpenPrinting database]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_2200"), you seem to be on the right track.  Was the printer powered up when you installed feisty?  If you have the liveCD, it might pay to boot that up and see if you can get the printer working in that environment (which is a known quantity).
Assuming you haven't made any changes to cups permissions or anything like that?

---

