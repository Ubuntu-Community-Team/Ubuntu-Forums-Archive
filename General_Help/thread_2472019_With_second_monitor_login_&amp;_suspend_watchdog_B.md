---
title: "With second monitor login &amp; suspend: watchdog: BUG: soft lockup - CPU#3"
date: 2022-02-15
forum: General Help
---

### Post by Dáire Fagan on 2022-02-15
[FONT=arial][COLOR=#232629]Only since adding a second monitor have I been experiencing soft lockups on suspend and roughly 20% of logins on Ubuntu 20.04 - I do not experience either of these issues with just a single monitor connected.[/COLOR]
[COLOR=#232629][B]
Hardware Details:[/B][/COLOR]
[COLOR=#232629]My existing Acer XB270HU only has a single DisplayPort input (and no other inputs at all) and my GTX 970 only has one Displayport output and one HDMI output. A new MSI MAG274QRF-QD is now instead using the DisplayPort output and I have connected the Acer back to the graphics card using this [HDMI to DisplayPort adapter]("https://www.amazon.de/gp/product/B08HGSGVXD/ref=ppx_yo_dt_b_asin_title_o01_s02?ie=UTF8&psc=1"). The motherboard is a Gigabyte GA-Z97MX-Gaming 5. CPU: [/COLOR][/FONT]i5-4690K.[FONT=arial]
[COLOR=#232629][B]
Intermittent Soft Lockup on Login[/B][/COLOR]
[COLOR=#232629]Even when it does not crash it can take between 40 seconds and 90 seconds after login for my desktop to appear though when just using one monitor this happens in seconds. When it crashes the screen (or screens as it varies between one or both having signal immediately after login) will display a black screen and then the cursor will load either frozen from the beginning or almost immediately after appearing. When this occurs I am unable to get to a TTY and REISUB works at least sometimes.[/COLOR]
[COLOR=#232629]The login screen mostly loads on the old Acer but sometimes it loads on the MSI, although there seems to be no pattern between this and the frozen cursor.[/COLOR]
[COLOR=#232629][journalctl]("https://pastebin.ubuntu.com/p/scr394ScMC/") [syslog]("https://pastebin.ubuntu.com/p/zrTrdQ2pHP/") [Xorg.0.log.old]("https://pastebin.ubuntu.com/p/VCzCSQKxS6/") Xorg.1.log.old: Nothing for the same time period[/COLOR]
[COLOR=#232629][B]
Soft Lockup on Suspend[/B][/COLOR]
[COLOR=#232629]When I try to suspend the monitors stop receiving the signal and turn off, the keyboard lights flash at least sometimes like the system is trying to suspend but the fans in my system keep going indefinitely. I cannot restore the display by typing on the keybaord, or trying a TTY, and REISUB seems to work at least sometimes.[/COLOR]
[COLOR=#232629][journalctl]("https://pastebin.ubuntu.com/p/MQ4SrfXkTx/") [syslog]("https://pastebin.ubuntu.com/p/sMBQ2q2CFM/") [Xorg.0.log.old]("https://pastebin.ubuntu.com/p/2353y3mSnh/") [Xorg.1.log.old]("https://pastebin.ubuntu.com/p/R6Cp3jhsbq/")[/COLOR]
[COLOR=#232629][I]
Separate to Ubuntu but may be relevant is that POST and the prompt to unlock my encrypted volume (before the Ubuntu login prompt) appear only on the Acer but in low resolution in the form of a miniature screen in the middle of the display - I expect this is down to the adapter, which works fine once I am logged into Ubuntu successfully. I would prefer this all to happen on my new MSI and in fullscreen but I have found no setting in the BIOS to do this, and I have tried enabling CSM.[/I][/COLOR]
[COLOR=#232629]
Is there something that might resolve these two issues?[/COLOR][/FONT]

---

### Post by Dáire Fagan on 2022-02-17
Extra detail combined into OP.

---

