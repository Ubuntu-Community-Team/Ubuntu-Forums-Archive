---
title: "Spectre V2 mitigation: LFENCE not serializing - Is this a virus or an error?"
date: 2018-03-19
forum: General Help
---

### Post by random turnip on 2018-03-19
Hi,

So I was browsing the internet and got a pop-up in my Chromuim browser telling me that the page I was trying to load may be "misleading", so naturally I closed the warning and closed the tab.  However, while closing the tab I saw some scary words in the including "ransomware" which instantly made me a little paranoid.  It was doing updates at the time, but they all seemed to be for programs, not the OS and after watching for a minute it didn't seem to be progressing anyway, so I just rebooted in a blind panic, which now I'm thinking was pretty stupid.

The reboot failed and gave me this error...
[img]https://i.redd.it/brnsszzg7pm01.jpg[/img]

At this point I'm crapping myself, I unplug the router and my desktop's wifi card to try and prevent any further damage if this really is ransomware.

When rebooting the machine again, I tried using the "advanced options" in GRUB and booted from the previous version (kernel?) and it booted without a hitch.  
My mind is telling me that even if something was trying to download, it failed and Chromuim saved my ass, but then my stupidity and panic made me reboot the machine during an update and killed it anyway and it was all just a coincidence.

But I'm still paranoid.  The laptop itself doesn't have anything of importance on it and can be formatted and have the OS reinstalled fresh if there's any point in that?  But I'm still worried that if there was something malicious downloaded and I've just convinced myself everything's ok then I could be putting my main desktop (which was off at the time, and when I booted didn't seem to have any issues), phones and anything else at risk.  The other thing is, even if the not booting problem is caused by an update issue, there's nothing to say there still isn't something nasty on the machine, but it isn't ransomware that I can see as I opening a picture as a test and it opened fine.

I can fix the none-booting issue easily, I'm just wanting to make 100% sure there's no chance of anything nasty and malicious lurking on my network to kill my main PC.

---

### Post by missmoondog on 2018-03-19
i have a topic on here with part of that exact same error. the part that reads "Spectre V2 mitigation: LFENCE not serializing" machine still boots and runs as fine as it can!
[https://ubuntuforums.org/showthread.php?t=2386324&highlight=lfence](https://ubuntuforums.org/showthread.php?t=2386324&highlight=lfence)

never got a reply as of the last time i checked on it.

i'm pretty sure my error is simply because it's and ancient amd athlon xp processor although another ancient machine i have with an amd smpron processor doesn't get that message.

edit:
i lied. i did get a couple replies to that topic but they were actually off topic due to me!

---

### Post by oldos2er on 2018-03-19
The Chromium ransomware and spectre v2 mitigation are two separate things. There's some info about spectre v2 here: [https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown) and [https://ubuntuforums.org/showthread.php?t=2381801](https://ubuntuforums.org/showthread.php?t=2381801) as well.

---

### Post by missmoondog on 2018-03-20
thanks for that first link. short, sweet and explains retpoline very well in the link under the "R" reference.

[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown/TechFAQ#Retpoline](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown/TechFAQ#Retpoline)

---

### Post by Yellow Pasque on 2018-03-20
HAve you tried to boot into a previous kernel?

---

### Post by random turnip on 2018-03-22
Thanks for all of the replies and sorry for sudden silence on my part, was working away from home and couldn't get on the internet much.
> **Temüjin said:**
> HAve you tried to boot into a previous kernel?
Yes I have and it works fine when I do, no signs of any data loss or anything to indicate a security breach that I can see.
> **missmoondog said:**
> thanks for that first link. short, sweet and explains retpoline very well in the link under the "R" reference.

[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown/TechFAQ#Retpoline](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown/TechFAQ#Retpoline)
Thanks, this helps.  It does also say about it not being supported on AMD chips, and I'm pretty sure that's what this laptop has, so could be an obvious cause right there.
> **oldos2er said:**
> The Chromium ransomware and spectre v2 mitigation are two separate things. There's some info about spectre v2 here: [https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown) and [https://ubuntuforums.org/showthread.php?t=2381801](https://ubuntuforums.org/showthread.php?t=2381801) as well.
Thanks, this puts my mind at rest a little.  Had the rebooting issue not happened then I probably wouldn't have thought anything of the message, it was just the two things happening together that made me panic.  And I've seen no signs of anything odd on any other devices on the network either.
> **missmoondog said:**
> i have a topic on here with part of that exact same error. the part that reads "Spectre V2 mitigation: LFENCE not serializing" machine still boots and runs as fine as it can!
[https://ubuntuforums.org/showthread.php?t=2386324&highlight=lfence](https://ubuntuforums.org/showthread.php?t=2386324&highlight=lfence)

never got a reply as of the last time i checked on it.

i'm pretty sure my error is simply because it's and ancient amd athlon xp processor although another ancient machine i have with an amd smpron processor doesn't get that message.

edit:
i lied. i did get a couple replies to that topic but they were actually off topic due to me!
I think I have the same processor (or at least similar)!  So looking more and more like an update happened to crash my machine on the same night as I got the malicious software warning.  My paranoid brain just jumped to the worst conclusion.


Starting to feel like I can turn my main PC on now without being too worried of some nasty malicious software getting onto it.

---

### Post by Yellow Pasque on 2018-03-22
Boot into the previous kernel, and purge/reinstall the problematic kernel.

---

### Post by random turnip on 2018-03-22
> **Temüjin said:**
> Boot into the previous kernel, and purge/reinstall the problematic kernel.

Thanks, will do.


Does anyone have any suggestions for double checking my network is alright?  I'd seen people suggesting that the DNS can get hijacked, I assume I'd check this by getting my IP address and doing a reverse search to check it goes to the correct server (which I've done and it does)?  Is this all I can do?

I can't see any problem with files on any device on the network, but somehow the internet seems slower (could well be paranoia) and got a weird error about network connection to a web page (Twitter) being encrypted on my Nintendo Switch, however it just worked anyway.

---

### Post by missmoondog on 2018-03-22
> **random turnip said:**
> Thanks for all of the replies and sorry for sudden silence on my part, was working away from home and couldn't get on the internet much.

Yes I have and it works fine when I do, no signs of any data loss or anything to indicate a security breach that I can see.

Thanks, this helps.  It does also say about it not being supported on AMD chips, and I'm pretty sure that's what this laptop has, so could be an obvious cause right there.

Thanks, this puts my mind at rest a little.  Had the rebooting issue not happened then I probably wouldn't have thought anything of the message, it was just the two things happening together that made me panic.  And I've seen no signs of anything odd on any other devices on the network either.

I think I have the same processor (or at least similar)!  So looking more and more like an update happened to crash my machine on the same night as I got the malicious software warning.  My paranoid brain just jumped to the worst conclusion.


Starting to feel like I can turn my main PC on now without being too worried of some nasty malicious software getting onto it.

you may have same or similar processor but i haven't had any issues with crashes, so may still be something else.

i'd simply change dns servers and not worry anymore about that. i don't use my junk isp's servers and never have. been using opendns lately.

---

