---
title: "Jpeg executable?"
date: 2006-11-16
forum: General Help
---

### Post by ajgreeny on 2006-11-16
I started a thread similar to this last night, about 18 hours ago but have not been able to find it so here is a similar request for information.  Sorry if the first thread appears later, but I assumed it shouldn't take that long to go online normally, so have repeated myself, in case it got lost in the ether somewhere.

I use Dapper Kubuntu and have just found in file properties that some of the jpegs saved from my digital camera are executable and others are not.  There seems to be no pattern to this.  I wonder why a jpeg should be executable in the first place and why all the jpeg files are not the same?

All the files work well in all programs as far as I can tell, Digikam, g-thumb, f-spot, etc all show them with no problems, so anyone got any thoughts on why this situation happens on my machine?  Am I missing some important point or is it just chance?

---

### Post by ESPOiG on 2006-11-16
i have the same sorta prob mine also happens with other file formats, but i dont worry cause i know it aint an exe :D... so it dont bother me

---

### Post by Ramses de Norre on 2006-11-16
Your digital camera probably uses fat which doesn't have these permissions so I guess you need to look for the issue at how the files are transfered from the camera to your ext3 partition.
It may be a stupid bug in the program you use for that, it wont really hurt anyway.

---

### Post by ajgreeny on 2006-11-16
Hi Ramses

I usually transfer the pics from memory card simply using a USB card reader, so much faster than the camera itself, and put them straight into a subfolder of my ~/Photos folder named appropriately for the pics in question.  I suppose it could be the difference between photos I have transfered direct from the camera compared to those through the card reader, but I have no way to find that out now, and if it really doesn't matter to the files, it certainly doesn't matter to me.  I'm just very curious about this fantastic new (well, 18 months for me now) OS that I really love more and more.  That never happened to me in 15 years of dos/windows.

---

### Post by Ramses de Norre on 2006-11-16
The only difference would be that if the files contain executable code instead of jpegs that that code could be executed on your machine when you open the file. This is a method that is sometimes used on windows to make an executable look like an mp3 for example (using .mp3.exe as extension and windows hides extensions by default so the user only sees .mp3).
On linux though, is the risk that such malicious code would überhaupt run so small that you shouldn't be worried about it. Definitely not because the files are made by yourself. So I'd just ignore it =)
(Although it could be interesting to search after the source of the difference...)

---

