---
title: "command for grub"
date: 2006-12-03
forum: General Help
---

### Post by DougieFresh4U on 2006-12-03
can some one please give some command to get me un-stuck at grub. can not boot any thing and cd rom drive is not being recongnized

---

### Post by nixclusive on 2006-12-03
un-stuck? what are you facing there man? Can you provide more information about the situation there?

---

### Post by DougieFresh4U on 2006-12-03
tty no job control. hard drive not recognized, cdrom drive not recognized, list goes on

---

### Post by DougieFresh4U on 2006-12-03
Some one please help

---

### Post by DougieFresh4U on 2006-12-03
I'm getting desparete I need help please as I can not boot my other machine!!!

---

### Post by taurus on 2006-12-03
[http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)

---

### Post by jimbone on 2006-12-03
Is the BIOS not recognizing the hard drive or just grub?

---

### Post by DougieFresh4U on 2006-12-03
It's hard to explain because it doesn't see hardrive or any drives (BIOS) but grub menue shows 4 kernels but can not boot into any of them. I click 'c' for command line and thats where I'm at. If I re-boot  and let it try to boo, it gets to where the ubuntu and the loading bar but nothing happens and thats where it goes to that tty no job control crap!!!

---

### Post by DougieFresh4U on 2006-12-03
Gee, taurus, I'm not a **'Rocket Scientist'**  I went playing with some of those commands and got a lot jibberish, ha ha. One of them was setup some thing or other and came back with 15 sectors embeded. what ever that mean. I think this box is 
**"Trashed"** and I should just relax and take it over to the computer shop tommorow and have a new hardrive or what ever put in. Mean while I will have to settle  with this old other machine I'm using now.

---

### Post by DougieFresh4U on 2006-12-03
what does (initramfs) stand for and if 'job control is off' how do you turn it on? I'm like ready to hang up on thi S.O.B.  :mad: :mad: :mad: :mad: :mad: :mad:

---

### Post by jimbone on 2006-12-03
If it's booting to grub then your hard drive is almost certainly being recognized.  Your cdrom may be as well.

I'm presuming that the computer doesn't respond to booting off a cdrom.  Check your BIOS settings to confirm that the cdrom is the first in the boot order.  You'll need to get booted on a live cd like Knoppix.  Then you'll want to follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=306756")

---

### Post by DougieFresh4U on 2006-12-03
in BIOS it says 'cd rom (not insrtalled)'  when I put cd in the lite comes on and I here the drive 'moving' but computer responds like normal boot up(ignoring cd drive) ](*,)

---

### Post by taurus on 2006-12-03
And didn't you say that the BIOS doesn't even detect your harddrive?

---

### Post by DougieFresh4U on 2006-12-03
this is what it says when machine starts: primary hard disk drive 1 not found: then it says secondary hard disk drive 0 not found: then it says : secondary hard disk drive 1 not found: then it says:Initializing intel boot agent. then :Grub loading stage 1.5, then it flashes to next page with kernel at the top then TRIES to load and goes to that BusyBoxand that /bin/sh: can't access tty; job control turned off  then ends with: (initramfs)_(flashing cursor)    also says : Enter 'help' for a list of built-in commands and that is whyn I keep asking for commands to put!!!!

---

### Post by DougieFresh4U on 2006-12-03
below where it says Booting 'Ubuntu, kernel etc, under the savedefault, I have managed to get some info out of it as follows:: **usplash**: **[B]Setting mode 1024x768 failed**[/B] ::: **usplash: Using mode 800x600**:: **mdam: No devices listed in conf file were found**:: **Target filesystem doesn't have /sbin/init**

---

### Post by DougieFresh4U on 2006-12-04
I need help real BAD, please

---

### Post by jimbone on 2006-12-04
I find it confusing that grub can run when the hard drive is not being recognized.  What drive is grub installed on?

---

### Post by Bigbluecat on 2006-12-04
Try this:

[http://users.bigpond.net.au/hermanzone/p15.htm#cli](http://users.bigpond.net.au/hermanzone/p15.htm#cli)

Herman's guides are extremely useful. I have used them to interrogate the system and manually boot the linux kernels (don't worry - it is not too hard).

Use these when you press "c" at the grub menu. This gives you the grub command line interface. I suspect when you reach the no job erroe you are already beyond grub and something may not be right in you menu.lst (pointing to incorrect disk partition is a possibility).

Follow the step by step instructions. 

Once you have done this you will knwo exactly how grub names the disk partitions and where you kernels are. 

One in we can restore grub to the MBR.

No idea why you can't boot CDROM though

---

