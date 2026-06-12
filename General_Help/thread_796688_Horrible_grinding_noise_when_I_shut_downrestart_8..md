---
title: "Horrible grinding noise when I shut down/restart 8.04"
date: 2008-05-16
forum: General Help
---

### Post by ByKeLaO on 2008-05-16
I've just installed Ubuntu 8.04 along with all the updates and for the most part it's excellent. However, when I shut down or restart the computer, the Ubuntu logo appears and then my computer starts making a horrible grinding noise like the sound the hard disk makes only 10 times louder. I just switch it off before it reaches this point in the shutdown sequence because frankly I'm scared it might be doing some damage. I didn't get this problem with Gutsy. Anyone know how to fix it?

---

### Post by joshsmith on 2008-05-16
hey, cant help you directly, (i hope someone can)
but if you really are worried and either pull the power from your computer or hold down the power button or press reset then you can do some damage to your hard drive that way
linux has a nice safe way to shutdown in times of trouble, which might be useful for you in the meantime:
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)
particularly the the raising elephants parts which lets you turn off your computer without the risk of damaging anything (usually useful in a crash, but probably could help you to)

---

### Post by ByKeLaO on 2008-05-16
Thanks! That'll do as a temporary solution until this gets fixed.

---

### Post by ByKeLaO on 2008-05-24
Still awaiting a proper fix :D

---

### Post by Anduu on 2008-05-25
Sounds to me like you've got some hardware starting to fail.Check your fans and drives.

I somehow think it happening since your move to Hardy is purely coincidence.

---

### Post by ByKeLaO on 2008-05-26
That seems unlikely to me. This never happens when using/booting/shutting down windows or in fact any other version of Ubuntu. It seems like too much of a coincidence that the grinding sound always happens when I shut down the computer, at precisely the moment when the progress bar fully empties.
Should I try reinstalling Ubuntu (again)?

---

### Post by ByKeLaO on 2008-05-26
Incidentally, I found the "Linux is NOT Windows" article in your sig very interesting! I'll be sure to use it on my friends who still see Linux as "beta" software.

---

### Post by ByKeLaO on 2008-05-27
Any other suggestions...?

---

### Post by ByKeLaO on 2008-06-04
Just installed some updates and they appear to have fixed it.

---

### Post by Errors suck! &quot;Kairu&quot; on 2008-06-04
i also think its a coinsidents that your hard disk would be grinding after instullation but sorr your disk may be F#@*ed. the portion of your drive that ubuntu is installed may be damaged. or the read/write hed may freek out when it gos to the ubuntu partition.

 all i can say is back up evrything on your drive and get it cheked out. i sirriosly boubt its ubuntu. if your drive is more than 5 years old (that is if it runs nonstop) it may be the drive. just be lucky you dident loos your data... if you have anny.

you may just want to buy a new drive. getting your drive checed may be expensive. it cant hurt, if the other drive is fine, more disk memory for you! you may also want to check the ubuntu installer disk fo defects.

---

### Post by Ameneon on 2008-06-04
I concur with the "your disk is failing" theory. I've had a harddrive fail with the same symptom for me (generally; scratching, squeaking, bird chipper and so on are bad and very clear signs of a failing HDD), and I've worked some time now as tech support for one of the larger computer vendors and it's the same story there. The fact that the noise only comes after updating is likely because portions of the data that consisted of the update have been written to the parts of the HDD with the problem. If you have any good diagnostic utility I would strongly recommend running it (Dell has some built in, other vendors have their own, and if not I know there are numerous utilities on the net freely available) in as complete a mode as possible.

Even without this, start making plans for replacement. With my HDD (one of the last IBM HDD's that came out, this was some years ago) it took several months from the first symptoms until the drive finally failed entirely, but barring that something is producing sound over your speakers (and I'm sure you would have mentioned it if that was what it was) then your hard drive is heading down that road.

---

### Post by ByKeLaO on 2008-07-02
> **Ameneon said:**
> I concur with the "your disk is failing" theory. I've had a harddrive fail with the same symptom for me (generally; scratching, squeaking, bird chipper and so on are bad and very clear signs of a failing HDD), and I've worked some time now as tech support for one of the larger computer vendors and it's the same story there. The fact that the noise only comes after updating is likely because portions of the data that consisted of the update have been written to the parts of the HDD with the problem.

Damnit. I was hoping to spend that money on a new case :(
I'll have to scrounge an external HDD from my parents to back everything up.

> **Ameneon said:**
> If you have any good diagnostic utility I would strongly recommend running it (Dell has some built in, other vendors have their own, and if not I know there are numerous utilities on the net freely available) in as complete a mode as possible.

I built this computer myself, so I guess I'll have to find said software on the internet ;). Do you have any suggestions for diagnostic tools for Windows or Linux?

---

