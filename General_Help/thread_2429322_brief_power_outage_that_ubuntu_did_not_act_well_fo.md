---
title: "brief power outage that ubuntu did not act well for (it stayed up)"
date: 2019-10-16
forum: General Help
---

### Post by Skaperen on 2019-10-16
i had a brief power outage this morning.  it was only about 2-3 seconds.  it was not long enough for the generator to even start its engine.  my laptop kept running on battery until the power was back on.  but i was not using it at the time so the keyboard and mouse were idle.  10 minutes later the screen blanks out.  usually i leave it running, when i sleep, as a big digital clock display so i can see the time without my glasses.  so i got up and checked it out.  it did say it was on plugged in power so i let it go. another 10 minutes and it blanked out, again.  this is what it is set to do if it is on battery, in power manager settings. it's behaving as if on battery even though it is plugged in and says that it is plugged in.  rebooting fixed it.  apparently, some part of the code doesn't go back to plugged in mode after going to battery mode and back.  does anyone (particularly xubuntu users) know about this, or what could be causing it, or if there are real bug reports on this?  it is fully up to date as of yesterday.

---

### Post by Autodave on 2019-10-16
I have an HP here that does the same thing.  The Dell and the Sony do not do that.

Don't know if matters or not, but the HP has a replacement battery from China.  The other 2 have OE batteries.

---

### Post by Skaperen on 2019-10-16
since checking the power state tells me it is running on plugged in power, then i believe the hardware notified the software of this condition.  apparently something didn't record the state correctly.  it did record the state of being on battery.  or maybe there was a failure of something to change the live settings of something else when the power state changes.  that's why i don't believe it is a hardware or battery issue.  this is a System76 Kudu Pro if that matters.  but your experience is certainly different.  OTOH, i could explain that away by suggesting the Dell and Sony have power supplies that can hold up the DC output for a longer period of time.

i recall being in a presentation, when i was in college around 1979, of some software someone was demonstrating on an Apple II computer that was dialed up to the school's IBM System 370/158 mainframe.  during the demonstration the power went out for 2 seconds and the windowless room was plunged into total darkness.  when the power came back on, so did the video monitor attached to the Apple II.  then it was obvious the Apple II stayed up during the 2 second outage.  but the dialup was now down.  the guy doing the demo dialed back, but the mainframe did not answer.  later, i found out the computer center power was only out for 2 seconds, too, but that was enough to take it down.  later i tested unplugging an Apple II and found it would quit outputting video after about 4 seconds.

maybe the HP power supply doesn't last as long or the HP computer is a bigger power load that drains the capacitors faster.  it could be more hard drives and/or attached cards.

---

