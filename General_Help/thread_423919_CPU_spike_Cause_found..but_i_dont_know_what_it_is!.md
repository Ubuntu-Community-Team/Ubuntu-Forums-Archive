---
title: "CPU spike Cause found..but i dont know what it is!?!?"
date: 2007-04-26
forum: General Help
---

### Post by twistedbydesign on 2007-04-26
I am very new to Ubuntu and Linux...so there may be an obvious answer...but here's my deal.
I recently upgraded to Feisty from Edgy. Everything seemed to work fine.
I was going about my business and i decided to get my music collection from my Windows partition. I believe it is about 10gigs worth of music ((maybe useless information, but i figure the more detail i go into, the more easily the problem can be narrowed down).
After this i loaded my collection into Amarok which took quite a while. It seemed to work fine for a while then i started getting these random CPU spikes (basically everything freezes for a few seconds...then goes back to normal..this happens once every couple minutes). I couldnt figure out what it was.
It SEEMED to start right after i brought my music collection over...but for all i know this could be a coincidence.
I noticed on another thread someone was having a similar problem with CPU spikes and they were told to go to the terminal and type     top     to figure out what it was.
So i did this and it seems that these two things are what randomly spike :

kacpid 
kacpi_notify

my problem is that i really don't know what these are. Is it something i can get rid of?..or if not is it something i can alter. I have heard of other CPU problems with Amarok but this goes on even after i close out Amarok entirely.
Any suggestions would be greatly appreciated.
Thank you very much.

---

### Post by orb9220 on 2007-04-26
Your system specs please?

---

### Post by Smuve on 2007-04-26
Could it simply be indexing the files you moved over?

---

### Post by canadianwriterman on 2007-04-26
I had a similar problem with the Beagle file indexing program eating up all my CPU when indexing media files. If you have Beagle installed, try uninstalling it and see what happens.  

Other thoughts: kacpid is a kernel daemon related to the acpi power management function. If your computer does not use acpi, you can disable it in the processes dialogue. I'm not at my Ubuntu machine, but it's under the system preferences menu. The only thing is determining whether you need acpi. I believe that a laptop needs it, and I'm not sure what kind of system you're using.

---

### Post by twistedbydesign on 2007-04-26
I have an Emachines W2646 Desktop with 512 DDR ,Celeron 2.60GHz processor and a Maxtor 500GB harddrive (dual boot...so half is for Ubuntu)
i know Emachines are known for being unreliable...but i generally havent had problems with mine.
I don't have Beagle on my computer...and disabling the power management didnt get rid of the two processes that are spiking.

---

### Post by canadianwriterman on 2007-04-26
Only other thing I can suggest is search "acpi" in the Forum search box. There are a couple of threads that suggest adding to the boot string in GRUB to disable acpi on bootup. Sorry I can't be of more help... this seems to be a fairly grey area in the expertise on these and lots of other forums I Googled.

---

### Post by twistedbydesign on 2007-04-26
You've actually been quite a big help...the only way to determine whats wrong is by determining what ISNT wrong.
I do appreciate the help. Thank you.

---

