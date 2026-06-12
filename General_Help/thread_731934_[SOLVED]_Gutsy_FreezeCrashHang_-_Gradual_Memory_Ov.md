---
title: "[SOLVED] Gutsy Freeze/Crash/Hang - Gradual Memory Overload"
date: 2008-03-22
forum: General Help
---

### Post by ShadowMKII on 2008-03-22
I am having a problem where my Gutsy decides that it wants to freeze.

Me, being a Windows user in the past, went to the System Monitor as the first course of action to try and solve this problem.

Since I have to hard reboot everytime this problem occurs, I did not want to do it again. My computer starts to freeze up, slow down, the mouse is jittery and partly unresponsive, then all of the windows fail to work. This is apparently a problem that has been happening to some other people on the forum as well, but I cannot seem to find the thread right now.

Anyhow, back to where I was. I timed the freezing intervals to about half an hour each. I then thought that it was odd for timed freezing unless this distribution of Linux somehow contracted a virus. Nonetheless, I went to the System Monitor at about the 25 minute mark (by chance) and found something even more odd than "timed freezing." What was strange was that one of my cores on my AMD Athlon X2 64-bit was at about 72% while the other was at about 5%. This, however is the strangest part - my memory was at about 85% usage.

I restarted my computer the regular way because my computer had not yet frozen and then went to the System Monitor after the fresh restart. (By the way, restarting X does not solve this problem entirely). I then watched the memory slowly build up in usage from my regular 256MB standing all the way to 1.9GB, since I have about 2.0GB of RAM. At the 89.8% usage mark, my computer was officially frozen and I barely made it out "alive" to do a regular restart instead of a hard reboot.

In other words, my computer's RAM was being stuffed with some kind of extra information that caused it to eventually fill up and cause my computer to crash. Just for additional info; my Ubuntu's swap goes from 0 to 100% in about 3 seconds when my memory usage reaches about 80%. As I am typing, this stage is happening right now and my computer will freeze in about 5 minutes.

You could say I have this down to an art - and that is only after having this happen 6 times or so.

I hope this information helps because I do not want to have to use some other non-Linux computer to get something done that takes more than 25 minutes!

---

### Post by ShadowMKII on 2008-03-25
Does anyone know anything about this? Is this a common problem? Does anyone else have this? Is this problem only Gutsy specific, or is this a virus?

---

### Post by ShadowMKII on 2008-03-25
Hello to whoever has been watching this thread. It seems I have solved my problem.

I am going to admit that was in somewhat of a panic and was not thinking logically about what to do when posed with such a problem. As I had never seen 2GB of memory taken up in 20 minutes on a Windows machine, which is something that I started using back in 1995, I was in a panic. I have now isolated the problem, or so I think.

After doing some research and looking at possible problems, I found that there could be something called a "memory leak" on my Ubuntu. I looked around for possible solutions on threads here in there, typing in search keywords such as; "ubuntu memory virus," "memory overload" and other such things along those lines. I had heard of memory leaks in the past, but I never even thought about the term at the time nor knew what entirely it meant.

I searched some more to find problems that were specific to AMD64 bit versions of Ubuntu and AMD64 bit computers. This was that computers running the 64 bit Ubuntu or that have a 64 bit processor would be overloaded somehow. I also heard of Nvidia driver problems that caused memory leaks. If you look at my signature, you can see that I have both an AMD64 bit processor and an Nvidia video card - one of the newer ones at that (which could potentially cause more problems).

I then heard about other problems such as Xorg being buggy as well as one other application/process that I cannot quite remember right now. Then I came to the holy grail that would help me solve my problems as of ten minutes ago. I went to the "Processes" tab of my System Monitor, which I would always have open so I could know when to restart my computer before it froze, and found the "trackerd" process taking up over 900MB of RAM/memory. I knew this was the problem... and the amount of memory it was taking up was so absurd and ridiculous that I knew it had to be it.

I searched for a solution on a single thread much to my delight and found that if deleted - I did this - or disabled, the memory usage would fall back into normal ranges after one's computer was restarted. I also found out that this was a bug.

I deleted "Tracker," restarted my computer and then have had no problems ever since twenty minutes ago.

Obviously this could be far too early to say that this is in fact solved, but it is something that I am very happy to have done. Now I am back to my open source computer that I appreciate even through my inability to understand Linux through and through, combined with its minor issues. I must say, I am quite ecstatic.

I will post one final update on this thread in a couple of days to confirm if the problem has been solved after running my normal, everyday applications. Once that is done, I will mark this thread as "solved."

I hope that this helped someone out there as it was a somewhat scary event to do all of this restarting all of the time in fear of breaking my newly hand-built computer. 

(By the way, I was trying to remember what I might have done to have triggered this event so suddenly in the past few days and remembered those Ubuntu updates. After finding the thread that helped solve my problems, I remembered in the very faint portion of my memory that I might have received a Tracker update that may have triggered the problem. Now I can finally get to work on my university paper that I have not been able to work on for the past week!!)

---

### Post by ShadowMKII on 2008-03-26
I tried opening about 15 applications with no slow down or errors whatsoever with memory remaining below the 500MB mark. My Ubuntu seems fine.

I will monitor this for another week to ensure there are no problems and will post back.

---

### Post by ShadowMKII on 2008-03-31
I have reported back as promised.

Nothing has changed. Everything is working fine. This thread is solved.

---

