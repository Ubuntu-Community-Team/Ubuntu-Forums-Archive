---
title: "Computer being insanely slow and other issues"
date: 2018-04-11
forum: General Help
---

### Post by melody5697 on 2018-04-11
I think something might be terribly wrong with my computer. There have actually been problems ever since I installed Ubuntu 17.10 several months ago, but it's getting worse. My computer would get really slow and eventually freeze after I had it in sleep mode for a while, which I figured was because my swap partition is too small. (That's the last time I let the installer do the partitioning for me to save time.) I almost ruined my hard drive a while back because I didn't know that I had any option when my computer froze other than holding down the power button. The sound is way too quiet when I'm using Ubuntu (even though it's just fine when I use Windows), which is a problem when I'm trying to watch a video or listen to music. There's also a problem where my computer will freeze briefly when I'm typing, and when it unfreezes, I see that one of the characters I typed is repeated over and over and over. But now I'm having new problems. Sometimes it takes forever for web pages to load, which I know isn't a problem with my wifi because I don't have any problems on my Roku, my phone, or my tablet. And now it sometimes gets super slow when my computer HASN'T been in sleep mode since the last time I had to reboot because my computer got too slow. Last night, it got insanely slow when all I had open was eight tabs in Opera. Fortunately I didn't have to reboot. Now I'm worried that I might have a virus. (I have no idea how I would've gotten one. I got one in Linux Mint on the laptop my grandparents bought me when I graduated from high school, but that's because I downloaded software from some obscure website that someone had probably hacked.) I tried to follow these instructions:
[https://askubuntu.com/questions/250290/how-do-i-scan-for-viruses-with-clamav](https://askubuntu.com/questions/250290/how-do-i-scan-for-viruses-with-clamav)
It took almost two hours for the software to install. When I tried to update the virus definitions, it told me that some process was keeping me from doing that. (It didn't tell me what the process was.) So I was like, okay, let's just go ahead and do the scan. After a few hours, it still wasn't done, so I decided to go to bed and come back later. 13 hours after I'd started the scan, it still wasn't done. When I clicked on this tab so I could start typing this post, my computer froze and I had to reboot. Shortly after booting into Ubuntu, I got a message telling me that Ubuntu had experienced an internal error. I don't know if it's possible for me to show you the details (since they're way too long to type myself). If you need those details, just tell me how to show them to you. What's wrong with my computer? Maybe I should just back up all my files and reinstall.

---

### Post by kerry_s on 2018-04-11
backup anyway before it's to late.

what are your specs?
i doubt you have virus, that's a uncommon thing in linux. you'd have to do some dumb things to get a virus/malware.

---

### Post by melody5697 on 2018-04-11
> **kerry_s said:**
> backup anyway before it's to late.

what are your specs?
i doubt you have virus, that's a uncommon thing in linux. you'd have to do some dumb things to get a virus/malware.
Here's the Amazon listing for the computer, since the specs are on there: [https://www.amazon.com/gp/product/B01M7VW4M9/ref=oh_aui_detailpage_o08_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B01M7VW4M9/ref=oh_aui_detailpage_o08_s00?ie=UTF8&psc=1)
Of course, I have Ubuntu 17.10 installed alongside Windows 10. Please don't misunderstand and think I'm advertising the computer. One time someone got really upset with me for telling them the specs of a computer by showing them the Amazon listing because they thought that meant I was really just trying to get people to buy the computer. (Which is stupid, since talking about problems I'm having with a computer is a very bad way to try to convince people to buy it.) I'm just providing a web page that has the specs.

---

### Post by kerry_s on 2018-04-11
specs look fine enough to run any linux version.
swap shouldn't matter you have enough ram.
i don't think this a hardware issue.

---

### Post by melody5697 on 2018-04-11
> **kerry_s said:**
> specs look fine enough to run any linux version.
swap shouldn't matter you have enough ram.
i don't think this a hardware issue.
Uh, did I say anything to imply that I thought this was a hardware issue?

---

### Post by kerry_s on 2018-04-11
sorry, multi-tasking have other things on my mind, never finished writing it out.

i meant say so we can concentrate on software. using the system monitor or top or htop. try to narrow down what's causing the freeze.
maybe an app is getting stuck & running your cpu at 100% or your ram is being filled by some process.
when it happens do you feel it slowing down or the fans kick on like it's working hard, any signs? to let you know when to check the monitors.
i don't really think you should have 1 open till it happens, cause then it's to late it freezes right?

---

### Post by melody5697 on 2018-04-12
Yes, it usually slows down before freezing. I'll check the system monitor next time. But I'm also worried about the internal error. Maybe it's connected.

---

### Post by kerry_s on 2018-04-12
> **melody5697 said:**
> Yes, it usually slows down before freezing. I'll check the system monitor next time. But I'm also worried about the internal error. Maybe it's connected.

that's most likely from the forced power off. like data corruption, ext4 filesystem is journaled so it should handle recovery from that just fine.
unless you're still seeing the error?

---

### Post by melody5697 on 2018-04-12
Actually, I restarted by holding down alt and prt sc and typing RSEIUB. So no, that's not what caused the internal error.

---

### Post by logix2 on 2018-04-12
This to me sounds like a memory leak. Take a look at the used memory column in System Monitor when this happens, and see if an app (or system component) uses a large amount of memory that's continually increasing.

---

### Post by kerry_s on 2018-04-12
> **melody5697 said:**
> Actually, I restarted by holding down alt and prt sc and typing RSEIUB. So no, that's not what caused the internal error.

the Reboot Even If System Utterly Broken (REISUB) is still a forced power down.

---

### Post by melody5697 on 2018-04-12
> **kerry_s said:**
> the Reboot Even If System Utterly Broken (REISUB) is still a forced power down.
So the person who told me that I should do that instead of holding down the power button was wrong? It's not really any better?

---

### Post by melody5697 on 2018-04-12
> **logix2 said:**
> This to me sounds like a memory leak. Take a look at the used memory column in System Monitor when this happens, and see if an app (or system component) uses a large amount of memory that's continually increasing.
What's a memory leak?

---

### Post by kerry_s on 2018-04-12
> **melody5697 said:**
> So the person who told me that I should do that instead of holding down the power button was wrong? It's not really any better?

it depends on how badly the system is locked up, use it if you can, no harm in trying.

> What's a memory leak?


it's when a app/process consumes the memory/ram leaving your system in a starve state, blocking access for other apps to use memory/ram.

---

### Post by melody5697 on 2018-04-12
My computer is also going into airplane mode on its own. I saw that it did that a few minutes ago. I turned it off, but it didn't reconnect to the wifi. I tried selecting my wifi network, but nothing happened. It went into airplane mode again. When I turned off airplane mode, it said the wifi was off, and I had to try to turn it back on a few times before it would work. I'm just gonna install Linux Mint. I always have way more problems with Ubuntu than with Mint. I switched to Ubuntu because my computer has a touch screen and I thought it would be nice to have a desktop environment that's more suitable for touch screens, but I rarely use the touch screen anyway. It's just not worth it.

---

### Post by kerry_s on 2018-04-12
i feel you everyone has that special thing the just like about a distro.

i'm using solus budgie, but i keep running into bug after bug, just to much broken to be my daily driver. i'm downloading elementary os, which is my favorite.
most of the other *ubuntu's had issues here & there as well for me. i can overlook a few things, but usability is not one.

good luck

---

