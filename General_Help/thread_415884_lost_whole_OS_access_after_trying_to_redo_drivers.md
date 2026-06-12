---
title: "lost whole OS access after trying to redo drivers"
date: 2007-04-20
forum: General Help
---

### Post by kystorms on 2007-04-20
if this belongs somewhere else, please let me know and i will move it.

after spending all day upgrading from dapper to edgy and from edgy to feisty, i finally got it all done. i then proceeded to follow a guide for beryl, which had me changing the driver for my ati radeon 7000 graphics card, after doig the code in the guide, it said to reboot to go to the next step, which i did. after that all i can do is get to the files section, it will not even go into the program at all. it says something about a GMD missing, (this is a blue screen with white text, like what the bios files look like.
My question is, do i have to redo from dapper ( on disk) and then upgrade all over again, or is there a way to get into the program to redo what ever I did?
thanks
:confused:

---

### Post by bwhite82 on 2007-04-20
Hmmmm....perhaps an essential package was not installed during the upgrade? I think you might be referring to gdm. Try this command, which BTW, will not hurt anything if you happen to already have gdm installed:

> sudo apt-get install gdm

---

### Post by kystorms on 2007-04-20
ok, when i boot up the pc, i get to the screen where it is black, the it goes to a blue with white text screen, telling me that the xerver failed to start, then another that says xserver is disabled and that i need to reset the GDM when configed correctly restart

any ideas?
can i use the idea you gave above from the black text screen?
:confused:

---

### Post by kystorms on 2007-04-20
ok
at the text screen after the lovely blue screens, i ran the code you suggested, and it said that i already had the correct up to date gdm, any other codes i could try?

thanks

---

### Post by bwhite82 on 2007-04-20
Since you have an ATI card, what you can do for now at least is edit a file until you can get your video driver problem worked out:
> 
sudo nano /etc/X11/xorg.conf

In it, you should see a section that looks *similar* to this:

> Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Change whatever YOU have in the quotes above ("fglrx") to "vesa". To save it, you have to hit CTRL+O and to exit, CTRL+X, then reboot. After you're in Ubuntu, check out the wiki, [http://wiki.ubuntu.com/BinaryDriverHowto/ATI](http://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

### Post by jppranker on 2007-04-22
I have the same card mine has 64 meg of ram. I tried the procedure you did and had the same results. My problem is jerky dvd playing. Is that your problem? If so maybe we can work together. I have got mine back up and running. Dvd playing of course is still a little slow like when they replay a call for football. Well maybe not quite that bad. Anyway hope everything works out.
JP

---

