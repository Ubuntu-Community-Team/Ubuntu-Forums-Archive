---
title: "Acer compatibility"
date: 2024-09-30
forum: General Help
---

### Post by alpetjr on 2024-09-30
I'm looking for a new laptop and I tried a ASUS VivoBook and there is no network driver for it. I was thinking of a Acer but it isn't listed in the Ubuntu Certified Laptop page. Has anyone had any luck running Ubuntu on a new Acer? I'm looking for a 16" - 17" with a actual SSD hard drive not intergrated. Thanks Much

---

### Post by TheFu on 2024-09-30
> **alpetjr said:**
> I'm looking for a new laptop and I tried a ASUS VivoBook and there is no network driver for it. I was thinking of a Acer but it isn't listed in the Ubuntu Certified Laptop page. Has anyone had any luck running Ubuntu on a new Acer? I'm looking for a 16" - 17" with a actual SSD hard drive not intergrated. Thanks Much

Compatibility isn't just at the vendor level.  I've had an Acer that worked great.  My LUG used to hold InstallFests at the start of every college semester, and a few students would show up with cheap Acer laptops that we couldn't get Linux onto.   You'll need to be EXTREMELY specific with the exact model.  For example, I had an Asus VivaBook (Core i5-8250u) that basically worked immediately when I got it - wifi, video, everything "just worked".   **_Compatibility is very specific to the hardware inside each system.  _**

In July, I got a new-to-me Dell 5320 laptop ($265 A+ condition) that also "just worked".  It has a Core i5-11xxxx CPU.  I had to change a few BIOS settings to be linux friendly, but that isn't odd.  The laptop came with Win10 Pro, which I quickly wiped.  I have no need for that spyware or their EULA that allows them to do anything they like on my hardware.  I haven't tested the fingerprint reader on it, as I never intend, ever, use risk my fingers over data on any computer.

Don't get too worried about systems that aren't specifically "certified" for Ubuntu.  Well, there are some servers from HP/Compaq that only worked with 1 specific release, but never again, but that was a long time ago.

So, when looking for acceptable hardware, you'll need to get much more specific. It is best to find exact model numbers (not the "5320", but the non-humans understandable model number that is on the box, never used in advertising, because the advertised numbers are "lines" of laptops, not exact configurations.  You need the exact configuration so you can look up the motherboard, network, webcam, microphone and other details.

Or just look through these forums for recent "I'm looking for a laptop" posts within the last few months.  Or you can post the specifics priorities for what you seek and the budget you have for recommendations.  In general, Lenovo and Dell are the most Linux compatible laptops.  That doesn't mean others don't work or can't work, but many builders self-design their systems and use odd chips to save $0.50 on really cheap wifi chips that nobody has seen before. Those systems will eventually work, probably, within 2 yrs, assuming a wifi driver guy gets one and has an itch to make it work.  Around 2018, there was a $90 Lenovo really, really, cheap laptop.  The wifi chip inside it didn't work with linux.  Took 6 months for someone to create a driver, but over a year later (18 months) before the driver started being included in kernels and 3+ more months before the popular distros started including that driver.

Anyway, hope this helps you make the best, informed choice possible ... or at least to post helpful, specific, data so people can help.

---

### Post by oldfred on 2024-09-30
If you call most vendors, their help desk will not offer any support for Linux unless pre-installed. 
The help desk scripts are just for Windows.

But some vendors offer firmware update directly from Linux with fwupdate.
I consider those at least indirectly recognize Linux installs.

[https://fwupd.org/](https://fwupd.org/)
Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

---

### Post by n1kz-t7 on 2024-10-01
I run a 2022 Acer Aspire 5, non-touch without a fingerprint reader. I've had no compatibility issues whatsoever. Everything works perfectly.

---

### Post by alpetjr on 2024-10-01
I'm real apprehensive about choosing a new laptop. Been using Ubuntu for about 20 years ,not good with the command line. No time to really learn it. After what I went through with a new Asus vivobook, the WiFi driver is Windows only, so I took it back. The Asus I have is about 8 years old but it is in need of replacing. Thanks I'll keep reading

---

### Post by alpetjr on 2024-10-19
Update. I did a lot of research and I decided on a laptop. Lenovo Thinkpad T16 Gen2 AMD. It comes preinstalled with Ubuntu. Thanks for the help
[h=1][/h]

---

