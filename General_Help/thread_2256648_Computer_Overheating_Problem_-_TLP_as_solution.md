---
title: "Computer Overheating Problem - TLP as solution?"
date: 2014-12-13
forum: General Help
---

### Post by joseph44 on 2014-12-13
Hi, the laptop I'm using right now is pretty old, only has 750 mb of RAM and often will run pretty hot.  its on a cooling pad but thats not much help.  

If I'm watching a video online streaming, it will run hot and loud, overheat, and shut off.  Otherwise, there aren't any probelms.

I read a few other forum posts and did some searching and TPL seems a good way to regulate the settings so that it won't overheat - basically I need to put it in a mode where instead of overheating and shutting down, it simply isn't allowed to run that fast and in turn, I'm sure my performance will go down, but that beats shutting off.

Now, I downloaded TPL and installed it in the terminal as per the instructions, but I'm not sure what I need to do to acheive what I've just described.

Any help would be super excellent!!!

---

### Post by agillator on 2014-12-14
I know nothing of 'TPL', so someone else will have to help you there. However, what you describe sounds suspiciously like a case of old thermal grease. The grease between the cpu and heat sink does get old after a while and does not conduct the heat to the heat sink as it did when it was new. If your machine is two to three years old or older this might well be your problem. It is not a difficult fix. First, if you have never worked on a computer, know nothing about components and so on, take your machine to a repairman. It should be a fifteen or twenty minute procedure if that is the problem. If you know a little about working on the beasts you can probably do it yourself depending upon how your machine is constructed. If you have any doubts or need instructions you are probably better off taking it to a repairman and NOT trying to do it yourself.

---

### Post by mörgæs on 2014-12-14
First I would check if the fan and heatsink are clogged in dust.

---

### Post by Mark Phelps on 2014-12-14
I think folks are missing that the machine is a laptop -- in which case, it's not a simple case of popping off the case cover and blowing the heatsink fins clean.  A lot is involved in disassembling a laptop enough to get to the CPU on the motherboard -- not something someone should attempt who is unfamiliar with working on laptops.  Lots of little screws to get lost and ribbon connectors to get broken.

As to the app, I believe it's "tlp" not "TPL". The link is to some instructions on how to use it: [http://refugeeks.com/use-tlp-to-optimize-the-power-consumption-in-ubuntu/]("http://refugeeks.com/use-tlp-to-optimize-the-power-consumption-in-ubuntu/")

---

### Post by Mike_Walsh on 2014-12-14
Hi, Joseph.

I suspect the others are right; I don't think this is something you can fix, simply by downloading some software & running it. I rather think, from what you have described, that it IS time to 'get your hands dirty'..!

But; I WILL echo what Mark has said. I had my elderly Dell Inspiron apart the other day, to do just exactly this. It's ten years old, the fan was running nearly flat-out all the time.....and the exhaust vent was doing a fair approximation of a hot-air paint stripper. Stripping her down, removing the heatsink & cooling assembly, cleaning everything scrupulously, checking the fan was working properly, then reassembling with new thermal compound, has worked a treat. She runs a LOT cooler now, and the fan hasn't once cut in on high since the overhaul.

I also took the opportunity to perform a CPU upgrade while I was at it.....but that's not in the scope of this thread!

I, personally, have been working with these here 'gadgets' for over 20 years, so I know what I'm doing; the whole job took me about an hour, from start to finish. BUT: there ARE an awful lot of tiny screws (all slightly different lengths, from many locations).....easy to get lost. And the ribbon connectors, and micro plugs, etc., are not easy to remove unless you know just how to do so. If you have ANY experience of doing this kind of work, you may consider attempting this yourself....it's not hard, and just requires careful, step-by-step progress.

Tools I use include a clear plastic organiser, with lots of small compartments.....ideal for those tiny screws; a magnetic pick-up tool, and miniature needle-nose pliers, as well as a large pair of electronics tweezers. Also, a good, insulated, Philips #00 screwdriver.

If you have ANY doubts about your ability to do this, then....DON'T. Take it to somebody who does this kind of thing for a living; and try to 'ask around' a bit, first, and see if they've got a good reputation for doing the work.....there's a LOT of 'cowboys' out there.

Regards,

Mike. ;)

---

### Post by mörgæs on 2014-12-14
Best original poster can do is searching for a disassembly guide on Youtube and judge if it's too complicated or not. 

Sounds like an older model and they are often easier to work with than new ones. Often the fan is made (fairly) easily accessible.

---

### Post by Mike_Walsh on 2014-12-14
> **mörgæs said:**
> 

Sounds like an older model and they are often easier to work with than new ones. Often the fan is made (fairly) easily accessible.

Usually, but not ALWAYS true. The very old Inspirons' fan is ONLY accessible from a nearly complete stripdown. But you're perfectly correct about looking for a stripdown guide, and judging the feasibility of such a project; probably the best way of approaching it.

Regards,

Mike.

---

### Post by QIII on 2014-12-14
I recently refurbished a Dell Latitude D620 with a more powerful CPU, memory, battery, wifi card, drive and also refreshed thermal compound (taking the opportunity to thoroughly clean the heat sink and fan.)  It took a lot of tear down and disassembly.

What is "easy" is definitely dependent on a person's experience.  I tore into the thing with no trepidation.  I also have a suitable work area and proper tools.  One thing I do is create working diagrams as I go to lay out screws and other parts in their relative positions to keep them straight for reassembly.  For others who haven't been elbow deep in electronics guts for 35+ years, it might be a confusing, stressful chore.

I agree that it is best to look up the process and decide if it is something even worth doing.

---

### Post by agillator on 2014-12-15
In my limited experience I have found laptops are designed one of two ways. First, and easiest to work with, is the type where the cpu and heat sink are accessible through the smaller cover that is used to access the hard drive. On these I have been able to fix the cooling problem. The other type has the cpu and heat sink buried somewhere else so you must take off the whole back which can involve almost disassembling the whole machine. That type I leave alone and recommend the non-experienced also leave alone! The other posts here concerning how to tell if you should try are good and wise. Use your best judgement. Oh, whatever you do whether it be to do nothing, try it yourself, or take it to a professional there is a common and vitally important first step: BACK UP ANYTHING YOU CANNOT EASILY REPLACE OR EASILY RECREATE, which means if in doubt back it up!!!!!

---

### Post by joseph44 on 2014-12-15
Thanks guys!  Especially Mike.

I do have a few tech friends who have taken apart and assembled laptops before, so I will see if they can't be of help.  Good to know that TLP (not TPL) probably can't help control this, although I did see some posts about it decreasing the temperature the computer is allowed to get to.

Cheers everybody, I'm new to Ubuntu, but I am LOVING it.

---

### Post by rowdy2 on 2014-12-17
Heyde  I like you am really new with Ubuntu, however I have serviced many laptops.  The advice you have gotten above is excellent.  I only wished to add a few fine points.  Laptops are notorious for this problem due to the extremely confined space to circulate air to ventilate.  Good quality thermal compound will pretty much last longer than the computer, unless it gets too hot.  So you can see that cleaning the dust from the vent system should be a regular preventative maintenance procedure in order to prevent the destruction of your thermal compound and thereby your CPU.  Some manuf. use a thermal sticky pad cause they are handy and actually cheaper, and they are junk.  You can tell if it was because it will have a layer of plastic, usually on the surface of the CPU.  On some units this will leave a space between the CPU and the heatsink (that should not be filled with just thermal compound) after you remove it.  I usually cut a small tab of sheet copper to make up the space with thermal compound on both sides.

And like you I am quickly learning to love Ubuntu.  Enough of gates

---

