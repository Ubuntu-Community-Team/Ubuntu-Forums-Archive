---
title: "Hard-drive problem? Or something totally different?"
date: 2008-05-21
forum: General Help
---

### Post by agradan on 2008-05-21
I have quite a strange problem. I was not sure where exactly to post this so I came up with General Help... I don't even know if this is a Linux problem...

I have a Sempron PC with a SATA hard-drive running Kubuntu Dapper. Everything has been going well with my system for 1,5 years now.

Then, suddenly, a week ago, when I started my computer and chose the correct kernel from the Grub menu, I was given an error message about something being wrong with the root partition. Unfortunately, I didn't write down the message. I tried ctrl-alt-del and was faced by a BIOS error stating a S.M.A.R.T. problem with the only hard-drive of my computer. At that point I switched it off to do some research.

I bought a new hard-drive and backed up everything using live-Kubuntu. I even run diff after the copying and had no problem.

I then decided to give the drive one more try. I started using the computer as earlier and, surprisingly, it booted to Kubuntu with no problems. Everything seemed to work as supposed.

A couple of days later, the problems started again. Whole system got stuck for some tens of seconds. After that, it worked well again except that I noticed that there were some hard-drive related IO errors at dmesg log and the drive had been remounted read-only by Kubuntu. I still continued using the computer as it seemed to work, allthough any attempt by any program to write on the disk resulted in an error message.

The same problem has occured a few times after that. I usually spot it when mp3 playback suddenly stops and soon starts again like nothing had happened. dmesg is always flooded with errors afterwards but that remounting has not occured again. I have also successfully "called up" the problem by roughly touching the SATA wire of the disk.

Yesterday, I took the computer to a computer store to be checked for hardware problems. They found nothing. However, they told that it might be because of some software problem. The service guy had had similar problems and he had tracked them back to Firefox and Java eating CPU resources with some Java-enchanted web pages. Supposing that (too) is what is wrong, could it possibly cause those IO errors at dmesg log?

Shortly put, I have absolutely no idea what to do next. All the data is backed up so there is no need to worry about that. I also have my laptop to work with so there little rush to get this problem solved. However, I'd appreciate any ideas that might prevent my from wasting my money in replacing something that is not broken.

Any ideas?

---

### Post by wdaniels on 2008-05-21
> **agradan said:**
> I have also successfully "called up" the problem by roughly touching the SATA wire of the disk.

This seems like your best clue - can you reproduce it consistently like that?  It does not sound much like a software problem to me.

---

### Post by Robin T Cox on 2008-05-21
It would help if you can let us review your dmesg file, to be able to see what the actual messages say. It's then often possible to use google to compare the relevant message with other people's experience, and maybe find a solution that way.

To enable you to recall your dmesg file, see:

[http://www.watchingthenet.com/ubuntu-guide-for-windows-users-view-logs-with-system-log-viewer.html]("http://www.watchingthenet.com/ubuntu-guide-for-windows-users-view-logs-with-system-log-viewer.html")

---

### Post by danwood76 on 2008-05-21
Obviously the guy at the PC repair shop had no clue!
How would a java/firefox issue stop your machine from booting, and causing a SMART error when neither java or firefox are loaded?

I would replace the sata cable, if it is slightly damaged of the contacts have got dirty it can cause issues like you are describing.
It could also be the power connection, check that its pushed in fully, possibly change it for another connector in the case.

---

### Post by agradan on 2008-05-21
dmegs dump taken when the problem occured 2nd time is available at [http://www.ee.oulu.fi/~ag/dmesg.txt](http://www.ee.oulu.fi/~ag/dmesg.txt)

---

### Post by wdaniels on 2008-05-21
> **danwood76 said:**
> Obviously the guy at the PC repair shop had no clue!

lol, I was trying to be more subtle than that but you said it anyway :D

---

### Post by wpshooter on 2008-05-21
Why don't you download and run PC-Doctor on this computer for several hours/days and that would more than likely tell you wherein the problem lays.  Run "complete" series of testing for a goodly number of hours.

Have you checked your CPU temperture thru either the BIOS or an independent program ?

My "GUESS" would be either hard drive going bad or power supply possible going bad.

---

### Post by agradan on 2008-05-21
Right now it appears that I can't reproduce the problem by rocking the SATA wire. That might hint of something more severe, right?

I don't think the problem is due to any sort of overheating. At least, last time it occured, I checked all possibly heating parts of the system and none of them was even close to too hot.

I have run the SeaTools tests (the booting CD version) on the hard-drive as it is a Seagate one. The program found nothing. The repair shop had run those tests (Windows version) too and they found nothing either.

What exactly is the PC Doctor someone mentioned? Google found it's web page but I couldn't find anything downloadable there.

By the way, I just restored the root partition from backup after getting the computer back from the repair shop, just to be sure. The only weird thing I noticed was after the first boot following the restoration: for some reason, the clock had stepped forward for one extra hour. I doubt if this should have anything to do with the original problem but it think it is a bit strange, nevertheless. The repair shop had booted the computer to Windows XP but that shouldn't cause such things.

---

### Post by wdaniels on 2008-05-21
> **agradan said:**
> The only weird thing I noticed was after the first boot following the restoration: for some reason, the clock had stepped forward for one extra hour. I doubt if this should have anything to do with the original problem but it think it is a bit strange, nevertheless. The repair shop had booted the computer to Windows XP but that shouldn't cause such things.

XP and linux use the system clock differently. Linux keeps the clock at UTC time and uses the time zone setting to work out the actual time in your current location, whereas XP just sets the clock to whatever the current time is at your location. That is probably the cause.

I honestly don't think you will get anywhere with software diagnosis tools - I wouldn't say that it's impossible for software to cause such errors, but intermittent I/O errors like you describe are characteristic of a hardware issue and I would say that should be the focus for further investigation.

---

### Post by agradan on 2008-05-21
This looks like a hardware problem for me too. It's just that I have absolutely no clue what is or is about to be broken. As I  already told, rocking the SATA wire today didn't reveal anything. The hard-drive has still 4 months of warranty left so I kind of hope it to be the cause for this. I really hope that it's not motherboard that is breaking up because that would lead to a bigger upgrade which in turn doesn't make sense right now because I will probably spend the next fall abroad without using my desktop computer for six months.

What do you suggest? Is there anything else to do but to wait until something finally really breaks up?

---

### Post by xueg0i on 2008-05-21
Did you perhaps install some other new hardware recently? It sounds to me as a possible power shortage. This can be caused by a newer videocard or such.

---

### Post by danwood76 on 2008-05-21
I think its probably not a power issue, more of a SATA connection issue as once its going it goes right?
If its a power issue it would be more unstable after the system is loading. (under drive load)

You could try pluggin the drive into another sata port, I would (if you have a spare cable or can steal one off a friend) replace the sata cable also as theyre cheap.

---

