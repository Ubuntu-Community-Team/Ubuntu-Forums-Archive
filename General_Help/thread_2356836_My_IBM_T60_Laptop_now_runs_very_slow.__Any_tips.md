---
title: "My IBM T60 Laptop now runs very slow.  Any tips?"
date: 2017-03-27
forum: General Help
---

### Post by egruber on 2017-03-27
Sorry to open a new thread, but the one I found that was relevant was closed.

I have an IBM T60 and I have run Ubuntu with Gnome as the desktop for years.  But lately I have noticed it is running very slow and the the hard drive seems to spin all the time holding up the response.  This never happened in the past.  I have seen tips for changing swapping and other things, but I wanted to check here first.  I appreciate any help.  Thanks!


 I have the following:

Ubuntu 16.04 LTS using Gnome

IBM Thinkpad T60 laptop
2 gb memory
Intel® Core™2 CPU T7200 @ 2.00GHz × 2 
Graphics - Gallium 0.4 on ATI RV515
64 bit
56.8 gb disk.

---

### Post by sp40140 on 2017-03-27
What does your filesystem look like? How much is used and how much is  free? Also, how much swap have you allocated? Also, swap file or swap  partition?
Is there any specific activity which causes this? What is the laptop used for primarily?

---

### Post by egruber on 2017-03-27
I use it primarily for web browsing and some light spreadsheet/document work.  I would be happy to answer your questions if you can be more specific on how to check.  Of the 56 gb hard drive 38 gb is free.

---

### Post by egruber on 2017-03-27
[ATTACH=CONFIG]274322[/ATTACH]

---

### Post by shridhar-kapshikar on 2017-03-27
can you please elaborate more on this.. meanwhile please try to check using $top command to check which are processes are taking more CPU/MEMORY. Have you upgraded your system recently?

---

### Post by egruber on 2017-03-27
I update the system as Ubuntu prompts me to.  I took a screen shot of the TOP command.  Does it show you anything?
[ATTACH=CONFIG]274323[/ATTACH]

---

### Post by shridhar-kapshikar on 2017-03-27
it is an average load and cpu/memory usage.

---

### Post by missmoondog on 2017-03-27
not much help here, but fwiw, i have a thinkpad t61 with the same specs as your machine with the only difference being i have an nvidia quadro graphics card.

i run lubuntu 16.04lts on it and it runs better than it ever did with any version of windows that i've had on it previously.

personally, i'd dump that bloated gnome desktop environment!

---

### Post by egruber on 2017-03-27
I've always run gnome and it was fine.

---

### Post by missmoondog on 2017-03-27
obviously not ALWAYS as you say it's running very slow now! ;)

---

### Post by egruber on 2017-03-27
Yes, you are correct.  My hard drive just spins and spins every time I switch windows or open/close something.

---

### Post by sp40140 on 2017-03-27
Do you have 32bit or 64bit os installed? you can check by system settings -> details. laptop platter drives are usually 5400 rpm. and your swap is being used regularly. And if you have 64bit, it would use swap a lot and cause performance issues.

---

### Post by egruber on 2017-03-27
These are the specs.  I have 64 bit installed.  And plenty of free space on the disk.

Ubuntu 16.04 LTS using Gnome

IBM Thinkpad T60 laptop
2 gb memory
Intel® Core&#8482;2 CPU T7200 @ 2.00GHz × 2 
Graphics - Gallium 0.4 on ATI RV515
64 bit
56.8 gb disk.

---

### Post by sp40140 on 2017-03-27
64Bit system is most likely the cause for performance problem. 64bit system is good more than 4 GB of ram. If you don't have 4 gigs, you run into this issues caused by more swap space being utilized which is on the 5400 rpm platter drive, it takes forever to read / write to platter drive (for memory). we can get bit more technical on addressable memory and such, but at the end. You should go for 32 bit os. And this is also the cause of your HD spinning all the time, as your swap gets constant use.

---

### Post by egruber on 2017-03-27
But then I have to completely delete and reinstall the OS, right?  There are no settings I could tweak to make the 64 bit perform better?

---

### Post by sp40140 on 2017-03-27
I am not aware of anything which tweaks your 64bit system to act like 32bit. I don't think it likely either. If you do decide to wipe and re-install, I suggest you keep one partition for is and one for data, so you don't have to worry about the data.

---

