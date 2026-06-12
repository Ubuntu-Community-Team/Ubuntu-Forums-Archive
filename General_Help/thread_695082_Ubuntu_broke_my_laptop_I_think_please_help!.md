---
title: "Ubuntu broke my laptop I think please help!"
date: 2008-02-12
forum: General Help
---

### Post by jcresswell on 2008-02-12
I have a custom built Aeoncraft laptop. I was running windows media center on it fine and decided to play with linux since I have not in years. I downloaded the Ubuntu CD and booted into live mode. My laptop worked fine with it so I hit install and it installed fine with no errors. When my laptop booted up it shows the boot screen where I can hit DEL to enter BIOS and what not and then goes blank. I tried rebooting many times and it did nothing. I then put the Ubuntu CD back in and it would not boot from it so I checked my BIOS and it was set to boot from CD. I then put a windows xp pro CD and a windows media center CD in and it will not boot from anything. I can not use linux or reinstall anything else and I use this for school and need it up and running badly Linux or Windows it does not matter I just need it to work.

---

### Post by jcresswell on 2008-02-12
I have a custom built Aeoncraft laptop. I was running windows media center on it fine and decided to play with linux since I have not in years. I downloaded the Ubuntu CD and booted into live mode. My laptop worked fine with it so I hit install and it installed fine with no errors. When my laptop booted up it shows the boot screen where I can hit DEL to enter BIOS and what not and then goes blank. I tried rebooting many times and it did nothing. I then put the Ubuntu CD back in and it would not boot from it so I checked my BIOS and it was set to boot from CD. I then put a windows xp pro CD and a windows media center CD in and it will not boot from anything. I can not use linux or reinstall anything else and I use this for school and need it up and running badly Linux or Windows it does not matter I just need it to work.

---

### Post by jcresswell on 2008-02-12
I have a custom built Aeoncraft laptop. I was running windows media center on it fine and decided to play with linux since I have not in years. I downloaded the Ubuntu CD and booted into live mode. My laptop worked fine with it so I hit install and it installed fine with no errors. When my laptop booted up it shows the boot screen where I can hit DEL to enter BIOS and what not and then goes blank. I tried rebooting many times and it did nothing. I then put the Ubuntu CD back in and it would not boot from it so I checked my BIOS and it was set to boot from CD. I then put a windows xp pro CD and a windows media center CD in and it will not boot from anything. I can not use linux or reinstall anything else and I use this for school and need it up and running badly Linux or Windows it does not matter I just need it to work.

---

### Post by nutts4life on 2008-02-12
What does you boot list look like?

I assume the first one is CD what is the second and third?

nutts4life

---

### Post by jcresswell on 2008-02-12
first is CD/DVD
second is HDD
third is Realtek network card

---

### Post by nutts4life on 2008-02-12
Make two and three blank and just have the CD.
Do either of the CD's boot?
If not, then set the first one to hdd (nothing for 2 and 3). does this boot?

If not, when the PC starts does the hdd or the cd drive spin? (you should be able to tell by the noise)

---

### Post by jcresswell on 2008-02-12
I made the next 2 blank. When it turns on the cd light will flash once and then that is it and the hardrive is spinning and it does sound like it is running normally when it goes to the blank screen

---

### Post by jcresswell on 2008-02-12
now the laptop wont even turn off.

---

### Post by smartboyathome on 2008-02-12
Try waiting a few minutes. I find sometimes it takes a long while to start booting.

---

### Post by Pumalite on 2008-02-12
Use Super Grub to fix your XP MBR:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by nutts4life on 2008-02-12
Ok,
Your laptop will turn off, just keep your finger on the power button and it will turn off eventually.
What is the make and model of your laptop?
Have you tried setting the first boot to JUST the HDD?

---

### Post by jcresswell on 2008-02-12
I let it set for 15 minutes and also it wont give me the press any key to boot form CD

---

### Post by jcresswell on 2008-02-12
will try that next. it is custom built from aeoncraft it has a AM2 dual core processor a SATA HD, 2 gigs of corsair ram, and a Nvidia 7600go

---

### Post by jcresswell on 2008-02-13
I put the Ubuntu live cd in my laptop to make sure that everything was compatable. It ran fine so I decided to go with the install. It installed fine, but after the first boot I got a blank screen and it stayed there forever. I looked up on line and apparently my MSI motherboard on my laptop has that problem the MS-61331. So I decided no big deal I will put windows back on. I tried 3 legal windows CDs and none of them would boot from CD. I checked my BIOS and it was set to boot from CD so I reset my BIOS and set it back up and nothing. I was thinking that maybe it was possible that my CD/DVD drive went out at the same time so I took 2 friends laptops and put their drives in my laptop and I still do not get the option to boot from CD. Also my drive works in their laptops. Somehow something on the Ubuntu install changed something and I cannot boot from CD. Anyone know anyway around this so I can have Linux or Windows on my laptop again I need it for school.

---

### Post by skymera on 2008-02-13
i dont think ubuntu had anything to do with why your CD's will no longer boot.

why didnt you dual boot incase something like this happened?

---

### Post by jcresswell on 2008-02-13
I know 3 people that was running Ubuntu on their laptops off the same CD so I did not forsee there being a problem. I know it sounds weird what I said about Linux killing it, but I did not know if it did something to the bootloader or if it set something to slave or what. I mean I installed something off a disk that day, I ran Ubuntu live off a disk that day. I booted off of CD that day to install Ubuntu and then it did not work and I tried two additional optical drives and none worked. I know my friends optical drives work and mine worked on his laptop I just cant boot on mine.

---

### Post by p_quarles on 2008-02-13
I've merged your duplicate threads. Please do not cross-post the same question in multiple threads.

---

### Post by jcresswell on 2008-02-13
that would be fine except for I am not dual booting. When I did the install I told it to use the whole harddrive which whiped it and put Ubuntu on it. But I get the blank screen that is apparently common on a MS-61331 MB on a laptop. The main problem is since I have installed linux I cannot boot from a CD anymore no matter what my BIOS says. I met up with some friends today and put there working optical drives in my laptop and I cannot boot from CD with their drives but my drive will work on theris. ever since the Linux install it seems like something is blocking my ability to boot from CD rom to reinstall windows or Linux I just need it working.

---

### Post by Herman on 2008-02-13
In a simple electrical circuit there are things that can go wrong.
A light bulb can burn out, a fuse can blow, a switch can become dirty and not close properly, a wire can short out or break. A battery can run out of charge. These are some of the things we expect to happen sooner or later in a simple electric circuit.
Computers are far more complex and yet we take it for granted that they work so reliably and next we begin to assume they will work forever.

Humans have not yet invented anything that will work forever. There is no substance known to science that I'm aware of that's indestructable except energy itself.
The fact is, computer parts can fail randomly, regardless of what you happen to be doing at the time of the failure.

Of course. materials, design and manufacturing all play an important role. There can be good quality PC parts and poor quality parts, and even parts made with the best care and attention can have problems.

I have two identical desktop  PCs here. both the same age. They both have a problem with the motherboard not powering the CPU fan and case fan. Both developed the problem at around the same age. There are no puffed out capacitors or any other visible signs of deterioration. Probably it's just a weakness in the design. It wouldn't matter what software I was using.

I hope it doesn't turn out that you need a new motherboard, I hope you can fix it by finding some setting in your BIOS that you can fix without spending any money.  Sometimes though, things just break and we have to accept that fact and learn to live with it. 

Regards, Herman

---

