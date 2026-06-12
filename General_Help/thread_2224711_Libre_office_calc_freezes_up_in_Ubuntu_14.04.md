---
title: "Libre office calc freezes up in Ubuntu 14.04"
date: 2014-05-17
forum: General Help
---

### Post by paulravin on 2014-05-17
Hi, I am having trouble with Libre office calc, it freezes up. 

 

 I am saving after every action to get work done, it reminds me of early windows. Probably just not a very powerfull program but maybe there is a way to stop it freezing up?  
 My last computer running Ubuntu 12 did not have this issue with the same files.
 

 Any help much appreciated!!

---

### Post by sanderj on 2014-05-18
It freezes up? I would run memtest86 from the GRUB boot menu and keep it running for a few hours.

---

### Post by paulravin on 2014-05-19
[COLOR=#1f497d][FONT=Calibri, sans-serif][SIZE=2]Hi,[/SIZE][/FONT][/COLOR]
 [COLOR=#1f497d][FONT=Calibri, sans-serif][SIZE=2]Thanks for the tip, I do not know much if any computer jargon... To run memtest86 do I restart the computer and get it running in a different mode? Use termenal?[/SIZE][/FONT][/COLOR]

---

### Post by sanderj on 2014-05-20
Yes, in the GRUB-boot-menu, where you see Ubuntu (and maybe Windows), select Memtest86

Example boot menu: [http://i.stack.imgur.com/Kmcq8.png]("http://i.stack.imgur.com/Kmcq8.png")

---

### Post by HermanAB on 2014-05-20
Do yourself a favour and install gnumeric.  It works a helluvalot better than calc.

---

### Post by paulravin on 2014-05-20
I will give it a go, thanks for the tip.

---

### Post by paulravin on 2014-05-20
> Yes, in the GRUB-boot-menu, where you see Ubuntu (and maybe Windows), select Memtest86


I am trying to get to this screen on start up, have tried about 10 times, what appears to be it comes up for about 1/3 of a second. When I press F2 on start up it goes to a disk check and memory check option which I have run and of course comes up all ok. How do I get to that screen?

---

### Post by vasa1 on 2014-05-20
> **HermanAB said:**
> Do yourself a favour and install gnumeric.  It works a helluvalot better than calc.

I'm having similar problems with Calc. I don't think that memory is an issue. (It may be but other programs run fine.)

I tried gnumeric but I found it a bit difficult to understand and customize. I might give it a try again. 
If you know of a non-nerdy resource to help one move from LiboCalc to gnumeric, that would be most appreciated.
Or even that kingsoft thing.

Edit: 
kingsoft is 32-bit; it maybe possible to install on a 64-bit system but I don't want to try that.
Installed gnumeric and it's fine (for now). It easily manages the same document that Calc gags on.

---

### Post by paulravin on 2014-05-29
Follow up on my multiple posts with all of the issues with this machine. I had about 6 problems with the HP pavilion split, 2 were solved, then the keyboard stopped working and HP refunded my cash. Go HP for customer support, they did not support using Ubuntu and also did not use it as an excuse for a keyboard that would not even work in Bios.  
 

 I have now bought an Acer Aspire V7-582p, it is listed as compatible with ubuntu, runs on live CD no problem. Loaded it up and no screen. So am now a week into trying to solve it via forums with no success, am now looking for tech support for it or lap top shop with pre loaded Ubuntu in Australia that is not double the cost. Sound easy? Try it. It is getting to the point of back to windows, never had issues like this in 4 years of using Ubuntu, 14.04 compatibility with laptops seems to have gone down hill big time!
 

 Motto of my experience:
 

 * Running live cd does not mean it will work on that machine after install. You are taking on a complete gamble.
 * Forum post that a machine works with Ubuntu does not mean it will for me. (I am not stupid with computers but I am not a programmer)
 * Finding payed help with Ubuntu is near non existent.
 * Buying a new Ubuntu pre loaded laptop is near non existent in Australia, I found one shop with computers at 2 x the price. Maybe that just is the price of something that works?

Follow up for posterity.
 

 Everything on this Acer V7 now works. It took me 1 week of half days, communication with _5 different tech support / linux savy people_, lots of trawling the web, posting messages etc to get the screen working.  
 

 Fixed now (by installing on Legacy not UEFI, see other post) just so releaved to not have to go back to the continual headache that is windows. Thank you Acer tech support, credit where credit is due, the guys at Acer 'out of scope' technical support (From Australia 1800 144 519) worked out why my screen would not work and how to fix it in 10 min. They charge $75 and it was worth every cent.  
 

 When trying to fix a HP I also found the best and fastest way to solve problems was HP tech support threats of warranty voiding bla bla but they fixed my computer issues where no one else could.

---

