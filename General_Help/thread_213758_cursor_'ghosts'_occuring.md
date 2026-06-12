---
title: "cursor 'ghosts' occuring"
date: 2006-07-11
forum: General Help
---

### Post by greengrocer on 2006-07-11
Hi All,

I was wondering if someone knew the solution to the following problem.

I am running Ubuntu 5.10 Breezy Badger and have noticed that in some applications (especially Firefox, OpenOffice and Gedit), if I move the text cursor with the arrow keys, it leaves ghosts of the cursor behind (vertical lines).

It makes navigating where your cursor really is, quite difficult.

My gfx card is an Nvidia GeForce 6200 with Turbo Cache.

Regards,
Greenie

---

### Post by thojoh on 2006-10-14
> **greengrocer said:**
> Hi All,

I was wondering if someone knew the solution to the following problem.

I am running Ubuntu 5.10 Breezy Badger and have noticed that in some applications (especially Firefox, OpenOffice and Gedit), if I move the text cursor with the arrow keys, it leaves ghosts of the cursor behind (vertical lines).

It makes navigating where your cursor really is, quite difficult.

My gfx card is an Nvidia GeForce 6200 with Turbo Cache.

Regards,
Greenie

Yes, same problem here!

It started happening at some point, I do not know exactly when. Probably with a new update of ubuntu (or a part of it. I tried to ignore it in the hope that it will go away with a bit of patience and probably another update - which I have found out is often the best strategy for me on ubuntu  :) ,  but unfortunately, this thing didn't go away. And it sure is annoying!!!

I only have the problem with Firefox and OpenOffice. Gedit works as it used to. But especially for OpenOffice it is making text editing and layout sort of 'challenging'.  ;) 

Is this thread still active?

Did you find a solution, Greenie?

thanks for helping,

thomas

---

### Post by thojoh on 2006-10-14
SOLUTION FOUND!

at least for my computer. I had the same problem: which was that I had those 'ghosts' of the cursor (caret, whatever it is called - the vertical line that shows you where the letters you type will appear). Many of these lines where just staying on the screen when I was moving through text in OpenOffice or Firefox.

I had to change my NVIDIA driver that was installed. If you have a certain graphic card version, you might need a different (older) driver to get rid of this ghosting thing. At least, that was it with me.

Changing it was easy using Synaptic:


1. Search for "Nvidia" in Synaptic

2. Look which NVIDIA driver is installed.

On my computer, "NVIDIA binary XFree86 4.x/X.Org driver" was installed (which probably is the default for computers using NVIDIA)
I had to change it to the "legacy" version:
"NVIDIA binary XFree86 4.x/X.Org 'legacy' driver"

3. Install the "legacy" version of the NVIDIA driver
(uninstalling the current driver will automatically be done by Synaptic)

4. In the terminal, run "sudo nvidia-glx-config enable" to enable the driver. 

5. Restart you computer.

Done!

(of course this solution only applies if you have one of these graphic cards that need the older 'legacy' version. I didn't know for sure about my graphic card, but I just tried it and it seems that that was the case. Now, the problem is solved.) 
The computer makes a backup of the changes to the xorg.conf file and tells you in the terminal which command to use to bring back the old settings. So if you note down that command before restarting you computer, you can always revert your changes if it doesn't solve your problem.

I hope this helps some of you!  (I have seen the problem posted several times, but never seriously addressed with a soution.)

all the best!   :-D 

thomas

---

