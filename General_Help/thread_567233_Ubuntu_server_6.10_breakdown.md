---
title: "Ubuntu server 6.10 breakdown"
date: 2007-10-04
forum: General Help
---

### Post by dbzsephiroth on 2007-10-04
First of id like to make sure im writing this in the right section....any complaints? *looks around room to see if anyone objects*..Nope!...ok. cool.


Well now to the error/bug. See i have been using Ubuntu server now just resently, teaching myself things like PHP, mySQL server and an attempt at a email server. I also know how to do DHCP, DNS (fun...real fun that is) samba, domain controller etc etc, this is all for my networking administration course im currently doing atm.....but i digress. Its seems that after installing and attempting to configure Postfix on the ubuntu server i was forced to reboot...cant remember y, but i had to. Now this is where it went all funny.

To begin with, i got this error on boot up.

[IMG]http://i66.photobucket.com/albums/h247/Auron_Roach/error1.jpg[/IMG]

well ok that doesnt tell me much so i went into recovery mode to see what exactly was failing.

[IMG]http://i66.photobucket.com/albums/h247/Auron_Roach/error2.jpg[/IMG]

Wait....done?....then it just hangs, which means that i really dont know what its doing right at this momnet.


Ive done my fair share of googling and found a few corrosponding errors....however, the solutions require me to have the machine up and running in order to correct some settings to get it working. But as u can see....i cant. Also this is not a removeable drive error as the first error seems to comply with.

All these errors occur right after the grub boot, so there really isnt anyway of fixing this without using a live cd, or completely reinstalling.


Other details are that this machine is running on a virtual machine ( VMware ), if u need any other details please post back with the request with any instructions that u want if theres something specfic u want.




Appreciate it guys, thanks
Yamashita masato

*for entertainment pruposes, here is a random emote of Goku holding a LOL! sign, please look and laugh till ur hearts content*

:lolflag:
STOP LOOKING AT THE ANIMATED IMAGE OF GOKU AND POST! XD

---

### Post by tgalati4 on 2007-10-04
Try Control-C if it is stuck at a certain point in a boot-up script.  I don't see any errors otherwise.  Looks like normal boot-up dialog.  Errors are pretty obvious when they occur.

Make sure your mouse is in the window and the window is active when you hit Control-C.

---

### Post by dbzsephiroth on 2007-10-05
thanks tgalati4 for the quick reply, however being written at 2am it seams i missed a few crucial details (as well as some really....really bad spelling errors)


There is no input, the the whole boot up process just hangs, any input results in odd characters being written. Which means that it cant accept any input at all. U know how it prints ^[[x or something like that.


So i tested what u suggested anyway, and like i expected nothing happened. A quick glance at what the machine specs - both host and VM machines (which is nothing at all) to see whats going on shows me that there is defiantly something wrong with the bootup process.


So.....uh..yeah help?

---

### Post by dbzsephiroth on 2007-10-05
Bump....

sorry guys, just i have to figure this out asap before i get back to tafe from holidays.

---

