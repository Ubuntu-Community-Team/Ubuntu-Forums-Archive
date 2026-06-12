---
title: "Battery discharging when turn off."
date: 2012-10-18
forum: General Help
---

### Post by jingaling on 2012-10-18
Hey guys,

This is more of a question that a problem I need fixing really. I have a HP Envy Sleekbook 6 laptop running 12.04 stock. When I turn it off the battery continues to discharge. I know this is definitely the case as I have fully charged my laptop, shut it down for a couple of days then come back to completely flat battery.

I am assuming that this is an issue with the kernel rather than something on the OS as such? Is anyone else having this same issue (I can't find anything else in the forums) and will this be fixed in the Quantal release today?

Thanks guys,

Kev

---

### Post by Insomn1a on 2012-10-18
> **jingaling said:**
> Hey guys,

This is more of a question that a problem I need fixing really. I have a HP Envy Sleekbook 6 laptop running 12.04 stock. When I turn it off the battery continues to discharge. I know this is definitely the case as I have fully charged my laptop, shut it down for a couple of days then come back to completely flat battery.

I am assuming that this is an issue with the kernel rather than something on the OS as such? Is anyone else having this same issue (I can't find anything else in the forums) and will this be fixed in the Quantal release today?

Thanks guys,

Kev

how long have you had this laptop?

It almost sounds like its just a bad battery.

---

### Post by jingaling on 2012-10-18
It's brand new - maybe 2 months.

You know, that hadn't crossed my mind - what an idiot! I'll see how it goes with 12.10 in case it is the Kernel pulling out some kind of charge from it. With the known issues with the battery life and Ubuntu I just assumed it would be the kernel.

Thanks for the quick reply.

---

### Post by Insomn1a on 2012-10-18
> **jingaling said:**
> It's brand new - maybe 2 months.

You know, that hadn't crossed my mind - what an idiot! I'll see how it goes with 12.10 in case it is the Kernel pulling out some kind of charge from it. With the known issues with the battery life and Ubuntu I just assumed it would be the kernel.

Thanks for the quick reply.

If the laptop is completely off, then the operating system or kernel has nothing to do with the discharge, what i would try is completely charging the battery, then shutting the laptop off and pulling the battery out, then after a while putting it back in and seeing if there is any discharge.

---

### Post by jingaling on 2012-10-18
I can't with it being a 'Sleekbook' it's a lithium battery that's inside the chassis.

I'll get on to HP about it.

---

### Post by Insomn1a on 2012-10-18
> **jingaling said:**
> I can't with it being a 'Sleekbook' it's a lithium battery that's inside the chassis.

I'll get on to HP about it.

cool beans

---

### Post by Giveingitago on 2012-12-04
Hi [jingaling]("http://ubuntuforums.org/member.php?u=1105191"),
I have a HP ENVY 6 Sleekbook ( 1 month old) and have just noticed the same characteristic. Its fully charged, turn it off, disconnect it form the charger, leave it 2 days and its only ~ 60% charged when I turn it back on without mains charger connected. Will investigate further and re- post if I find anything.

---

### Post by Giveingitago on 2012-12-10
Hi,
Confirmed.
I have a HP ENVY 6 1006sa running Ubuntu 12.10. Fully charged, unplugged Mains adaptor powered down. 48hrs later re-powered charge now only 65% ! 12.10 has a really decent power diagnostics, click on the battery icon:

[http://www.divnut.com/HP_ENVY6_1006sa/HP_ENVY_6_48hr_discharge_2012-12-08.png](http://www.divnut.com/HP_ENVY6_1006sa/HP_ENVY_6_48hr_discharge_2012-12-08.png)

The gradient looks OK, so nothing wrong with the battery. Left a further 48 hrs and the Sleekbook would not start on battery alone.

[http://www.divnut.com/Ubuntu/HP_ENVY_6_96hr_discharge_2012-12-10.png](http://www.divnut.com/Ubuntu/HP_ENVY_6_96hr_discharge_2012-12-10.png)

I've logged a support request with HP.

---

### Post by jingaling on 2012-12-10
Thanks Giveingitago,

Let me know how you get on with HP support. I don't really want to send my laptop off again but I will if I have too.

Kev

---

### Post by Giveingitago on 2012-12-12
I logged a support case with the HP Commercial Support by mistake which was rejected, should have logged with Consumer support. Before I ventured there I thought one last test was in order as I was getting ready to return my Sleekbook to PCworld when I thought can I demonstrate the same fault with Windows 7 ? (e.g. when returning the Sleekbook to its original build). I'm duel booting, so booted into Win 7, fully charged & shut down. 24 hours later rebooted into win 7 the battery discharge was only 4% !! Still more than expected but now significantly less than with Ubuntu shutting down the Sleekbook. Just repeated the same test but booting into Ubuntu and the battery charge status was 96% confirming the Win 7 measurement. 

So a work around is following an Ubuntu session is to reboot into Win 7 and then shut down.

I'll log a Bug in Launch Pad.

I'm going to triple boot with other Unbuntu releases and variants   to see if its a new problem with latest Ubuntu. I noted that in a Win 7 session the HP power control tools were quite sophisticated. Could be a new type of battery interface issue or an actual battery issue. I've been researching Lithium ion batteries, the expected discharge is 5 to 10 % per month and this is mainly due to the power monitoring circuit in the battery. So even the 4% per day with Win 7 still seems a much larger than expected discharge.

---

### Post by Giveingitago on 2013-01-11
Now logged as a Kernel bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1098697](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1098697)

---

### Post by jingaling on 2013-01-11
Thanks for all the info Givingitago.

Looks like we've found the root cause of the problem. I don't dual boot so I was unable to test with Windows 7 without replacing the upgraded SSD that I have with the original HDD (which still has the original image on it).

Thanks for the info, I'll keep an eye on that bug.

---

### Post by mark bower on 2013-10-09
Maybe my final blast on laptop battery drain that may be helpful to others: 1) a summary of data from tests, and 2) a link to a method that worked for me. 

Again, my system is an HP Pavillion g6, Ubuntu 12.04 LTS with Gnome Classic overlay. The BIOS on this computer does not have power options to turn things off versus what other posters have reported whereby their BIOSs have power turn off options.

At the beginning of each test the battery was charged to 100% capacity.  Booting was always done with connection to AC; immediately after boot I looked at the battery capacity via battery icon (in top tray)>battery>Laptop Battery>scroll to read percent capacity remaining.

The conclusions I draw from my tests are the following: 1) the battery alone has a very low self discharge rate, 2) the computer in "WOL g" mode causes a very high rate of battery discharge and 3) "WOL d" mode results in about 2% battery discharge per day. 2% is not good in my opinion; .5% would be much better for a person who leaves the computer unattended for a month or so at a time.

I also did a hardware only test (not included here) which seemed to indicate that with no OS on board, there was a very low rate of discharge. However, I did not control the test well so this is only an assumption, ie, if no operating system on board the battery only discharges at its stand alone self discharge rate. And if this is true, it "says" again that "WOL d" does not eliminate some other unknown discharge action.  Following are the test results:

[table="width: 500"]
[tr]
	[td]**Test**[/td]
	[td]**# of test days**[/td]
	[td]**% charge remaining**[/td]
	[td]**% loss/day average**[/td]
[/tr]
[tr]
	[td]Batt charged,removed for dys, then reinstalled to test[/td]
	[td]7[/td]
	[td]100[/td]
	[td]0[/td]
[/tr]
[tr]
	[td]WOL g --> WOL d[/td]
	[td]5[/td]
	[td]90.2[/td]
	[td]1.96[/td]
[/tr]
[tr]
	[td]repeat above longer period[/td]
	[td]10[/td]
	[td]80.0[/td]
	[td]2.0[/td]
[/tr]
[tr]
	[td]WOL d --> WOL g[/td]
	[td]6[/td]
	[td]0.0[/td]
	[td]>16.6[/td]
[/tr]
[tr]
	[td]repeat above shorter period[/td]
	[td]1[/td]
	[td]82.3[/td]
	[td]17.7[/td]
[/tr]
[tr]
	[td]WOL g --> WOL d[/td]
	[td]6[/td]
	[td]88.1[/td]
	[td]1.98[/td]
[/tr]
[/table]


The following link by Hectic Geek is the key to what worked for me to reduce the daily discharge rate to 2%.  Essentially he describes how to copy the "disable-wol" file to /etc/pm/power.d and specifies the line in it to modify "WOL g" to "WOL d".* Then for each boot, "WOL d" is active.  If anyone has problems with the link, I can repeat the essential code in another response to this thread.

[http://www.hecticgeek.com/2012/09/disabling-wake-on-lan-in-ubuntu-might-save-a-tiny-bit-of-power-on-your-laptop/](http://www.hecticgeek.com/2012/09/disabling-wake-on-lan-in-ubuntu-might-save-a-tiny-bit-of-power-on-your-laptop/)

---

