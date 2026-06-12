---
title: "Added a DVD RW drive now boot takes over 5 minutes"
date: 2007-04-05
forum: General Help
---

### Post by NICU on 2007-04-05
Hi, I've been using Ubuntu for close to a year and love it.  Have an AMD system ~2.0GHz with 1.5GB RAM, so Ubuntu (Edgy) has always booted in 1-2 minutes.  I had an old DVD RW drive burn out so I replaced it with an [NEC Super Multi (AD-7170A)]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=N27-1896")  The first time I booted it came up right away, the second and third times since then it took over 5 minutes to boot up.  The only other times this has happened were times that Ubuntu was checking my ext3 drives, I did not receive the messages I usually get when that happens.  I didn't get any messages, just a blank screen with a blinking cursor on the top left.

The new drive is set as the master on the second IDE channel, I also have an older DVD drive which is setup as the slave on that same channel.  BIOS correctly identifies both drives and once Ubuntu is up and running both drives read CD/DVDs correctly.

---

### Post by DoctorMO on 2007-04-05
Is it the BIOS that is taking time to boot?

Have you checked the dmesg log for hardware conflicts of just a 'Waiting for DVD drive to come alive' message?

Good luck.

---

### Post by NICU on 2007-04-06
Hi, I haven't seen anything weird in my dmesg log.  After the first few minutes it goes back to booting correctly and the next thing to appear on the screen is "Activating Swap" followed by "Checking file systems" (not sure if those are the exact words).  I may try to make some changes in the BIOS...  If anyone has any suggestions please let me know.

---

### Post by lukew on 2007-04-06
> **NICU said:**
> Hi, I've been using Ubuntu for close to a year and love it.  Have an AMD system ~2.0GHz with 1.5GB RAM, so Ubuntu (Edgy) has always booted in 1-2 minutes.  I had an old DVD RW drive burn out so I replaced it with an [NEC Super Multi (AD-7170A)]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=N27-1896")  The first time I booted it came up right away, the second and third times since then it took over 5 minutes to boot up.  The only other times this has happened were times that Ubuntu was checking my ext3 drives, I did not receive the messages I usually get when that happens.  I didn't get any messages, just a blank screen with a blinking cursor on the top left.

The new drive is set as the master on the second IDE channel, I also have an older DVD drive which is setup as the slave on that same channel.  BIOS correctly identifies both drives and once Ubuntu is up and running both drives read CD/DVDs correctly.

I would check your master slave setup. I would not put things on auto select either; that slows things down to. Saying that 5 minutes longer is excessive for the bios hd checks.

---

### Post by m4xr8d on 2007-04-06
i recently experienced the same situation on several boxes. it was affecting both windows and linux installs. a quick BIOS update solved the problem

---

