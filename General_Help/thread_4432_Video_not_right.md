---
title: "Video not right"
date: 2004-11-15
forum: General Help
---

### Post by ITLogic() on 2004-11-15
Ok, I admit, I just installed Ubuntu yesterday for the first time and haven't had the time to really deal with it since. So, if this is one of those RTFM things, please tell me to just shut up and get a life.  :wink: 

Anyway, when I first booted into Ubuntu and after the Ubuntu splash screen, I got a black screen with a glob of white lines off to the right of thr screen.  The GUI started, but it had lines through it here and there. The background was black and I tried to change to one of the backgrounds that came with the system. When I did, nothing happend. I called up some other programs, like firefox, and they were jittery as the screen loaded and lines appeared and disappeared. Finally, there seems to supposed to be some system icons at the bottom right. All I see are some boxes, but no icons appear.

All-in-all, the graphics are very choppy. I should also mention that I tried installing Mandrake before, and I go no GUI at all on that one. My video card is an old PCI Triden, but it was detected correctly during installation. The rest of the system in a Pentium 200mghz with MMX, 96 megs ram, 10 gig Quantum hard drive with 5gigs for Windows ME and 5gigs for Ubuntu. Also note, in Windows ME that graphics are fine. Any suggestions for settings to change that might help?  :-?

---

### Post by Marauder1 on 2004-11-15
Hello, are you fresh with Linux or do you know a bit ?
Can you change your video driver to vesa instead on your
current brand name in your XF86Config-4 file and see if
it correct the image.

In a terminal type :

sudo nano /etc/X11/XF86Config-4

and go under : Section "Device"
and change the Driver	"whatever" to Driver  "vesa"
save the file with a ctrl+o and exit with ctrl+x and reboot.

Ciao.

---

### Post by ITLogic() on 2004-11-15
Thanks Marauder1 for the super fast reply!  \\:D/ 

Yep, I'm as green as the grass on the other side! This is my very first experience with any distro of Linux. I do understand your post thought, I have been reading alot and, at least, have a theoretical clue.  :wink: 

I'll tru your suggestion as soon as I get a chance, which will be later this evening CT. I'll post my findings ASAP.  :grin:

---

### Post by spirospr on 2004-11-15
I think that my reply could offer some help to you too :

[http://www.ubuntuforums.org/showthread.php?t=4425](http://www.ubuntuforums.org/showthread.php?t=4425)

feel free to experiment but leave most in defaults

---

### Post by ITLogic() on 2004-11-19
Hey spirospr it has been awhile since I've dealt with this problem, but I had a chance to try you suggestion last night. I followed your instructions an VOILA! The video was perfect, no more lines across the screen!  \\:D/ 

Now, can you, or someone else, tell me what I did? I know I changed the video driver from " triden" to "vesa", but what is vesa? I'm assuming it is some standard driver like the "vga" driver in Windows. How did you know to change that?

Also, not only did it fix the video, but it inabled me to have more than just 820x640 resolution. I can now change it to 800x600, which is what I wanted.

Thanks again! :grin:

---

