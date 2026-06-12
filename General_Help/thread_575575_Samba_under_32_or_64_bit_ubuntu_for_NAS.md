---
title: "Samba under 32 or 64 bit ubuntu for NAS?"
date: 2007-10-14
forum: General Help
---

### Post by njparton on 2007-10-14
Openfilter looks horrendously complex and Samba under FreeNAS doesn't perform particularly well (a FreeBSD issue?). So I'm going to build a home NAS device based around an ubuntu desktop installation with a 3ware hardware RAID card (9500S or 9650SE) and a low power AM2 uATX MB/case with an AM2 Sempron. The initial RAID array will use 2x seagate 750GB SATA II hard drives in RAID 1.

My question is whether I should go for 32 or 64 bit ubuntu - which will yield the best Samba performance over a gigabit network using an onboard nforce gigabit nic?

I've googled quite a bit for Samba 32 and 64 bit performace comparisons and not really found anything useful.

Does anyone here have an opinion/prediction for this?

The NAS device will serve as a document, HD video, photo etc store for a group of PC's running Vista (mixture of x86 and x64). File sizes are therefore lilkely to span the range 100KB to 2GB.

---

### Post by fjgaude on 2007-10-14
> **njparton said:**
> My question is whether I should go for 32 or 64 bit ubuntu - which will yield the best Samba performance over a gigabit network using an onboard nforce gigabit nic?

Does anyone here have an opinion/prediction for this?

Well, from recent experience with what you are getting ready to do either will work just fine. I don't think you will see any difference in network throughput, speed. If you are going to use Ubuntu 7.10 released version as the OS the 64-bit will likely not cause any more trouble than the 32-bit version. If you are using 7.04 or 6.06, go the 32-bit route.

Make sure you install and setup Samba (Shares Folers) in Ubuntu. They are not setup as default.

What is your CPU clock rate?

---

### Post by njparton on 2007-10-14
I'm going to go for a low powered sempron as it will will be in small case I can only squeeze in a small HSF.

Probably <2GHz or 3000+ (which ever you believe!).

I didn't think Samba was CPU intensive?

I'm also going to wait for 7.10 and possibly plump for x64 with 1 gig RAM.

---

### Post by fjgaude on 2007-10-15
The CPU has to be fast enough to keep up with the fast disk speeds. Single disk has a 77 MB/sec throughput these days.

You will do fine the way you are going.

---

### Post by njparton on 2007-10-15
Would dual core be an advantage then?

---

### Post by fjgaude on 2007-10-15
Well, if you have only one process, task active, likely not. If you intend to be using it for more than NAS than, maybe.

---

