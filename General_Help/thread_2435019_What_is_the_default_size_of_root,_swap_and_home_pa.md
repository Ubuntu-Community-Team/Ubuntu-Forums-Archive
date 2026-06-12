---
title: "What is the default size of root, swap and home partition?"
date: 2020-01-15
forum: General Help
---

### Post by alvinrr on 2020-01-15
What is the default size of root, swap and home partition when I choose Erase disk and install Ubuntu?

---

### Post by deadflowr on 2020-01-15
It'll be whatever the size of the disk is.
And it only creates a single partition for all.

---

### Post by GhX6GZMB on 2020-01-15
AFAIK, there is no default, it's up to you. Your swap partition should be equal to or greater than your RAM size, though.

---

### Post by CelticWarrior on 2020-01-15
> **ml9104 said:**
> Your swap partition should be equal to or greater than your RAM size, though.

... only if you intend to use hibernation, which you shouldn't. reason why it's not enabled by default in most Linux distros and even Windows (recently).

Otherwise, if you have enough RAM changes are you won't even use swap, ever.
And since 17.04 Ubuntu uses swapfile by default instead of the traditional swap partition and its maximum size is determined during installation.

---

### Post by GhX6GZMB on 2020-01-15
> **CelticWarrior said:**
> ... only if you intend to use hibernation, which you shouldn't. 

Why on earth not? Hibernation is a wonderful functionality for laptops et al. Close the lid and you can restore your session days/weeks/months later.
My hibernate works like a marvel. But I do agree that it's not straightforward to set up.

---

### Post by CelticWarrior on 2020-01-15
> **ml9104 said:**
> Why on earth not? Hibernation is a wonderful functionality for laptops et al. Close the lid and you can restore your session days/weeks/months later.
My hibernate works like a marvel. But I do agree that it's not straightforward to set up.

That's **suspension **and has nothing to do with hibernation. Very different beast, do not confuse them! Suspension keeps the RAM alive with the session, no problem with that. Hibernation saves your session to the HDD/SSD and shuts down the whole machine.

---

### Post by GhX6GZMB on 2020-01-15
> **CelticWarrior said:**
> That's **suspension **and has nothing to do with hibernation. Very different beast, do not confuse them! Suspension keeps the RAM alive with the session, no problem with that. Hibernation saves your session to the HDD/SSD and shuts down the whole machine.

Yes. Did you understand the part about "days/weeks/months"? Apparently not  ](*,)

I'm fully aware of the difference between Suspend and Hibernate and have fully functioning hibernation on my laptop.

---

### Post by CelticWarrior on 2020-01-15
> **ml9104 said:**
> Yes. Did you understand the part about "days/weeks/months"? Apparently not  ](*,)

I'm fully aware of the difference between Suspend and Hibernate and have fully functioning hibernation on my laptop.

Good for you... Now please keep that information for yourself, do NOT suggest it here. Many newbies and even not newbies may follow that advice and end up with an unbootable system.

With any modern system, especially if it has a SSD, there's no reason other than laziness to use hibernation. Cold boot is as faster and sometimes even faster than from hibernation. There are too many risks in hibernating that I consider its removal both from Ubuntu and Windows as one of the wisest decisions by the developers in recent years.

---

### Post by GhX6GZMB on 2020-01-15
[COLOR=#000000]> Good for you... Now please keep that information for yourself, do NOT suggest it here. [/COLOR][COLOR=#000000] 
Forums like this are for exchanging information, not for hiding it. The participants are grown-ups who can make their own decisions and learn during the success/pain process when something's just right or perhaps fails.[/COLOR]

[COLOR=#000000]Here's the Hibernation recipe for 19.04 and 19.10:[/COLOR]

[https://ubuntuforums.org/showthread.php?t=2432961](https://ubuntuforums.org/showthread.php?t=2432961)

Hibernation is fantastic for business people who might have umpteen windows open and get called to the airport gate, or into a shortly called meeting, or simply need to move quickly and don't have time to shut down all programs/windows. At home, it's probably useless. But when traveling, just closing the lid and knowing that everything is there when you boot again is great!

---

### Post by CelticWarrior on 2020-01-15
> **ml9104 said:**
> [COLOR=#000000] [/COLOR]Hibernation is fantastic for business people who might have umpteen windows open and get called to the airport gate, or into a shortly called meeting, or simply need to move quickly and don't have time to shut down all programs/windows. At home, it's probably useless. But when traveling, just closing the lid and knowing that everything is there when you boot again is great!

Everything mentioned can be done better, faster, more efficiently and risk-free with suspension which is also the default behavior for closing the lid.

PS - This forum particularly has stict rules about what "information" is shared. Posts containing dangerous commands and other similar info are routinely deleted; discussing cracking, hacking and even white-hat pentesting isn't allowed. Arguably posting recipes for hibernation isn't as bad and those but in the end of the day it's posting a method to enable a feature that for very good reasons have been removed, even in Windows, therefore potentially dangerous.

And this all started because of your incorrect/outdated information about the swap partition...

---

### Post by mc4man on 2020-01-15
> **alvinrr said:**
> What is the default size of root, swap and home partition when I choose Erase disk and install Ubuntu?
As mentioned that method will create a single partition (/) the size of your drive.
The initial install of Ubuntu generally consumes about 7GB.
As of late (18.04+) a swap partition isn't created, a swap file is used instead, generally by default it'll be about 25% of ram though I see significant variations there, on same machine it varies from 1.1 to 2.1 GB 
(myself have never used swap so don't much care.

---

