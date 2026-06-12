---
title: "Date and Time from 'dmesg'"
date: 2007-06-25
forum: General Help
---

### Post by nixgeek on 2007-06-25
Hi all,

Is there a way to change the Date and Time displayed when running the command 'dmesg'?

[413740.748385] sd 1:0:0:0: SCSI error: return code = 0x00040000
[413740.748392] end_request: I/O error, dev sdb, sector 586099263
[413740.748441] md: super_written gets error=-5, uptodate=0
[413740.748446] raid5: Disk failure on sdb1, disabling device. Operation continuing on 4 devices
[413740.786727] RAID5 conf printout:

This above example is rather cryptic. Why is does 'Ubuntu' {or Debian} display the date and time
this way? I guess it is in Julian date format.

Any info would be great.

Thanks,

Tim

---

### Post by bprsofteng on 2008-03-11
Can anyone at least tell me what the format represents? It's not epoch, is it seconds since boot, and what does the decimal point mean, nanoseconds?

---

### Post by bprsofteng on 2008-03-13
It's not Julian, my current numbers are reading as: 14488110.525996
which can't be Julian. I'm guessing that it is seconds since boot, but I can't find anything to support that.

---

### Post by jonrkc on 2008-03-26
I wish somebody would describe a way to make dmesg read in human-understandable time format.  Other distros I've run show the time and date, but not Ubuntu.  I posted about this over a year ago and never got a response.

When I (attempt to) troubleshoot using dmesg, I need to know the time that events occurred so I can correlate the information there with the mishap that I'm trying to figure out.

---

### Post by Azariatech on 2008-05-06
Hey all,

I'm basically a newbie to Ubuntu (and linux in general) coming from a fairly strong windows background.  This dmesg timestamp thing drove me nuts for a while.  

I had to do quite a bit of digging and eventually found that it's a format related to something called PrintK (which seems to be some kind of timer output function and was added to the Linux kernal around 2.6.12 or .14 iirc)  The format is basically timer Ticks of some sort (which I think is in the micro or nanosecond resolution, again, iirc.  Sorry I can't find the links to what I read.  it was a more than a few weeks ago).

The numbers represent Ticks since the kernel's Init or the start of some function shortly thereafter.

I also found that there is a similar list of messages (not sure if it's *100%* identical but in my limited experiences so far, it appears so) in /var/log/kern.log but with normal time and date stamps instead of Ticks.  
I just 'less' or 'tail' it and that works for me.  Don't know if there's a specific util (like dmesg) to read it but I guess it doesn't matter.

HTH somebody!

J.

---

### Post by dmizer on 2008-06-04
know this is old but i was looking for this answer and landed here too.

actual human readable dates for dmesg can be found in /var/log/kern.log

---

