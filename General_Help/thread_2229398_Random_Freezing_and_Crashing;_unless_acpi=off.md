---
title: "Random Freezing and Crashing; unless acpi=off"
date: 2014-06-12
forum: General Help
---

### Post by UnusedUserNameHere on 2014-06-12
Hello,

I tend to ramble a bit, but I will try to be concise. I will appreciate any feedback or suggestions.

I originally had Ubuntu 12.04 installed, and would notice that occasionally the PC would completely lock up. First, all of Ubuntu would become unresponsive except the mouse pointer would still move around. After about a minute, the mouse pointer would stop. Then after a few minutes, the PC would reboot itself - or I'd have to do it manually. This occurred enough to be annoying, but not frequently enough for me to investigate. Sometimes I would leave Ubuntu running overnight, and wake up to find my PC booted into Windows (so I know it restarted itself at some point).

When I tried to upgrade to Ubuntu 14.04; I was surprised to see the same issue, but even worse. I could not even get through the install. I had about 8 attempts on the install, but it seems as soon as there was heavy CPU or disk usage (not sure which, or if it was just coincidence), the lock up would occur. Sometimes I would see text "Machine Check" error codes (I apologize I forgot what they were). The code instructed me to run a program to decode the error once it restarted, but the program wasn't available. When I Googled the codes at the time, I remember that it showed this was an error given directly from the CPU and usually means bad hardware - it was not a software error.

I then tried booting the install with acpi=off, and I had no issues at all. Once 14.04 was installed, now I have to continue to run it with acpi=off for stability. I tried following instructions to further diagnose the issue, but they all seem to assume that acpi=ht will work, then you diagnose from there. For me, I don't even get stability with acpi=ht. Only acpi=off will let Ubuntu run long-term. I also disabled C1E in Bios and still acpi=off is the only way to run stable.

If I run Windows, I have no issues at all. I even stress the GPUs and CPU very hard in Windows without any issue. I have had Windows run for weeks at a time without needing a reboot. As far as I know, Windows is using ACPI. It is only in Ubuntu (haven't tried other Linux distros) that it will not run for more than 10 minutes unless booted with acpi=off. The time it takes to freeze varies. If I type my password as soon as the login screen comes up, then try to load an application as soon as the desktop comes up, I can guarentee it will crash right away. If I take it slow, it will crash, just not right away. It may also be worth noting that when the crash occurs, it is incremental. One application will freeze completely, while others will continue to work. Then another app will freeze. Then the entire interface except the mouse will freeze. Then eventually the mouse will freeze. Then the PC will reboot. This all occurs within 5 minutes of the first symptom. I never get any error messages. I was wondering if this sounds like one core/thread crashed, then it eventually cascades to all of them.

Also, I've run memtest86+ at length without finding any memory issues.

Obviously the easy answer is keep booting with acpi=off, if that's the only way to get Ubuntu to run stable.
However, am I losing anything by doing this? I'm not too concerned about any of the power saving, but it looks like I lose Hyper Threading? Is this going to affect performance? Typically I only use Ubuntu for programming. Is it worth continuing to investigate? What should I check next?

My setup:

Intel Core i7-950, clocked @ 3.8ghz
Asus P6X58D-E motherboard
6 GB RAM
2x MSI N780 TF 3GD5/OC sli
Adaptec 6805E raid card

---

### Post by Bucky Ball on 2014-06-13
*Thread moved to **General Help**.*

Run with acpi=off. No big deal. You finally found the fix.

---

