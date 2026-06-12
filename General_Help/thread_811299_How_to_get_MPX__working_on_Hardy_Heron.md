---
title: "How to get MPX  working on Hardy Heron"
date: 2008-05-29
forum: General Help
---

### Post by brnetonboy on 2008-05-29
I have always wanted multiple cursors and multiple Active applications! I was SHOCKED to find out that Multi-Pointer X Server does just this!

But I'm a Linux Newb, and I don't understand what MPX website is telling me. It says it's part of the X window System... do I have that already? I just got Compiz working... 

Next it tells me that my devices will be automatically configured through HAL. Well I have two mice hooked up and nobody has told me "good morning Dave" so I don't think it's working... or am I missing something?

Then it says something about compiling MPX?? :0

Are there any directions for getting MPX installed that are geared towards beginners?

---

### Post by Javed_Ahamed on 2008-05-29
wow, I just started looking for this as well. For those who want to help out this is the main mpx site: [http://wearables.unisa.edu.au/mpx/](http://wearables.unisa.edu.au/mpx/)

now how can we get it working on hardy heron :)

---

### Post by Javed_Ahamed on 2008-05-30
I couldnt really find many guides on how to install this online... but apparently it has been merged with the master x server or something? Should this make it easier to install or is in the repository now guys? I would really like to use this program would make dual screens so much better :)

---

### Post by matt-j on 2008-05-31
Imagine how cool this would be to have this in Intrepid Ibex.  

This week Microsoft are showing off multitouch in Windows 7 - which *might* come at somepoint in the future - imagine we could say "You don't have to wait for Windows 7 - we have multitouch now!"

That would be so cool

---

### Post by starcannon on 2008-05-31
> **matt-j said:**
> Imagine how cool this would be to have this in Intrepid Ibex.  

This week Microsoft are showing off multitouch in Windows 7 - which *might* come at somepoint in the future - imagine we could say "You don't have to wait for Windows 7 - we have multitouch now!"

That would be so cool

I'm not entirely sure I'm interested in multi-touch; touch screens have been around quite a while now, and yet I have not run out to buy one; a primary reason being, I already clean my monitor more than I want to, finger print smudges and all the yuck that comes with does not sound like something I want to add to my day.

I will say its always intrigued me though, but I'll wait for holographic display screens to be developed first.

---

### Post by Javed_Ahamed on 2008-05-31
Yeah but this MPX thing isnt all about multitouch either. I want it since you can have more than one cursor, and since i have two x windows i can have one cursor on each x window and use one mouse for each window, or one mouse for both windows and just flick a button on my mouse to switch. too bad this thing is a pain to install (at least in my opinion since i dont understand heads or tails of it, its not in the package manager or a .deb so im lost :) ):lolflag:

---

### Post by zmjjmz on 2008-06-08
I'd like to see this too.

---

### Post by brnetonboy on 2008-06-10
It's good to know I'm not the only one who is interested in this but too confused to figure out how to install it. Too bad, as I really am interested in this and it seems super cool, but I just can't figure it out. Thanks for the moral support though!

---

### Post by Rhubarb on 2008-06-10
I would be very interested in getting MPX up and working in Ubuntu (hopefully with nvidia drivers).

Wiimote with whiteboard [http://code.google.com/p/linux-whiteboard/](http://code.google.com/p/linux-whiteboard/)
and cwiid [http://abstrakraft.org/cwiid/](http://abstrakraft.org/cwiid/)
would be just brilliant!  (not to mention it'd be good with multiple mice + keyboards).

---

### Post by motin on 2008-06-10
There is already a thread for this subject: [http://ubuntuforums.org/showthread.php?p=5153570](http://ubuntuforums.org/showthread.php?p=5153570)

Cheers

---

### Post by lieryan on 2008-06-10
The configuration for having two or more independent mouse, monitor, and keyboard has another name: Multihead, the idea is to have a single computer (box) to be used by multiple user at the same time each with their own mouse, keyboard, and monitor. 

I've never tried it myself though, so I can't comment on how it is done.

---

### Post by Rhubarb on 2008-06-10
> **motin said:**
> There is already a thread for this subject: [http://ubuntuforums.org/showthread.php?p=5153570](http://ubuntuforums.org/showthread.php?p=5153570)
You just linked back to this same thread :P


Here are some threads that are a bit more relevant:
[mpx for Ubuntu]("http://ubuntuforums.org/showthread.php?t=397414&highlight=mpx")
[Hooray, MPX is merged to master!]("http://ubuntuforums.org/showthread.php?t=809663&highlight=mpx")
[Screenshot of 18 mice operating simultaneously!!!]("http://ubuntuforums.org/showthread.php?t=824425&highlight=mpx")
[Using 2 mice, showing 2 mouse pointers?]("http://ubuntuforums.org/showthread.php?t=182600&highlight=mpx")

---

### Post by motin on 2008-06-11
> **Rhubarb said:**
> You just linked back to this same thread :P


Here are some threads that are a bit more relevant:
[mpx for Ubuntu]("http://ubuntuforums.org/showthread.php?t=397414&highlight=mpx")
[Hooray, MPX is merged to master!]("http://ubuntuforums.org/showthread.php?t=809663&highlight=mpx")
[Screenshot of 18 mice operating simultaneously!!!]("http://ubuntuforums.org/showthread.php?t=824425&highlight=mpx")
[Using 2 mice, showing 2 mouse pointers?]("http://ubuntuforums.org/showthread.php?t=182600&highlight=mpx")

Bummer! Thanks :) - I meant to link to that first suggestion of yours... 
In that thread there was a Howto for Gutsy (or was it Hardy), but currently it seems to be offline...

---

### Post by freakalad on 2009-06-09
I suspect that multitouch may be implemented into the kernel around-about 2.30.x
[http://www.linuxhq.com/kernel/v2.6/30-rc7-git5/Documentation/input/multi-touch-protocol.txt](http://www.linuxhq.com/kernel/v2.6/30-rc7-git5/Documentation/input/multi-touch-protocol.txt)

---

### Post by kaefert66014235 on 2011-05-19
I just got MPX working with Ubuntu 11.04 Natty! Its really beautiful and quite easy to set up, once you found the (hard to find) instructions --> [http://alec.mooo.com/mpx.html](http://alec.mooo.com/mpx.html)

Summed up: 
-) List your devices --> xinput list
-) Create a master for second set --> xinput create-master new_name
-) put the mouse and keyboard of the second set into the new_master --> xinput reattach id_of_device id_of_new_master

Hope this post helps others to get to their goal more quickly than me.

---

