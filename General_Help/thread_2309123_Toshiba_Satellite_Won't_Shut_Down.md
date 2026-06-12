---
title: "Toshiba Satellite Won't Shut Down"
date: 2016-01-07
forum: General Help
---

### Post by 2guntom on 2016-01-07
Toshiba Satellite A135-S2326 laptop
Intel Celeron M processor
1GB RAM
Xubuntu 14.04.3 32bit installed from USB iso

To get the install to work I had to run it with option ACPI=off
in the GRUB file it has the line "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off" ; this has to be there or Xubuntu will not start.
The laptop starts fine, runs fine, and restarts fine.
The problem is shutting it off. I see the Xubuntu screen with the swirling circle. It shows for a few seconds, then freezes. To power the laptop off, I have to hold the power button.

I have been all over the askubuntu pages, the forums, Google, wiki, and I have tried everything I found at least twice to no avail. In the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" I have tried reboot=bios, reboot=this, reboot=that... I've tried them all. Nothing works.

I'm missing something... what is it?

---

### Post by 2guntom on 2016-01-08
Sooooo...

---

### Post by 2guntom on 2016-01-09
Wow... I must be in the wrong forum

---

### Post by sammiev on 2016-01-09
Hi,

Have you went into addition drivers yet and see what's available?

I'm not sure but the specs on line shows it may have a ATI Radeon® Xpress 200M 128MB dynamically allocated shared graphics memory.

---

### Post by 2guntom on 2016-01-09
> **sammiev said:**
> Hi,

Have you went into addition drivers yet and see what's available?

I'm not sure but the specs on line shows it may have a ATI Radeon® Xpress 200M 128MB dynamically allocated shared graphics memory.

Yes I did; there was nothing there

---

### Post by 2guntom on 2016-01-09
I used the "additional driver" tool. Are you referring to downloading drivers from ATI/AMD?

---

### Post by sammiev on 2016-01-10
> **2guntom said:**
> I used the "additional driver" tool. Are you referring to downloading drivers from ATI/AMD?

I was talking about additional driver tool.

It's an old card, one that I haven't played with.

---

### Post by 2guntom on 2016-01-10
So, I finally found a computer that Xubuntu won't run on?
Hmm...

Very disappointing

---

### Post by 2guntom on 2016-01-10
Hours of Googleing tell me this is a hardware issue.
I did update the bios to the most recent version.
The system is halting instead of shutting down. I have tried the various commands in a terminal window to cause/force it to shutdown/shutoff with no joy; it still halts.

Is there something else I can try?

---

### Post by 2guntom on 2016-01-13
After a week of messing with this thing, suffering through cpu lockups, touchpad driver crashes and running every command line in the grub file I could find, I ended up putting Windows Vista back on it. That is not mind boggling enough; what is mind numbing is that Windows Vista works!

So, this must be the holy grail of Microsoft computers or a key that Bill Gates lost somehow since it is a laptop that ONLY works with Windows...

I'm going to bed and hope that I awake back in MY universe tomorrow

---

