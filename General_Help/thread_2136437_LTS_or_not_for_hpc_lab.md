---
title: "LTS or not for hpc lab"
date: 2013-04-17
forum: General Help
---

### Post by Pacopag on 2013-04-17
Hi.  I'm setting up a cluster for some scientific computing, and I'm thinking that Ubuntu would be a good choice of OS (opinions/alternatives are welcome).  I'm just wondering if I should use 12.04 (LTS) or the latest release.

It's been a while since I used ubuntu (probably since 8.04, or maybe 9.10, can't remember) and I have a couple questions:

1. If I go with the latest release (e.g. 13.04) how seamless is it to upgrade to the next release when it comes out?  I remember usually ending up with a partly broken system when I'd try to upgrade in the past.

2. How much more up-to-date will packages be in the latest release compared to the LTS?  How great will the difference be by the time 12.04 runs out of support?

I welcome any other discussion on the matter too.  Thanks a bunch for any advice.

---

### Post by TheFu on 2013-04-17
I'd suggest that you ask for recommendations on the HPC forums to get better answers.  It also matters if your cluster is 3 PCs or 50,000 which solution you should further research.

When it comes to picking any Ubuntu/Mint release, I always choose LTS over "newer" when possible.  Other releases only have 18 months of patch support where the LTS gets 5 yrs. That is very important in a long running project.  LTS releases tend to be more stable and fewer "alpha level" programs are included.  Stability is the primary goal for an LTS, unlike for the mid-LTS releases where Canonical seems to inflict changes on users following their vision, not necessarily what the community desires.  The only time I'd select a newer release is when there is something specific in those newer releases that I need.  For example, if you have an UEFI BIOS, then 12.04 isn't a good choice, you'd want something newer.

---

### Post by Pacopag on 2013-04-18
Thanks for your input.  The UEFI BIOS is a good point.  Is there any other distro you'd suggest maybe?...since the next LTS isn't due for a couple years.  I have a feeling that some newer software may be needed.  But I guess I could always install that stuff from source (right?).

---

### Post by papibe on 2013-04-18
> **TheFu said:**
> if you have an UEFI BIOS, then 12.04 isn't a good choice, you'd want something newer.
That is no longer an issue. If you get 12.04 on Ubuntu.com you'll be downloading 12.04.4. That version supports UEFI.

Regards.

---

### Post by Pacopag on 2013-04-18
Thanks papibe.  Very good to know.

---

