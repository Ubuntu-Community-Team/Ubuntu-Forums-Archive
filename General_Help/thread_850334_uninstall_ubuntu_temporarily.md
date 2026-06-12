---
title: "uninstall ubuntu temporarily"
date: 2008-07-05
forum: General Help
---

### Post by joordee on 2008-07-05
Hi guys,I had vista on my computer and I decided to dual boot ubuntu as well, now that ubuntu is installed I cant get back to windows, A screen comes up saying loading grub please wait, but I dont get the choice of loading vista

---

### Post by niyonk on 2008-07-05
Hi, you might want to repair vista's bootloader
and use the easybcd to add ubuntu entry 
or if you want to use grub as the default, then post your menu.lst (where the entries are stored)
type into the command line 'gedit /boot/grub/menu.lst '
and paste the entries, from there we can help you :)

---

### Post by joordee on 2008-07-05
how do I do that

---

### Post by niyonk on 2008-07-05
how do you do what? :tongue:

the Grub part or vista bootloader part? :)

---

### Post by joordee on 2008-07-05
you could tell me how to do both if you dont mind

---

### Post by niyonk on 2008-07-05
**Vista** - insert the Vista DvD, let it boot. and now check the first attachment then choose start-up repair from the second attachment.
your vista will be safe to boot now, but not Ubuntu you are going to have to add it from the easybcd program.

-Ubuntu...:-k hm...i am not sure but maybe you menu.lst can tell us something before i can know if it is the wrong entry in Grub

---

### Post by joordee on 2008-07-05
Ill give you some more information. I installed Ubuntu on an external hard drive, Ubuntu will only work if I make my eternal drive the first disk in setup. Vista is supposed to be on the my original built in drive but when I boot from that drive I get a screen that says loading grub please wait..., but it doesent do anything, the dvd only works when I boot from my external drive,and I only saw an option to install windows probaly because it doesent see that windows is already installed on the other disk, but I cant install windows on te other disk because it cant install windows on a drive that uses a usb.so how would I get the disk to work on my interal hard drive

---

### Post by niyonk on 2008-07-05
I am afraid I can't help you much when it comes to external hard drives...:(

As for you internal one, we can help you make grub recognize the vista partition from there..someone will help you in your dual-boot process.

-Again, i need to know what your menu.lst contains otherwise i cant tell why vista isn't booting..
BTW, can you view your vista partition from Ubuntu itself?

Sorry, again. I haven't played around with external HDDs alot. I wouldnt want to ruin your setup ;)

---

### Post by joordee on 2008-07-05
no it says that it cant mount it.

---

### Post by joordee on 2008-07-05
I can only view the partition if I boot the windows dvd and and I can see the partitions that I have a choice to install windows on, but I tried to install windows on the first partition which is my internal hard drive and it says that it cant install on that partition(says something about volume, even though it has 126 gigs of free space)

---

### Post by niyonk on 2008-07-05
oops! double post

---

### Post by niyonk on 2008-07-05
*bump*

:confused: now i am confused...
Sorry I wasn't of any help
Someone else will come to your rescue don't worry ;)

One last comment: try 'sudo fdisk-l' to see a list of your partitions

---

### Post by jackhe22 on 2008-07-05
When it boots Ubuntu, It says Press "ESC" to enter menu.....
Press ESC!!!
Now use your arrow keys to select Vista at the bottom.
When in Vista go to the Start menu, select the search box and type msconfig. Press enter
Select boot and from the menu select Vista. Reboot (like normal again!)
Otherwise you need to go to BIOS and select the IDE - or SATA as your first boot device and your External last.


Happy Ubuntu!
jackhe22

---

### Post by joordee on 2008-07-05
when it boots ubuntu from where? my external drive where it actually boots ubuntu or my internal drive where it says loading grub please wait...

---

### Post by joordee on 2008-07-05
well heres what i did do, since ubuntu only boots from my external drive i booted from ther and presses escape and ended up with a black screen that says boot, and you can type things there, is there anything I can type to fix my problem from there.

Anybody?

---

### Post by joordee on 2008-07-05
or do i press escape where it says loading grub please wait...

then it says error 17

---

### Post by joordee on 2008-07-05
will someone please reply

---

### Post by ago on 2008-07-05
grub in wubi starts AFTER the windows bootloader, unless you installed the full version of Ubuntu from CD (not wubi). You might want to run chkdsk /r from windows CD or another rescue CD.

---

### Post by niyonk on 2008-07-07
Joordee, I'm back!

I must say I am really disappointed by your level of asking :-s
Please...if you know you need help. Try and be as descriptive as possible to ease the process.
As you can see most of the answers you got were merely guesses because none of us knew exactly what you were asking :(

The bottom line is...the short sentences you write can mean more.
I hope you find the solution to your problem :)
Cheers! :biggrin:
~niyonk

p.s. Welcome to the forums By-The-Way ;)

---

