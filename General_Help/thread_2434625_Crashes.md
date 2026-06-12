---
title: "Crashes?"
date: 2020-01-08
forum: General Help
---

### Post by skyesharica on 2020-01-08
*Ubuntu 18.04.3 LTS - 64-bit.*
Gah ... it's the new gadget fit word, LOL. I'm writing a book and losing my stability. [IMG]https://ubuntuforums.org/images/smilies/confused.gif[/IMG]

For the first time in six years I had some freezing with Ubuntu, so I  upgraded to the latest operating system - I did the install perfectly.

Now I have a problem where I suddenly log out ... the screen goes dark,  and then comes back as a log in screen ... and when I log in, of course,  all the stuff I was doing is gone.

---

### Post by Autodave on 2020-01-08
That sounds more like a hardware problem to me: either power supply failure or RAM failure.  Can you give us some info on your machine please?

---

### Post by skyesharica on 2020-01-09
Thanks Autodave. ):P I've had this tower desktop for about 4-5 years, and it was about $1K from a shop. It's been a great PC. But those strange freezes started about four months ago. I thought the recent OS clean install would fix it. But I've had this dark screen/log out thing about 10 times now. I don't know of any hardware faults yet, other than what I've told you. I thought it might have been the hardware four months ago, because I've never had freezes/crashes from Ubuntu. These are my device details.:

_Memory_: 3.8 GiB
_Processor_: Intel® Core™ i3-4170 CPU @ 3.70GHz × 4 
_Graphics_: NVA8
_GNOME_: 3.28.2
_Disk_: 983.4 GB

Do you think I should get the machine serviced - the RAM checked or changed? Very costly to me - I'm a struggling author - not published.

---

### Post by CatKiller on 2020-01-09
> **skyesharica said:**
> _Graphics_: NVA8
It's interesting that you've written it like that. Does that mean you're using the open source nouveau driver rather than the proprietary driver? The 340 branch, which is in the repositories, should still support that ~2010 card.

An issue with the graphics seems like a likely culprit. If switching between the nouveau and nvidia drivers doesn't help, you also have a graphics device integrated into your processor. You can also try using that instead at no additional cost.

For testing your memory you should have a memtest boot option. That runs a comprehensive series of test patterns for the RAM. If the RAM is OK it should be able to run indefinitely (overnight is generally a good proxy) without errors.

Since the computer is long in the tooth, cleaning out the dust from all the vents and heatsinks with compressed air is good maintenance. Components overheating can cause issues.

---

### Post by TheFu on 2020-01-09
Dude, look at the log files.  They are in /var/log/ .... look for warnings and errors.

No need to guess what the issue might be. The system logs should tell.

---

### Post by Quarkrad on 2020-01-09
It might be worth (after powering down) taking the side panel off your machine and giving everything an 'unplug' and 'plug-in'.  Sometimes you find the inside of your pc is covered in dust and needs a good clean (hoover job).  If you do this make sure you touch the power supply to ground yourself.  I've had a number of suspect hardware/software? potential faults over the years that has been solved by simply taking things out (e.g. RAM) and putting them back in again. HR in connectors can cause all sorts of issues.

---

### Post by skyesharica on 2020-01-09
> **CatKiller said:**
> It's interesting that you've written it like that. Does that mean you're using the open source nouveau driver rather than the proprietary driver? The 340 branch, which is in the repositories, should still support that ~2010 card. An issue with the graphics seems like a likely culprit. If switching  between the nouveau and nvidia drivers doesn't help, you also have a  graphics device integrated into your processor. You can also try using  that instead at no additional cost.

Sorry, I am not an IT expert like that - no idea what you're talking about.

> **CatKiller said:**
> For testing your memory you should have a memtest boot option. That runs a comprehensive series of test patterns for the RAM. If the RAM is OK it should be able to run indefinitely (overnight is generally a good proxy) without errors.

Again, I do not know the boot stuff well - I would feel very insecure. Can you give directions please?

> **CatKiller said:**
> Since the computer is long in the tooth, cleaning out the dust from all the vents and heatsinks with compressed air is good maintenance. Components overheating can cause issues.

Thankyou very much for that. I will ask for the prices of an all round inspection and service. Do you have a suggestion to save money? I'm writing a book - not enjoying the published booty yet, LOL. :guitar:

---

### Post by skyesharica on 2020-01-09
> **TheFu said:**
> No need to guess what the issue might be. The system logs should tell.

Thanks friend. I finally found those log files ... dummy here ... but there's so many. Can you give me a further idea which folder or file to open? :rolleyes:

---

### Post by skyesharica on 2020-01-09
> **Quarkrad said:**
> It might be worth (after powering down) taking the side panel off your machine and giving everything an 'unplug' and 'plug-in'.  Sometimes you find the inside of your pc is covered in dust and needs a good clean (hoover job).  If you do this make sure you touch the power supply to ground yourself.  I've had a number of suspect hardware/software? potential faults over the years that has been solved by simply taking things out (e.g. RAM) and putting them back in again.

Thanks. I'll look for a cheap service. Any ideas about how to save money as I am really struggling terribly?  :-({|=

> **Quarkrad said:**
> HR in connectors can cause all sorts of issues.

I've googled 'HR' for ages but can't find a technical explanation for the word. Do you mean Human Resources?

---

### Post by TheFu on 2020-01-09
> **skyesharica said:**
> Thanks friend. I finally found those log files ... dummy here ... but there's so many. Can you give me a further idea which folder or file to open? :rolleyes:

I'd use **egrep**.  That is a search tool.  Very useful for looking inside text files.  It is basic Unix knowledge.
You could also use **journalctl** which has a search capability, but I'm not up on systemd stuff.

---

### Post by CatKiller on 2020-01-09
> **skyesharica said:**
> Sorry, I am not an IT expert like that - no idea what you're talking about. 

There are two types of graphics drivers available for Nvidia devices: an open source one called nouveau, and a closed source proprietary driver from Nvidia themselves. The nouveau driver is reverse engineered, so doesn't have as many features, and the nvidia driver is a black box that does its own thing. You can switch between them easily enough, but I don't know exactly what the tool would be called in your desktop environment; it will be something like "Additional Drivers." 

> Again, I do not know the boot stuff well - I would feel very insecure. Can you give directions please? 

Your boot process is handled by a utility called Grub. It has a menu that you can invoke by either holding Shift or pressing Escape when you turn the computer on. One of the options on that menu should be memtest, which will test your memory. Leave it to run overnight to see if it finds any errors. 

>  Thankyou very much for that. I will ask for the prices of an all round inspection and service. Do you have a suggestion to save money?

The suggestion to save money is to use compressed air to blow out any dust yourself.

None of other things I've suggested will cost any money at all. Just some learning about your machine, which is a transferable skill.

---

### Post by Quarkrad on 2020-01-10
I would not suggest you pay for somebody to take the side panel off and unplug and re plug - all of us are suggesting things that do not cost you any money in the first instance.  Don't be afraid of what is inside the case.  Take the left hand side panel off (as you look at the pc). Normally there are two screws holding it on at the rear of the panel and take a close up picture of the inside with your phone, and post the picture(s) on this site.  We can then advise what to unplug and re-plug.  It is like taking lego bricks apart and re-joining them - certainly something you can do yourself.  (If you decide to do this, before you take the side panel off there might be a small rocker switch above or below the mains lead that powers your pc. Turn that off to disconnect the power going to your pc and then back on again when you put the side panel back on).

---

### Post by TheFu on 2020-01-10
> **Quarkrad said:**
> I would not suggest you pay for somebody to take the side panel off and unplug and re plug - all of us are suggesting things that do not cost you any money in the first instance.  Don't be afraid of what is inside the case.  Take the left hand side panel off (as you look at the pc). Normally there are two screws holding it on at the rear of the panel and take a close up picture of the inside with your phone, and post the picture(s) on this site.  We can then advise what to unplug and re-plug.  It is like taking lego bricks apart and re-joining them - certainly something you can do yourself.  (If you decide to do this, before you take the side panel off there might be a small rocker switch above or below the mains lead that powers your pc. Turn that off to disconnect the power going to your pc and then back on again when you put the side panel back on).

First, turn off the PC and **pull the plug** from the wall before starting.  When you are more comfortable, the small rocker power switch on the PSU is all that really needs to be touched. Better safe today.

Putting together a PC is easier than legos.  Fewer parts and the parts are key'ed.  Almost uniquely key'ed so they cannot be put in the wrong place.  It has been this way 15+ yrs. In the early 1990s, hooking up a PC didn't have key'd parts and it was possible to fry parts by plugging in the wrong PSU cables to the wrong places.

The motherboard manual should spell out any important things, like where to put RAM if there are 4 slots (every other slot, but the first one matters). Usually, just drop RAM into every other slot. As you push it in firm, but gently, it will snap the side holders in place.

And almost always, the GPU goes in the longest PCIe slot closest to the CPU/PSU/top.   

SATA ports might have different colors to help denote SATA3 vs SATA2.  Most of the time, it doesn't matter, unless the motherboard supports NVMe storage, which might disable 2 SATA if used.

Don't touch the CPU+Cooler.  The way those are mounted means there cannot be any dust in the connections.

Usually the SATA ports and/or PCIe cards are the only things where re-seating helps.  The other connections are so good and "click" into place to prevent issues.  Getting the dust out of the case can prevent short circuits on the different components.

There has to be 500+ videos about this stuff on youtube.

Did you check the logs yet?

---

