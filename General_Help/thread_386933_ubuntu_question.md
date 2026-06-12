---
title: "ubuntu question"
date: 2007-03-17
forum: General Help
---

### Post by cessna_89702 on 2007-03-17
Hey I have been running Ubuntu for a while now and its great but if I turn my computer off to reboot after an update or something it usally wont turn on the first time. I usally have to keep trying to boot over and over until finally it goes. After the Ubuntu screen that says loading and all that stuff it switchs to a black screen usally without a white line blinking at the top left but when the lines blinking it boots easily. It says PCMIA services not found or something, could that be a problem or is their some sort of problem in the boot loader thing?

---

### Post by peabody on 2007-03-17
Try this: when booting, as soon as the Ubuntu splash screen comes up, press Alt+F1.  That should take you to a text screen which will show you the details of the boot up process.  If this process gets stuck, try writing down what's on the screen and posting it here.  Sometimes network services stall during boot up if the internet is flaky, or your DNS service is slow.

---

### Post by cessna_89702 on 2007-03-17
I ran it in a text mode and the very beginning when it starts is says BIOS BUG then it has some number then continues to attempt a boot but right now it wont boot up. So usally it boots after tons of trys. Is this Bios Bug important??

---

### Post by peabody on 2007-03-17
Potentially.  Could you write more details down as well as post your hardware specs (make manufacturer of computer, or motherboard, etc.).

---

### Post by cessna_89702 on 2007-03-17
PCI:BIOS BUG #811494350241
     And I think theres other numbers before PCI to the left,
I have a hp dv9000 not sure on the exact model but it has two amd turion 64 processors. This is a new computer.

---

### Post by mgmiller on 2007-03-17
It could be a PCI bus mastering issue.  Try removing all PCI or PCI-e cards from the computer with the exception of the video card and try rebooting.  If it works, add the cards back in one at a time to see which is causing the hang.  I have a USB/Firewire card that does this to me and I have to remove and reinsert the card almost every time I reboot.  Luckily, I leave my machine on 24/7 so it doesn't affect me too often.

---

### Post by darksong on 2007-03-17
This could potentialy be a hardware fault if it is a new computer - does the live cd run? if not you could have a faulty mother board, or processors. If you have no vitail information try a re-install, it could be faster and easier than typing line apon line of code to getting the system running again. 

If that doesn't work your install disks could have some curropt data - which is highly unlikley, try installing another distro - if that don't work you most likely have faulty hardware,

---

### Post by peabody on 2007-03-17
This thread seems to talk about your particular computer:

[http://www.ubuntuforums.org/showthread.php?p=2219340](http://www.ubuntuforums.org/showthread.php?p=2219340)

---

### Post by cessna_89702 on 2007-03-17
I really doubt theres a faulty motherboard or anything like that.
Yea I try not to shutdown because I know that usally will happen. What exactly is a PCI card?

---

### Post by mgmiller on 2007-03-17
Inside on the motherboard, there are expansion slots that can contain add-in cards that add more functions.  They are usually optional like a better sound card or extra USB/firewire ports, modems, network cards, tv tuner cards, etc.  The newest mobos use an interface called PCI express or PCI-e, the slightly older boards use PCI, but the trouble shooting is the same.  Remove all the cards except for video and try rebooting.  If it works OK, add one board back at a time and reboot until you find the one causing the problem.  Make sure you have grounded yourself to the case and turn off the power at the power supply rocker switch on the back of the machine  before removing or adding cards.  Also, make note of which slots they came from so you can put them back in the same spot.

That being said, many modern mobos have all the extra devices built in, so you may not have anything in the slots.  If that's the case, this trouble shooting howto won't help you.

You can tell from the outside if anything has been added, as the row of expansion slot covers will have some replaced by the backs of the cards with various connectors.

---

### Post by cessna_89702 on 2007-03-17
I just tried that, it didnt work but thanks for trying to help

---

### Post by cessna_89702 on 2007-03-18
pretty sure it isnt a pcmia problem but I read that other post and they said to download the 64 bit disk. I didnt download that one...Could that be whats causing the issues??

---

### Post by peabody on 2007-03-18
You should, to get the full advantage of your hardware.  I can't promise it'll fix the problems.

---

### Post by cessna_89702 on 2007-03-18
Well I think I will update to 6.10 using a edgy 64 bit disk. Anyone have a link for something liek that or is that even possible

---

### Post by mgmiller on 2007-03-18
Because the 64 bit is a different architecture, you can't upgrade to it.  It would require a fresh install.  If you have some original data in your /home directory, you should back it up first.

---

### Post by cessna_89702 on 2007-03-18
I think later today I will probably back up my data & do a install of the 64 bit Edgy, but do you really think that would be the problem??
I ran Edgy on this computer before and it wouldnt boot up but it wasnt the 64 bit and does anyone have a iso burner for ubuntu

---

### Post by peabody on 2007-03-18
you should be able to burn isos in gnome by right clicking on them.  If that doesn't work, K3B is a great cd burner.

---

### Post by mgmiller on 2007-03-18
> I think later today I will probably back up my data & do a install of the 64 bit Edgy, but do you really think that would be the problem??

Usually, the 32 bit version works just fine with 64 bit CPU's, but you never know, there could be something in the 64 bit kernel that gives better support for your hardware.  What happens when you boot off the 32 bit live CD?  Do you still get the lockup?  If you do, then see if the 64 bit Live CD boots without problems.  Maybe that can give you a clue.

---

