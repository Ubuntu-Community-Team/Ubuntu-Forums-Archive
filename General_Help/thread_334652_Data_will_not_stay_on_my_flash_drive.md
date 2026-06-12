---
title: "Data will not stay on my flash drive"
date: 2007-01-09
forum: General Help
---

### Post by ambir on 2007-01-09
With my flash drive or any other device i put in it like a sony duo card. When i put the files in the mounted folder, they show that they are there. But when i take the card out and put it back in, the file isn't there. On my sony duo card, it says i've used 200mb even though it shows that there are no files on the drive as yet.](*,)

---

### Post by konst88 on 2007-01-09
You need to unmount it before ejecting.
Right click on the device on the desktop, and choose unmount.

---

### Post by meng on 2007-01-09
Yes, many folks pull the card out without thinking to unmount ("eject" in Windows-speak). Ubuntu doesn't do a final write until the unmount - it prolongs the life of the flash drive by cutting down on write-cycles.

---

### Post by megamania on 2007-01-09
> **meng said:**
> Yes, many folks pull the card out without thinking to unmount ("eject" in Windows-speak). Ubuntu doesn't do a final write until the unmount - it prolongs the life of the flash drive by cutting down on write-cycles.
One thing I've been wondering for a while is why Windows doesn't (apparently) destroy flash cards, since as far as I know it doesn't cache the data by default.

---

### Post by Swankyman on 2007-01-09
The things is most people with normal usage won't observe Flash memory failure.

Thats because each memory location on the flash chips can undergo 10,000 and 1,000,000 write cycles before failure is likely. The only time you would see a problem is say if you used  flash memory to hold your swap partition which gets written to alot each session.

So really its not Windows been clever, just the fact you never really use Flash devices that intensely.

:-k 

Rich

---

### Post by orb9220 on 2007-01-09
And I am curious as I have tested thumb drives and my sansa e250 uplugging without unmounting first on both xp and ubuntu with zilch data lose.  Is it because it is still 1.1 usb or and I am just lucky?

I haveunplugged without ejecting  usb keys at least 50 times and my sansa about 30 or so and never have lost data.

Just wondering if this is more an issue with usb 2.0 with a higher chance of corruption?

---

### Post by ambir on 2007-01-09
Windows destryoed my 4GB flash about a year ago, i was using the 'remove safely' feature before i pulled it out. But in about a month, all my files started corrupting. I have no idea why that happened.

Thanks alot, konst88, I never thought that the unmount thing would ever make a difference.

---

### Post by Swankyman on 2007-01-09
Depends on how much data you transfered to the drive. A Small amount takes hardly any time thus likely to have finished transferring before you pull it out. 

I had the opposite problem with usb 1.1 and a flash thumb drive and it kept corrupting but not my usb 2.0 one. (this wasn't with ubuntu though :-D, this was with gentoo ages ago and it wasn't setup up to tell me it had fully umounted)

---

### Post by meng on 2007-01-09
What about these new notebook computers coming out with flash hard drives rather than conventional ones? Does anyone know whether these hard drives are much more likely to fail with "normal, average" use?

---

### Post by Swankyman on 2007-01-09
not really cos they use a technique called 'Wear levelling'

'Conventional file systems like FAT, ext2 and NTFS were originally designed for magnetic disks and as such rewrite many of their data structures (such as their directories) repeatedly in place. This makes them poorly suited for use on media with erasure limitations. Wear-levelling attempts to work around these limitations by arranging data so that erasures and re-writes are distributed evenly across the medium. In this way, no single sector prematurely fails due to a high concentration of write cycles.'

[http://en.wikipedia.org/wiki/Wear_levelling](http://en.wikipedia.org/wiki/Wear_levelling)

Rich:-|

---

### Post by meng on 2007-01-09
Cool, that explains a lot. After reading the wiki, I'm still a little unsure whether these will rely on the microcontroller, or use a different filesystem to NTFS (since most of these computers will presumably be used with Windows). I assume it's the former. Also, this explains why the (now-defunct ?) FlashLinux used JFFS2!

---

