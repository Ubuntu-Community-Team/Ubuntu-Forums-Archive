---
title: "How much swap space do I need for my Mac, and what is hibernate"
date: 2014-11-26
forum: General Help
---

### Post by Cason_Asher on 2014-11-26
I recently dual-booted my MacBook with Ubuntu 14.04 and the install went great, however whenever I try to boot to a live USB stick, the installed Ubuntu boots instead. The reason I want to boot to a USB is because when I set up my Ubuntu partitions, it was recommended to me that I have only 1 gigabyte of SWAP area (which is what I set up), but I also have heard online that I should have at least the same amount of SWAP as I have RAM (I have 4GB). So, I opened up Gparted and tried to shrink my Ubuntu partition to make room for more SWAP space, and I couldn't, I assumed this is because I am booted to it, so I made a live USB of Ubuntu, and even though it shows in my boot manager (rEFInd), my installed Ubuntu boots instead, bringing me to the log in screen. I also tried to make a live USB of Elementary OS, which did the same thing. So my first question is: Is 1GB of SWAP enough? If not, my second question is: How can I force the USB to boot instead of my installed Ubuntu?

---

### Post by sudodus on 2014-11-26
> **Cason_Asher said:**
> ... So my first question is: Is 1GB of SWAP enough? If not, my second question is: How can I force the USB to boot instead of my installed Ubuntu?

I don't know much about Mac computers. But I know about RAM and swap. If you want to hibernate the computer, you need at least as much swap as RAM (in gibibytes, base 2). Otherwise you can have less, and 1 GB swap should be enough.

Maybe you can get some tips from the following links

[How to install Ubuntu on MacBook using USB flash drive]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick")

and [this Ubuntu Forum thread by Quackers]("http://ubuntuforums.org/showthread.php?t=2174630")

---

### Post by Cason_Asher on 2014-11-26
Thanks for the quick reply. What exactly is the difference between hibernate and suspend? I have no issues with suspending the computer when I close the lid, so do I really need to worry about enabling hibernation?

---

### Post by sudodus on 2014-11-26
Hibernate means that the content of RAM is written to swap and the computer is switched off. Instead of a normal reboot, the content of the swap is read back to RAM. Suspend is a power saving state, but the computer is not switched off, the RAM is fed with power and the data are kept there. (Microsoft's hybrid sleep can create problems for dual booting Windows and linux.)

See for example this link

[http://windows.microsoft.com/en-us/windows7/sleep-and-hibernation-frequently-asked-questions](http://windows.microsoft.com/en-us/windows7/sleep-and-hibernation-frequently-asked-questions)

or browse the internet if you want it described by some other company/organisation ;-)

---

### Post by Cason_Asher on 2014-11-26
Alright, well thank you for your help. I'm used to a Mac (which only has sleep and off), so I think I will keep everything as-is. :cool:

---

### Post by sudodus on 2014-11-26
Good luck :-)

Finally, when you feel that your problems are solved, please come back here, click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

---

### Post by Cason_Asher on 2014-11-26
Done. Is there a way I can change the title of this thread? To simplify things and help others looking for how much swap they need on a Mac and what hibernation is?

---

### Post by sudodus on 2014-11-26
I can do it, and maybe you can do it (I don't remember what is possible for 'regular users'). Try selecting **Edit Post** for the first post and see if you find a box for editing the title. If you can't find it, please tell me, which title you want, and I'll edit it :-)

---

### Post by Cason_Asher on 2014-11-26
It doesn't look like I can. I think something along the lines of "How much swap space do I need for my Mac, and what is hibernate?" Thanks!

---

### Post by sudodus on 2014-11-26
Done :-)

---

### Post by Cason_Asher on 2014-11-26
Thank you! ;)

---

