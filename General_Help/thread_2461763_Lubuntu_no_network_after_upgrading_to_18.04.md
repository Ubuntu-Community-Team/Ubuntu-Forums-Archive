---
title: "Lubuntu: no network after upgrading to 18.04"
date: 2021-05-06
forum: General Help
---

### Post by rg4w on 2021-05-06
One of my machines here is an old Lenovo Q100 nettop, and after an in-place upgrade from Lubuntu 16.04 to 18.04 the Ethernet networking no longer works.

I've done quite a few web searches, but the circumstances described and suggestions for remedying them vary so broadly I'm reluctant to just dive in and try them all.  So coming here for guidance seemed the best bet.

Relevant lshw:
```
*-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 03
                serial: 00:26:18:a7:00:e3
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw latency=0 link=no multicast=yes port=MII speed=1Gbit/s
                resources: irq:16 ioport:ec00(size=256) memory:dffff000-dfffffff memory:dfff8000-dfffbfff memory:febe0000-febfffff
```

Any tips on what I might try to resolve this?  Any other info I can provide to assist your assistance?

This is an old machine and I'm half-tempted to just replace its role with a newer machine I have available here.  But I just hate to landfill working hardware, so I'm hoping we can find a solution.

Thanks in advance for any guidance you can offer.

---

### Post by mikewhatever on 2021-05-06
The output above looks good. The hardware seems to be recognized, but there is no IP. Have you tried to connect with the Network Manager applet?

---

### Post by guiverc on 2021-05-06
Are you aware that *flavors* of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors), so you're asking about a release that only days ago reached it's EOL. 

- [https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/)
- [https://lubuntu.me/bionic-5-released/](https://lubuntu.me/bionic-5-released/)

which mentioned the 3 years and support ending April-2021.

The latest Ubuntu Weekly Newsletter
 - [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses)
(or on this forum see [https://ubuntuforums.org/showthread.php?t=2461582](https://ubuntuforums.org/showthread.php?t=2461582))

Not all *flavors* gave EOL notices, but if you look they had dates provided already. eg. Xubuntu mentioned on [https://xubuntu.org/release/18-04/](https://xubuntu.org/release/18-04/) that EOL was 29-April-2021 (*more accurately than Lubuntu's April-2021*).

FYI:   *As warned on the Lubuntu forum/discourse, I've been moving wiki pages so they aren't reporting as  Lubuntu any longer (search engine searches however using historical pages names may result in errors) however searches performed on wiki.ubuntu.com or help.ubuntu.com will find them. Lubuntu only uses and supports the LXQt desktop now.*

---

### Post by rg4w on 2021-05-07
> **mikewhatever said:**
> The output above looks good. The hardware seems to be recognized, but there is no IP. Have you tried to connect with the Network Manager applet?
Thank you for chiming in. Yes, I have tried setting up new settings in NM for both static (preferred) and DHCP (usually easiest). NM has no problem even recognizing the NIC's MAC, but no go on actually working. :(

---

### Post by rg4w on 2021-05-07
> **guiverc said:**
> Are you aware that *flavors* of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)...
D'oh! I so rarely use that machine that I'd totally forgotten about the shorter EOL for flavors.  Thank you for the reminder.  VERY helpful.

I could convert it to use Ubuntu Server, but is there even a 32-bit version anymore?

I took a quick look around and it seems 32-bit distros are dropping like flies.  This may be a good moment for me to just replace the machine and finally landfill it. I hate to landfill functional hardware, but there's a time when every architecture has a negative ROI for supporting it, and maybe keeping a 32-bit system alive in 2021 isn't the best use of my time.

Would you recommend a well-supported 32-bit distro for such an older machine?  Or would you be inclined to just ditch it and move on to newer HW?

---

### Post by HermanAB on 2021-05-07
You can probably ditch the machine and pick up a better one for $50 at your city landfill.

---

### Post by rg4w on 2021-05-07
> **HermanAB said:**
> You can probably ditch the machine and pick up a better one for $50 at your city landfill.
LOL :)

Replacing it isn't the hard part; I have a new one ready to go.

I was just hoping to keep another electronic device out of a landfill a little while longer.  But 32-bit systems are dinosaurs today, so it's looking increasingly impractical to try.

---

### Post by tea for one on 2021-05-07
> **rg4w said:**
> I was just hoping to keep another electronic device out of a landfill a little while longer.  But 32-bit systems are dinosaurs today, so it's looking increasingly impractical to try.

To save you a trip to the landfill:-

[https://antixlinux.com/antix-19-isos-available/](https://antixlinux.com/antix-19-isos-available/)

---

### Post by guiverc on 2021-05-07
> **rg4w said:**
> Would you recommend a well-supported 32-bit distro for such an older machine?  Or would you be inclined to just ditch it and move on to newer HW?

My IBM Thinkpad t43 still runs Lubuntu 18.04 LTS, and it's not alone...  (*I've often thought of switching to Debian & have written about it.. but I'm lazy & I'm not online with the box so don't see it high priority*)

I still use a few i386 (*what Debian & Ubuntu refer to all x86 but really i686 grade cpus*) laptops as they do what I need them too, and one cheap *amd64* device I purchased with intention of replacing one i386 was soon replaced with the older nicer i386 thinkpad.

At the Lubuntu discourse site we've had a few questions about i386/32-bit so there is discussion there if you look. 

I'll provide [link]("https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466/4") to one of my recent *bionic*/EOL posts where I wrote about i386 where I suggest Debian Buster/10 as I often test Debian releases too. On all but one box I found Debian performed about equal to Lubuntu (*one box alone had Lubuntu performing much better than Debian; but it was the most under-powered thing I have & I rarely used that box in QA-testing*).

[https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466/4](https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466/4)

---

### Post by him610 on 2021-05-07
Debian Buster with Raspberry Pi Desktop. I have this installed on a 12 year old atom powered netbook - works great.
[https://www.raspberrypi.org/software/raspberry-pi-desktop/]("https://www.raspberrypi.org/software/raspberry-pi-desktop/")

---

