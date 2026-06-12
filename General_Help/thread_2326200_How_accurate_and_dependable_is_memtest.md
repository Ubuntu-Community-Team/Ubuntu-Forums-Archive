---
title: "How accurate and dependable is memtest?"
date: 2016-05-29
forum: General Help
---

### Post by xeddog on 2016-05-29
I have a computer that has been having issues for a while.  At some point during the day, something will happen.  It might not even get fully booted up before something breaks, or it might go for several hours, but something will happen.  It might be php5 programs crashing (sometimes they restart and sometimes they do not),  Firefox or Chromium crashing and not restartable, kernel panic, filesystem corruption (only once and I *might* have a possible explanation for this one), unable to do system updates, or any of a number of other things that have happened.  

I finally got around to checking the SMART data for the disk drive and saw a buttload of read errors, so I replaced the disk and did a clean install of Ubuntu 15.10.  Unfortunately that did no good what-so-ever.  I have run memtest a couple of times with no errors, but I only let it go for a  pass or two.  Yesterday I started memtest again and let it go overnight.  When I checked this morning there was one error that occurred on pass #4, test #7, CPU 0.  It is now running pass #7. but only the one error has been reported.  This has me wondering if I really need the $700 worth of new cpu/motherboard/memory I just purchased and have not received yet. 

So my question is, just how reliable is memtest?  Is it reasonably possible this could be a false error?  Or more likely, is it reasonably possible that it could still be a problem with the motherboard or cpu?  After all, the memory data still has to pass through some portion of the motherboard and then be diagnosed by the cpu.

Any thoughts or opinions appreciated.

Thanks,

Wayne

---

