---
title: "Random hard crashes and power off"
date: 2014-10-15
forum: General Help
---

### Post by wboziuk on 2014-10-15
Hope you can help me! My computer often has either a hard crash - where the screen breaks up into flashing blocks and cannot be recovered - or a complete power off. Just going along, doing your thing, and then "CLICK!" ... power is cut. Power will cycle back on a few seconds later and the computer boots.

Your challenge, should you choose to accept it: help me figure out the cause? See details below.
1. Not a heat issue (my first thought!). This is a low-power, well-ventilated desktop. Temps do not go over 50C, ever. The issue can even occur just after boot.
2. No discrete graphics card. IE, using the stock Intel 4400 graphics and the Ubuntu driver.
3. Can happen on either browser, Chrome or Firefox. Happens with hardware acceleration on/off, GPU blacklist on/off.
4. Can happen when browser is closed, though very rare.
5. Happens on both Ubuntu and Lubuntu desktop environments (Unity and LXDE)
6. Have run memtest for a few hrs, no errors found.
7. Can happen when playing videos or scrolling. It's pretty random, but the only way I can reliably reproduce a power off is with this excellent [video of Norway]("http://petapixel.com/2014/09/29/breathtaking-motion-time-lapse-tour-norway/") from Vimeo. These things tell me it has *something* to do with content on web pages ... probably.

Happy to post the tail end of the syslog if it's helpful!

System info:
Corsair CS450M PSU 
Gigabyte B85N motherboard
Core i3 4130 processor
Intel 4400 graphics
8GB RAM / 64GB SSD
WiFi b/g/n on the motherboard (not quite integral - came plugged into the slot). This required a third-party driver that Ubuntu identified.
Currently using HDMI graphics; DVI has same issue.
Ubuntu 14.04 (upgraded from 13.10, where I don't *think* I had this issue, but can't recall clearly)

I have a few not-yet-tested suspicions but in order to not bias anyone I'll keep them for now. Thank you!!!

---

### Post by Bucky Ball on 2014-10-15
Welcome. You make no mention of what brand your PSU is. A generic silver box? If so, how old? Also, did this start happening out of the blue when the machine had been working fine for a month/year? It just started happening when everything had been running fine previously?

Please, go ahead and test your theories and let us in on what happens. It is only going to help, not hinder, in your quest for support.

If this happens randomly when you have no browser open I doubt it has anything to do with the content of web-pages. Sounding more like hardware to me. Do you have Windows too? I suggest you experiment in that for an hour or two if you do.

---

### Post by wboziuk on 2014-10-15
It is a Corsair PSU. It's the same age as everything else on the list, ~6 mos. I think Ubuntu 13.10 ran fine for ~1 mo before I upgraded to 14.04, at which point the problem started to happen intermittently. It's possible the problem occurred with 13.10 and I just didn't pick up on it; 13.10 was not in place that long. Although I said that the problem can occur with the browser closed, I only observed this once and I can't say for 100% certain that there *wasn't* a process or hidden window in that one case. This machine runs only Ubuntu, not Windows.

This is really a toughie for me. The crashes are one thing, but the (more common) abrupt power cuts are another. I can't think of much beyond a memory, heat, or PSU issue that causes that -- but the cut can be reliably set off by playing the video I linked to. I'll try it again now :)

---

### Post by christopher9 on 2014-10-16
I have the same exact issue with a Toshiba P50-A running Nvidia Gt740M/Intel hybrid graphics..totally random, no errors in any log files, no heat issues, all software up-to-date, etc...happens whether using Noveau driver, whether using Nvidia card or Intel onboard, on battery or on AC power, happens with elementary OS Freya, Lubuntu/Ubuntu 14.04/14.10, Zorin OS, or PCLinux (I have never dual-booted)...switched out AC power supplies...no help

I'm beginning to suspect something with my Logitech wireless KB/Mouse receiver because it seems to occur most often when I am scrolling through web content but it does happen with the laptop just sitting idle as well...annoying but not a dealbreaker so far for me as I don't game at all and I backup my stuff religiously....hope you find a solution!

---

### Post by wboziuk on 2014-10-17
Interesting, you know, I hadn't seriously thought about the mouse as a possibility. Because the Logitech dongles work just fine on basically every OS (Windows, Linux, ChromeOS), and also because, it seems odd to me that such a basic peripheral could cause a power cycle event. Maybe I should consider that, or at least eliminate it as a possibility. I am not sure if I have any wired mice I can use for testing or not.

I think I may be at the point where I need to try swapping components, which is pretty discouraging. I am very knowledgeable about how everything screws together, but I just don't have spares of anything lying around so I would have to buy them.

A power supply is cheapest, but I'm most worried this is a motherboard issue, or the on-chip GPU. I suppose I could always buy a nice GPU and see if that cleared it up, haha ... !

---

### Post by tgalati4 on 2014-10-17
Motherboards do fail and in a fashion similar to what you describe.  Put in a video card and see if reliability improves.  Has this machine seen extensive gaming over the past 6 months?  On-board GPU's get hot and warp causing problems.  Does the GPU run +10C hotter than the CPU?

Run memtest for several hours.  That will test the CPU, motherboard, RAM, but not really exercise the GPU.  If it passes (at least 10 full passes), then you can try using one graphical app (extremetuxracer) and see how quickly your machine locks up.  Monitor the GPU temps on another machine logged in with ssh.  If it locks up before you get to the bottom of the hill, then you know the issue.

---

### Post by wboziuk on 2014-10-17
No gaming, no. I'd love to know the GPU's actual temp but there is no temp sensor labeled "GPU," or documentation on where each of the sensors are. Beyond the two core sensors, there are a few labeled "temp 1" and I suspect the second "temp 1" may be the GPU. It tends to run in line with the higher-temp core.

I'll try extremetuxracer, and see if that temp reading spikes, thanks!

---

### Post by wboziuk on 2014-10-19
Sadly, not the Logitech mouse. Although it fooled me with a period of no crashes during that Norway VIMEO movie after a swapped in a standard corded USB mouse! Didn't last forever though.

I played extremetuxracer for a bit while watching the temperature monitors. Either there is no sensor for the GPU, or that's no issue whatsoever. There was no temp above 105F throughout. No crashes during that test either, but fire up that VIMEO movie and within a few minutes, ... "CLICK!" [off...]

---

### Post by tgalati4 on 2014-10-20
I presume you are using wired networking.

The video is streamed, so that implies the network chip.  On some Intel boards, the Southbridge controls both the audio chip and the network chip, so streaming anything can cause it to heat up and lock up the data bus solid.  Try streaming music from Pandora for an hour and see if locks up.  Put your finger on the Southbridge chip and see if it is hot.  If you can't keep your finger on it for more than 30 seconds, then it is hot.

TuxRacer proves that your GPU is working OK, so we can move on to other things.

---

### Post by wboziuk on 2014-10-21
Actually no, wireless. There is a broadcom (I think) wireless chip that I am using; it's part of the board as shipped. Purely as an aside, the placement is poor; it clears the CPU fan, but the screwdriver needed to free the chip - it's removeable - doesn't. 

I have been wanting to try wired in case it's the wireless driver, however that requires moving the entire setup to somewhere with a network jack. That is obviously do-able, but just a big pain.

What is the Southbridge chip? There is a small (in inch sq) heat sink on the board, is that it? It certainly can be warm sometimes, so I infer, that the chip underneath must be quite toasty indeed :) That heat sink is located on the lower left of[ the top-view picture]("http://www.gigabyte.com/products/product-page.aspx?pid=4844#ov"), between the PCI and RAM slots.

Is what you are describing a* normal* limitation? Surely a current motherboard would need to be somewhat broken for it to not be able to stream both audio and video, right?

---

### Post by wboziuk on 2014-10-21
My trusty infrared hand-cannon (ok, thermometer) records that the two hottest components on the board are the wireless card and the heat-sink-covered bit I was discussing. Both topped out at ~99.5F, and maintained that temp while the video played small-screen. When I maximized the video, the system crashed within 30 seconds, but the temperature did not increase during that time.

The below is a snip of the end of the syslog. (Please ignore the Think-Pad-T400; that's just the name I gave the SSD when I installed Ubuntu to test the OS/SSD prior to sticking the drive in the desktop build). The last line is a very typical thing before a crash (but not always); I haven't been able to figure out what it means. It may be a red herring.

Oct 21 21:11:21 wboziuk-ThinkPad-T400 NetworkManager[765]: <info> Activation (wlan1) successful, device activated.
Oct 21 21:11:21 wboziuk-ThinkPad-T400 dbus[702]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct 21 21:11:21 wboziuk-ThinkPad-T400 NetworkManager[765]: <warn> dnsmasq appeared on DBus: :1.57
Oct 21 21:11:21 wboziuk-ThinkPad-T400 NetworkManager[765]: <info> Writing DNS information to /sbin/resolvconf
Oct 21 21:11:21 wboziuk-ThinkPad-T400 dnsmasq[3157]: setting upstream servers from DBus
Oct 21 21:11:21 wboziuk-ThinkPad-T400 dnsmasq[3157]: using nameserver 192.168.1.1#53
Oct 21 21:11:21 wboziuk-ThinkPad-T400 dbus[702]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 21 21:11:21 wboziuk-ThinkPad-T400 ntpd[933]: ntpd exiting on signal 15
Oct 21 21:11:21 wboziuk-ThinkPad-T400 whoopsie[1121]: message repeated 2 times: [ offline]
Oct 21 21:11:21 wboziuk-ThinkPad-T400 whoopsie[1121]: online
Oct 21 21:11:22 wboziuk-ThinkPad-T400 avahi-daemon[757]: Joining mDNS multicast group on interface wlan1.IPv6 with address fe80::260a:64ff:fe95:7cee.
Oct 21 21:11:22 wboziuk-ThinkPad-T400 avahi-daemon[757]: New relevant interface wlan1.IPv6 for mDNS.
Oct 21 21:11:22 wboziuk-ThinkPad-T400 avahi-daemon[757]: Registering new address record for fe80::260a:64ff:fe95:7cee on wlan1.*.
Oct 21 21:11:24 wboziuk-ThinkPad-T400 NetworkManager[765]: <info> WiFi hardware radio set enabled
Oct 21 21:11:29 wboziuk-ThinkPad-T400 ModemManager[721]: <info>  Creating modem with plugin 'Generic' and '1' ports
Oct 21 21:11:29 wboziuk-ThinkPad-T400 ModemManager[721]: <warn>  Could not grab port (tty/ttyS4): 'Cannot add port 'tty/ttyS4', unhandled serial type'
Oct 21 21:11:29 wboziuk-ThinkPad-T400 ModemManager[721]: <warn>  Couldn't create modem for device at '/sys/devices/pci0000:00/0000:00:16.3': Failed to find primary AT port
Oct 21 21:11:31 wboziuk-ThinkPad-T400 ntpdate[3310]: adjust time server 64.113.32.5 offset 0.307934 sec
Oct 21 21:11:31 wboziuk-ThinkPad-T400 ntpd[3363]: ntpd 4.2.6p5@1.2349-o Wed Oct  9 19:08:06 UTC 2013 (1)
Oct 21 21:11:31 wboziuk-ThinkPad-T400 ntpd[3364]: proto: precision = 0.191 usec
Oct 21 21:11:31 wboziuk-ThinkPad-T400 ntpd[3364]: ntp_io: estimated max descriptors: 2144, initial socket boundary: 16
Oct 21 21:11:31 wboziuk-ThinkPad-T400 ntpd[3364]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Oct 21 21:11:31 wboziuk-ThinkPad-T400 ntpd[3364]: Listen and drop on 1 v6wildcard :: UDP 123
Oct 21 21:11:31 wboziuk-ThinkPad-T400 ntpd[3364]: Listen normally on 2 lo 127.0.0.1 UDP 123
Oct 21 21:11:31 wboziuk-ThinkPad-T400 ntpd[3364]: Listen normally on 3 wlan1 192.168.1.10 UDP 123
Oct 21 21:11:31 wboziuk-ThinkPad-T400 ntpd[3364]: Listen normally on 4 lo ::1 UDP 123
Oct 21 21:11:31 wboziuk-ThinkPad-T400 ntpd[3364]: Listen normally on 5 wlan1 fe80::260a:64ff:fe95:7cee UDP 123
Oct 21 21:11:31 wboziuk-ThinkPad-T400 ntpd[3364]: peers refreshed
Oct 21 21:11:31 wboziuk-ThinkPad-T400 ntpd[3364]: Listening on routing socket on fd #22 for interface updates
Oct 21 21:11:41 wboziuk-ThinkPad-T400 NetworkManager[765]: <info> (wlan1): IP6 addrconf timed out or failed.
Oct 21 21:11:41 wboziuk-ThinkPad-T400 NetworkManager[765]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct 21 21:11:41 wboziuk-ThinkPad-T400 NetworkManager[765]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct 21 21:11:41 wboziuk-ThinkPad-T400 NetworkManager[765]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct 21 21:11:43 wboziuk-ThinkPad-T400 kernel: [   32.262141] audit_printk_skb: 177 callbacks suppressed
Oct 21 21:11:43 wboziuk-ThinkPad-T400 kernel: [   32.262150] type=1400 audit(1413940303.273:70): apparmor="STATUS" operation="profile_replace" parent=4277 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=4281 comm="apparmor_parser"
Oct 21 21:11:43 wboziuk-ThinkPad-T400 kernel: [   32.262170] type=1400 audit(1413940303.273:71): apparmor="STATUS" operation="profile_replace" parent=4277 profile="unconfined" name="/usr/sbin/cupsd" pid=4281 comm="apparmor_parser"
Oct 21 21:11:43 wboziuk-ThinkPad-T400 kernel: [   32.263130] type=1400 audit(1413940303.273:72): apparmor="STATUS" operation="profile_replace" parent=4277 profile="unconfined" name="/usr/sbin/cupsd" pid=4281 comm="apparmor_parser"
Oct 21 21:11:49 wboziuk-ThinkPad-T400 ntpd_intres[935]: parent died before we finished, exiting

---

### Post by tgalati4 on 2014-10-21
That big heatsink is the on-board graphics chip which drives your DVI and HDMI connections on the motherboard.  I believe the Southbridge chip is the ITE chip.  You can put your finger on it and see if it is hot while streaming music.  I have seen holes burned in Southbridge chips due to overuse, or possibly manufacturing defect.

Take out the wireless (or turn it off in BIOS) and run an ethernet cable to isolate.  It may be difficult for you to do it, but it is impossible for me to do it.

It's interesting that *ntpd* terminated twice.  Perhaps your motherboard is having clock issues.  

I have had defective (burned out) wireless cards crash laptops before.  Because the cards are on the PCI bus, when they glitch, Bad Things Happen(tm).  

Can you play a similar HD video from the local drive and see if the machine is stable?  It's possible that your wireless chip has delaminated.

---

### Post by wboziuk on 2014-10-22
Ok, a few things for me to try then.
[COLOR=#000000]"It may be difficult for you to do it, but it is impossible for me to do it"[/COLOR]
This made me laugh, definitely a true statement! I'll move the machine over the weekend (I would need a much longer cord than I have to run one to the current location.)

The ITE chip does not run hot. I looked at the diagram, that is an ITE super I/O chip. All that is running is the PS2 keyboard. The one with the heat sink is the B85 chipset. The block diagram has this connected up to the CPU and out to the USB/BIOS/SATA/Super IO/Codec/LAN ... So I think maybe this is not quite what you would call a southbridge chipset, instead it is a Platform Controller Hub. Bear with me I am learning as I go.
The heat of that chip does concern me.

The other mode of failure is not the power cut, but instead a hard freeze and blocked/flashing graphics patterns. (would an alternate driver possibly be of help? Ubuntu should be using the stock Intel driver though ..) These two failure modes could be two separate root causes, of course.

If I can eliminate the wireless card as the issue, then I am down to 1) the B85 chip or 2) something relating to ntpd, which I'll have to research in much more depth if I need to troubleshoot it. 

But given that the power can be cut *and then restored* I lean more towards a hardware issue than software (possibly incorrectly ...)

---

### Post by wboziuk on 2014-10-22
I'm also wondering about the audio driver. I haven't looked into that yet. I don't know what driver is in use.

---

### Post by tgalati4 on 2014-10-23
For the audio driver, open a terminal:

```
aplay -l
```

Yes, different manufacturers call the supporting chips by different names.  To reduce cost, more and more functions are put on a single chip.  Platform Controller Hub sounds like a likely suspect.  Since it controls SATA, pull out your disks and boot off of a LiveUSB stick.  See if your system is stable by running in RAM only.  Then use a wired network to see if you can watch Youtube videos or stream music during the Live session.  If that works, then put in one disk and boot from it and see if it is stable.  Monitor the temperatures of the B85 during your testing.

It's possible that your motherboard has developed a defect--one that is likely not repairable.

---

### Post by wboziuk on 2014-10-23
Lots of crashing in testing last night. Fiddled with a number of BIOS settings, monitored SYSlog, nothing useful came of any of it, sadly. So I won't bore you with it. 

I looked up B85 PCH specifications; thermal limit is over 100C for that component, so actually an exterior heatsink temp of 95F/30C or a sensor temp of 38C (which is what I am seeing) is not that concerning to me. Additionally the computer is fully capable of crashing 30 seconds after boot with a video streaming, and at that stage no components have had the chance to heat up. 

Still working on this one. More time over the weekend, maybe. I probably should have started with the wireless card test given how bad they are on Linux. Thanks for your help to date :)

---

### Post by wboziuk on 2014-10-24
Ok, update. I have moved the computer to a wired location and disabled the Broadcom wireless card driver. So I know it's not using the card, but it does still get warm. There was no difference at all in crash-when-streaming-video performance.

I also noticed that after a crash, the system can no longer auto-restart. The fan stops and then starts agian, but the computer does not boot. It only can boot if I shut off the power at the power strip, and wait for the PSU to click 3 times (I think it's the PSU, unless it's some sort of relay on the motherboard near the PSU). Then if power is restored the computer will boot when the power button is pressed.

Odd. And concerning. The above points me to the PSU or motherboard. But I don't know how to differentiate without buying another PSU. The PSU, by the way, can be seen to provide stable and in-spec voltage through the BIOS (obviously not under load). I'm thinking some sort of power protection relay being tripped, but I have no idea what to look at.

---

### Post by Bucky Ball on 2014-10-24
What kind of PSU is it? If it's a generic silver box, I'd be worried, but you may have found the culprit. If it's a newish name brand efficient PSU, doubtful the cause.

What are the details of your PSU?

---

### Post by wboziuk on 2014-10-24
It's a Corsair CX430M (hopefully remembering correctly). 80 Plus Gold. It was new, and should be a good brand. But it *was* offering a big rebate and I have heard rumors Corsair's lower-price PSUs are outsourced or not-that-great-quality. Of course you *can *have a failure in any PSU component regardless of quality, but it's less likely than the generic silver box.

---

### Post by wboziuk on 2014-10-24
My next step might be to disassemble the computer so I can physically separate the PSU and board on a bench -- that way when it fails i should be able to hear which component the click is coming from.

Actually before THAT I will probably do a 14.10 upgrade to see if a new kernel automagically solves the problem :) It is a relatively new board, and the problems started after the 14.04 LTS upgrade, so it's possible ...

---

### Post by Bucky Ball on 2014-10-24
Anything's worth a try I guess, but if a newer released killed 12.04, then unsure a newer release again that was released yesterday (is it actually released?) is going to make a lot of difference.

But worth a try.

PSU sounds fine.

---

### Post by tgalati4 on 2014-10-24
The clicking noise is probably the overcurrent relay in the PSU.  If your motherboard is drawing too much current (because of a shorted chip), it will cause the PSU to trip.  The simple way to find that shorted chip is to identify the hotspots on the board.  Any bulging capacitors?  It could be a bad board.  Do some web searching to see if others are having problems with that particular board.

---

### Post by wboziuk on 2014-10-25
Ok, a few updates!
1. There IS a hotspot on the board. It's just below and to the right of the wireless chip. It's an IC chip flush with the board, about 1/4 inch sq. All the capacitors on the board look good. Some hit 100F but not far beyond that.
2. I removed the wireless chip. No help.
3. Memtest ran 3 hrs, no errors.
4. Tried live USB. Same issue: power cut when streaming video or just web browsing (this ubuntuforums page here has caused 4 immediate crashes in a row for some reason, and it's not a very taxing page!)
5. One of my temperature sensors on the board has disappeared. None of them ever indicated an issue with high temps, but um, one has gone away.
6. I noticed that when the computer crashes, it would previously restart immediately. Now, the GPU fan spins up but no POST keyboard flashes. To restart I have to kill power physically to the PSU, then wait for CLICK! .. click.. CLICK! from the PSU before I can restart. And get this: it's now the same a*fter a proper shutdown!*


Thoughts on this? The IPv6 time out, apparmor, and ntpd are all typical - but not certain to occur - before a crash.

```
Oct 25 20:16:21 wboziuk-ThinkPad-T400 ModemManager[637]: <warn>  Couldn't create modem for device at '/sys/devices/pci0000:00/0000:00:16.3': Failed to find primary AT port
Oct 25 20:16:28 wboziuk-ThinkPad-T400 NetworkManager[770]: <info> (eth1): IP6 addrconf timed out or failed.
Oct 25 20:16:28 wboziuk-ThinkPad-T400 NetworkManager[770]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct 25 20:16:28 wboziuk-ThinkPad-T400 NetworkManager[770]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct 25 20:16:28 wboziuk-ThinkPad-T400 NetworkManager[770]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct 25 20:16:35 wboziuk-ThinkPad-T400 kernel: [   31.798019] audit_printk_skb: 75 callbacks suppressed
Oct 25 20:16:35 wboziuk-ThinkPad-T400 kernel: [   31.798021] audit: type=1400 audit(1414282595.793:36): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=4633 comm="apparmor_parser"
Oct 25 20:16:35 wboziuk-ThinkPad-T400 kernel: [   31.798026] audit: type=1400 audit(1414282595.793:37): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=4633 comm="apparmor_parser"
Oct 25 20:16:35 wboziuk-ThinkPad-T400 kernel: [   31.808147] audit: type=1400 audit(1414282595.805:38): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="third_party" pid=4633 comm="apparmor_parser"
Oct 25 20:16:38 wboziuk-ThinkPad-T400 ntpd_intres[963]: parent died before we finished, exiting
```

---

### Post by Bucky Ball on 2014-10-25
Please use [code] tags when posting code. See the last link in my signature for how. Thanks.

---

### Post by wboziuk on 2014-10-27
Will do. Sorry about that!

Ordered a replacement PSU on Amazon. Similar to (but cheaper than) the modular supply I have now, still Corsair to minimize the number of changes made at once.

I actually suspect the motherboard; that hot spot is either the wireless mini-PCIe slot or a cpu PWM power-management chip of some kind. But in general if someone was encountering this problem I would recommend a fresh PSU before anything else, plus motherboards are expensive enough I'd have to slog through a warranty process rather than just buying a new one.

---

### Post by tgalati4 on 2014-10-28
You will find out soon enough.  With a new power supply, the hot chip will either go pop, or something else will give out.  Troubleshooting motherboard shorts is difficult.  Any markings on the hot IC?  A simple google search will reveal what it is supposed to do and what the Vcc (feed voltage) is supposed to be.  For instance, if Vcc is 5 VDC on pin 1 and you measure 2.5 VDC on pin 1 in reference to chassis ground, then you are losing 2.5 volts at some amperage, (say 4 amps), that's 10 watts, and it will be hot to the touch.

---

### Post by wboziuk on 2014-10-30
Ok here I am trying to write! :)

I've been going through frankly endless a/b testing, swapping stuff out, fiddling with things. No luck.
- Testbed the computer, ie removed from case.
- New PSU. 
- New OS entirely. Puppy Linux. Slacko is great btw.
- The hot component is an ISL9582. Probably [this thing]("http://www.datasheet-pdf.com/search.php?sWord=isl9582"). Don't expect anyone to read through it :)
- Most recently, trying just one stick of 4GB RAM at a time. One of them ran all night, a big improvement. Testing the second now. 

I've done that last before, I think. But I'm at the stage now of thinking: "what's less hassle than calling the warranty line at Gigabyte?" Next up may be a BIOS update.

---

### Post by Bucky Ball on 2014-10-30
What happened when running from the other stick of RAM ONLY. Test them one at a time.

---

### Post by wboziuk on 2014-10-31
I tested that last night as I mentioned. It did have some crashes. Then I switched them back to the first. No crashes on the "good" stick. However I must test for a lot longer before drawing the conclusion - especially since I'm pretty confident I did this in the past and it would crash on either. I'll report back later.

I can also obviously run memtest some more although that has never found a flaw in the past.

---

### Post by tgalati4 on 2014-10-31
8 GB of RAM will draw a lot of current.  That PWM chip is rated for 150C.  And operating temperatures are up to 125C, so it does appear to rated for heat.  But, the tech sheet said it was "low cost" and "green", which may be incompatible with how you are building your machine.  Is your machine "low cost" and "green"?

Page 36 of the tech sheet calls out how the temperature protection is supposed to work.  It is quite sophisticated.  It's possible that something is out of specification causing these shutdowns.  A new motherboard (of identical make and model) may have the same problem with your selection of components.  Try a different PSU, different RAM, or a different brand or model motherboard.  It's hard to say at this point.

---

### Post by Bucky Ball on 2014-10-31
Test for a lot longer on the 'good' stick, then. That is the only way you'll know for sure. Even though mem test might not be showing an issue, if one stick isn't working in a practical test and the other is, then one's not working and the other is.

If you have any other RAM around that you know is working, perhaps you'd like to give that a whirl.

---

### Post by wboziuk on 2014-10-31
That'd be pretty disappointing if the motherboard couldn't support an i3 and 8G! It's supposed to handle any 1150 processor and up to 16GB ... plus something in the PCIx16 slot. No, this isn't an Z87 overclocker special, however it is supposed to be "ultra durable" (actually the reason I went with a business motherboard - 3 yrs warranty instead of a 1 year on an H81). But your point is good that if there's something out of spec I might be stressing it. Thanks :)

I'll got to the bottom of it one day ... when I do I'll post it here so a future problem-solver can find it. But there might be some more posts in the interim too!

And I don't sadly have any other RAM. Well I do, but this is the only desktop. Everything else around is SODIMM. And to think I almost got a thin-mini-ITX so I could use SODIMM, shoot! [But that cuts out the option to add a graphics card later, they don't (usually? ever?) have a x16 slot.

---

### Post by wboziuk on 2014-11-04
Update!

Several days of testing different stick combinations reveals a clear pattern. Stick A is good by itself, Stick B causes crashes either with stick A or by itself.

And so now the question is ... is it a bad STICK? Or something about the motherboard? Because stick B causes crashes either with or without Stick A, I'm going with that the stick is bad.

I did realize my motherboard has some previously unavailable options for component voltages and ram timing. And that this G.Skill Areas RAM has some documented issues with XMP. Some users report it may be more stable if you downgrade the frequency below the 1600 listed rate, or increase the voltage to other components even in situations where there is no overclocking going on. I did try a 1600->1333 change as a test. I also turned on XMP which sets the timings to 9-9-9-24 (the non-XMP are slower). There are some other options for interleaving too. And yes, it was more stable for a while with both sticks, but ultimately did crash eventually. So, I have plenty of other voltage options to play with potentially, but I need to read up a lot more on the topic before I start fiddling with voltages at the RAM, I/O or PCH. 

(Those options have always been available, it's just that there's a quirk in the BIOS wherein the options in those sections can only be toggled up and down with a keystroke, not entered with "enter" and then selected, like most options on the BIOS ... it's probably just a minor UI flaw, and makes it really unobvious that the fields can be changed. I had assumed that the options were only available to unlocked K-series processors, but it's not so. Or maybe they really don't want you to play with them.)

In the *near t*erm, the computer can be used just fine. The good stick is 4GB which is enough obviously for basic operations - though I've just discovered Darktable which really would like more! G. Skill has a lifetime warranty so I can see if I can replace before buying a new one.

Thanks for everyone's help! :D

---

### Post by tgalati4 on 2014-11-04
RAM should work out-of-the-box.  If it doesn't, then return it and get a new stick.  Since your board supports 16GB, you should not run into issues running 8 GB.  Tuning RAM can get you about 10% increase in transfer speed, in my experience.  The RAM gets hotter and uses more power, and you may or may not notice the speed increase since many times the hard disk becomes the bottleneck.  I would leave it on "auto" detection, unless you are doing something special and you know what you are doing.  

Declocking RAM can help to troubleshoot other problems.  Sometimes a failing motherboard chipset will work at a slower speed--this may give you a little more time out of old hardware, but if a computer isn't reliable, then it's not worth keeping.

---

### Post by Bucky Ball on 2014-11-05
> **wboziuk said:**
> Update!

Several days of testing different stick combinations reveals a clear pattern. Stick A is good by itself, Stick B causes crashes either with stick A or by itself.

And so now the question is ... is it a bad STICK? Or something about the motherboard? Because stick B causes crashes either with or without Stick A, I'm going with that the stick is bad.



I'd say bad stick. Next thing to do is test the slots. Sometime a slot can die. Try them one at a time in the first slot, check the outcome. If one works in that slot and the other doesn't, replace faulty RAM stick. If both work in the first slot and neither work in the second, second slot has died. My desktop has this issue but has four slots, so not problem, I just use two of the other three with a couple of 2Gb sticks and fine. ;)

Let us know the outcome. If one stick isn't working and the other is (in the SAME slot), no need to get more complicated about it. Chances are, and very good chances, that is a dead stick. If they are not a matched pair (i.e. identical make and model RAM) then one of the sticks might be too slow (or fast) for your motherboard's capabilities.

---

### Post by wboziuk on 2014-11-06
Agree that "very good chances" it's a memory issue. I've been doing some more testing. These are matched sticks by the way, g.skill Ares. Good looking things. Looks aren't everything.
 1) Stick A works fine - to date - by itself, at stock settings (1.54V, 1600MHz, 9-9-9-24, t1)
2) Stick B, either by itself or with Stick A, causes problems at these settings.
3) Stick B will work with Stick A under *very* conservative settings (1.57V, 1333MHz, 11-11-11-28, t2)

So ... this is interesting. Not that useful though. Although I *can* still run with 8GB, and 1.57V is technically still within spec, the settings are so slow that performance is no better than 4GB. Also in case you are wondering about the stock voltage, the MB supplies more power to RAM than the setting. If I really wanted the RAM to get only 1.50V, I'd have to put the setting at 1.46V. Vrin, Vcore and some other voltages are also a bit off target, although all within spec and all stable.

Here's another wrinkle. Shut down the computer and it won't start properly right away - it will spin up the fan, but not boot; I have to turn off the switch and let the PSU relays click 3x: CLICK (off) click CLICK. Clearly *that* isn't a RAM problem! Someone pointed out that maybe the two sticks together are asking causing overcurrent protection to kick in, which makes sense, but then how do I explain that Stick B by itself causes instability? And that Stick B works fine when I put *more *power through the two sticks? Aaaauuuughh so frustrating! No, this is not the most critical problem in my life, but it is one of the most annoying at present.

---

### Post by tgalati4 on 2014-11-06
You could be dealing with a "Triple Threat"--a bad power supply, a bad motherboard, and a bad RAM stick.  I would pick up a lottery ticket--your luck may change.

It's possible that all 3 components are slightly out-of-specification.  The power supply is having a hard time putting out enough current in the 3.3 VDC line to run the RAM.  The motherboard chipset is having a problem keeping the RAM timing with 8 GB.  One of your RAM sticks is not reliable at default timings.  Only time and money will fix this stituation.

---

### Post by wboziuk on 2014-11-12
Having used the good 4GB stick for a number of days with zero problems, I've reassembled the computer and am going ahead with one stick for now. For anyone reading this string in the meantime, my testing did establish that the other stick would reliably cause problems both alone and with the good stick, so the "resolution" of the problem has happened .... in the sense that the computer is working properly again.

However, the computer still has the odd behavior of not restarting properly after a shutdown unless the power button is cycled with the power disconnected from the mains. That triggers some sort of relay within the PSU after which power can be restored. This doesn't affect the powered operation of the unit, but it is not normal behavior and it appears it cannot be related to the RAM at all. I attribute it to some fault in the power delivery or protection circuits in the motherboard. The PSU is the less likely culprit because I tested a spare already.

So I am now in a situation where the computer is working, and the easiest way to determine the root cause is to wait for something to fail further. It may take a while, but because the computer is working, I have time :D

Thanks for all your help!

---

