---
title: "Boot / Harddrive problem."
date: 2007-10-14
forum: General Help
---

### Post by JohnKoziar on 2007-10-14
I have a highly concerning problem!

I've recently used the ubuntu liveCD a couple times to run ubuntu live. The problem I have now is that I cannot boot into Windows, I can only boot from the liveCD.

What happens is that I start my computer without the CD in the drive and it gives me a message saying no disc to boot from, please insert disc and press any key.

The reason it gives me that message seems to be that it does not recognize my harddrive. When in the live session of ubuntu it doesn't see my harddrive (for instance, the partitioner does not think I have a harddrive). When I run the live disc and choose 'boot from first harddrive' from the boot menu, it says boot failed, and then restarts the computer.

And also, when I look at the BIOS settings at startup, in the section where you set order of precedence for booting between CD, floppy disc, and harddrive (that being the natural order) it says that No Device [is] Detected for both floppy disc (I don't have a floppy drive) and for my harddrive!

It seems like an obvious solution would be to jiggle the cables, but I have never opened my computer. I do not mean that I couldn't do so, just that it's strange that a cable could have come loose.

I would try using the Windows boot CD to see if that helps, but it is at my past residence, a ways away. Ditto screwdrivers to open my computer (though I could buy one of those easily). I will be able to get a hold of the Windows boot CD in a couple of weeks.

Any help you can provide is greatly appreciated.

---

### Post by JohnKoziar on 2007-10-14
The error I get when trying to boot from the harddrive from the ubuntu boot menu is:

Booting from local disk.
    isolinux: Disk Error 02, AX = 0201, drive 80
Boot failed: press a key to retry

Also, it might be pertinent to note that I was unable to boot from the liveCD until I appended "# defoptions= irqpoll" to the, uh, is it called a boot string? The line of text specifying boot options. What you get when you highlight "Start or install ubuntu" and then press F6.

---

### Post by JohnKoziar on 2007-10-15
Bump.

I feel like there is some simple solution that I am missing.

---

### Post by HelixAgent on 2007-10-15
Well that is not certainly caused by Ubuntu because you did not installed it in the first place, and the Live CD as I understand charges everything to memory so that shouldn't be the thing messing with your HDD. I beleive its easier to extract your HDD and connect it to another computer (with technical help!) and see if it works, if not, well you pretty much need another HDD (or at least that is the way I see it), and if it does works try checking the cables sometimes the cables just stop working for time wasting or internal damage, that happened to me once and it turned out to be the cable!

Good luck!,
Helix.

---

### Post by JohnKoziar on 2007-10-15
Thank you, and I think you are right!

---

### Post by dabl on 2007-10-15
> **JohnKoziar said:**
> 

And also, when I look at the BIOS settings at startup, in the section where you set order of precedence for booting between CD, floppy disc, and harddrive (that being the natural order) it says that No Device [is] Detected for both floppy disc (I don't have a floppy drive) and for my harddrive!



If I understand this correctly, you're saying that BIOS does not see a hard drive in the boot sequence?  That's a bad thing!  Check both power cable and data cable -- is that hard drive actually running? Booting a CD would not cause this, as far as I can imagine -- only a disconnection or failure of the hard drive or it's power would cause this.  :(

---

### Post by JohnKoziar on 2007-10-15
You may have noticed that I tried to change the thread title to "Not Unsolved." This is because for a moment I got hopeful. You see, suddenly, after ubuntu was running live for several hours, my harddrive was suddenly spotted. It showed up in the File Manager and then in the partitioner, which is to say in the same places it didn't show up before.

Gleefully, I booted my system in Windows, successfully. The first thing I did was to log on here to write a post saying that my harddrive was found, but that the problem will probably recur because its cause hadn't been found.

Well guess what, I was right. After I had changed the subject of my first post and halfway through writing my success post, I got a BLUE SCREEN OF DEATH. I had to restart my system and guess what -- no harddrive.

The moral is don't get your hopes up. It seems more than ever now that it is a loose cable. I'll get a screwdriver soon! Until then, I'm stuck in this crappy live session with only occasional and short-lived access to my harddrive and with no CD drive that I can use.

---

