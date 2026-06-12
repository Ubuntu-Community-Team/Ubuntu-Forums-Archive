---
title: "Computer shut down when watching HD video on youtube"
date: 2013-01-14
forum: General Help
---

### Post by dodjob on 2013-01-14
Hi there,
I think I need some help there :/
I have mounted a machine for a friend and he has got some odd problems since one year.
He can watch video in HD with vdpau or with the standard player. But the computer will shut down (completely) in 5s after watching a video on youtube. I tried to switch to HTML5 and the result is the same.
I, since the begining of the mess, upgrade to 12.04 and now to 12.10. The problem is still there.
I firstly tried another nvidia drives (I don't know how much but about 5 or 6 differents) and then a different nvidia graphic card with the same result. (was thinking of overheat)
I also tried another Power supply and again.. the problem remained.
I have stressed the 4 procs at 100% for about 3 hours without fail of the system.
I must say this is the extend of my expertise :(
From everything I could find on internet this problem was nearly all the time related to a defective power suply or graphic card. Doesn't seems to be my case.
Has anyone an Idea what could be the problem?
I attach a hardinfo report. I also don't have any idea how to generate a log which could show anything.
The problem is easily replicable: Start a video in youtube, switch it to 1080p and 2 seconds after the system shut himself down.
Gruß,
H.
PS: I don't know If I am in the right thread. Please move it if not!

---

### Post by sanderj on 2013-01-14
Have you run memtest86 (it's in the boot menu)?

Can you try a different card than nvidia?

---

### Post by tgalati4 on 2013-01-14
Put a temperature monitor of the GPU in the panel.  My guess is the graphics card is overheating, locking up the bus.  Many times, the heat sink paste on the graphics card dries out, or the fans quick working (due to dust).  Have you cleaned the machine recently?

It could also be the IO-Bridge (North Bridge or South Bridge) that shuffles data from RAM to the CPU.  They also heat up and fail under stress, especially streaming since some chips also process networking as well.

If you can't find anything in the log files (/var/log), then I would suspect a temperature/load dependent hardware problem.

Since you swapped power supplies, that is probably not the problem.  Take out the graphics card and use the on-board graphics for a while to see the machine stays up for a few days.

---

### Post by dodjob on 2013-01-16
Thanks for the hints!
I will summarise:
- I did run a memcheck86
- I do not own any other card 
- The GPU of the graphic card remain cool
- Machine is completely dust free
- The machine will also stay up a few days if I don't watch HD video on youtube. but If I do.. in any case it will shutdown (the onboard Graphic card has also only a VGA output...
I unfortunately think it's an Hardware realted problem... this sucks :(
Thanks again!

---

