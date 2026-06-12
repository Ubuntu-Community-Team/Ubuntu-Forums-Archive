---
title: "JBD2 IO and SSD"
date: 2014-08-30
forum: General Help
---

### Post by wewantutopia on 2014-08-30
Hello everyone.  I have an odd issue that just started occurring.  There were no updates or system changes that occurred prior to this starting.  It DID start after an improper shutdown (had to hold the power button) The main reason I'm concerned is I recently upgraded to an SSD and I am concerned about premature failure.

Just yesterday my system multiload indicator has started showing I/O using about 15-20% load on a plateau for about 5 seconds then it drops to zero and repeats.  This starts the moment the second loads until i power it off.  It is always occurring, even during system idle.

Looking at iotop there is nothing happening during the 5 seconds of hi IO usage but during the drop to zero it shows jbd2/sda3-8 with high disk write rate.

I'm not sure what caused this what I can do to fix it; google proved useless.  Really I have no idea where to begin trouble shooting.

Any help would be greatly appreciate!  Thanks!

---

### Post by wewantutopia on 2014-09-02
The odd thing is when the indicator shows IO activity has stopped, that is when iotop shows heavy usage (for about 1 second) and when the hard drive led blinks.  When the indicator shows I/O activity has resumed iotop shows more or less idle.

Any ideas where I cant start looking what is causing this?  Thanks!

---

### Post by wewantutopia on 2014-09-02
Yelp, it turns out it was I/O on a flash drive that was plugged in and not the hard drive.  Phew...  good thing since I had no idea how to solve it....

---

