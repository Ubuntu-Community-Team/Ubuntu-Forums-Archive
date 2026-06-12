---
title: "Strange Hard Drive Problem"
date: 2007-07-14
forum: General Help
---

### Post by Shawn Dineley on 2007-07-14
Hello

      I been running into a strange problem with hard drives in one of my systems. I have two systems running ubuntu Edgy (6.10). The first is my main system in my bedroom. Never have had any problems with it. Second system as a htpc setup on my living room tv. This is the one giving me problems.  I bought it about 6 months ago. From old hardware I had laying around. It's a p3 800 mhz, 256mb ram. Geforce 4 mx400 video card with tv out. At first I had a 8 gb hard drive in it. With all the media being served by my main system. Well I went to start it up one day and it wouldn't even get to grub. I tried repairing grub and doing a bunch of searches on the fourm but I couldn't get it going again. So I went and got a 160 gb drive. Reinstalle everything. And it's been running fine for about 3 months. In till yesterday. While I was at work the power went out for a second. When I got home all my system were off. So I went around turning them all back on. All but the htpc started without a problem. It just hung at the ubuntu boot screen. So I restart and selected recovery from the grub menu. It said it could find the partition table, and a kernal panic then stopped. So I tried a couple of things, nothing worked. So I removed the hard drive and put it in my main system. And it boots right up, no problems. Everything is right where it should be. Hell I'm using it right now to type this. But while I put it back in the htpc it comes up with the same errors.

        I know this is alittle long, Sorry. But does anyone know whats going on here? 

       thanks

---

### Post by louieb on 2007-07-14
Well it sure sounds like a hardware problem. The first thing I would look at is the power supply. Checking the voltage not always reliable. Best to try a spare.

---

### Post by davidjmayo on 2007-07-14
I know you said you tried a couple of things. To state the obvious did you try bedroom HD in the htpc

The HD from htps works as you did that already. 
Now where is the problem? Power supply as suggested already or motherboard in htpc?

tried resetting the RAM just in case?

(Please don't ask me any more ideas I hate hardware issues)

---

### Post by smoker on 2007-07-14
hi, a dicky power supply can cause a lot of problems, so always worth a check. i would also try a memtest, let it run for a while,

if your hard drive is ide, try it on another ide channel and see if it works ok there. if sata, try it on another sata connection,

best of luck

---

### Post by Shawn Dineley on 2007-07-15
Well I guess it was a buggy power supply. After I switch it out with another I had laying around all is good again. Thanks to everyone for the help.

---

