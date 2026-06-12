---
title: "Almost given up now!!"
date: 2008-04-17
forum: General Help
---

### Post by dan0z on 2008-04-17
Morning all,

I have recently decided to dual boot ubuntu with vista on my main pc, as vista was making me very stressed, and breaking USB flash drives and mp3 players (Vista is crap!). Anyways my little rant done, im now having loads of troubles with Ubuntu, first off I should point out that i have Ubuntu running on an old machine and i never had any problems with that (touches wood). As i put it on my main PC i decided to have a go with compiz and try and make it all look flash, all was fine until then... now i cant use a resolution over 800x600 (yes i know loads of other posts about this problem) i have tryed all the usual suspects to get this to work properly, but it either boots up with no bigger than 800x600 or it boots up and my monitor just displays the text "cannot display this resolution" (or something similar). I have tried all the different backup xorg.conf files within the folder but just always get one of the two outcomes, im hoping one of you bright sparks will be able to help me fix that with ease... 

Next problem... and quite likley related to the first.

Resolution again, this time this has happened right from the word go, anytime i try to play a game (ones i have tryed: red alert2, CS 1.6) It opens the game but again my monitor just displays the text "cannot display this resolution" and i have to then reboot (have not tryed just restarting X, that may work tho.) One of the other main reasons to put Ubuntu on my machine was the lack of IPX in vista. All hail to the clever guy at microsoft who woke up from his desk one day and thought.... hmm.... i know how i could piss a load of people off.... lets stop them being able to paly LOADS of games on LAN!!! Yeah lets just remove the whole protocal!  The more amaizing thing is that once this guy had come up with the great idea, ssomeone actually agreed!! What were they thinking that day :/

Now i would like to say, if the quickest way to get back to the norm is to just wipe it off and start again, I will. But i have a LAN to attened on saturday where Red Alert 2 is gonna be played so im relying on good old Ubuntu to allow me to play with everyone. I also want to get all the desktop effects working, i dont care if i have to rebuild my machine four times (already been done once) I want it working (surely it cant be that hard...???).

Specs:
Pentium D 930 
2 Gb RAM
ATI Radeon x1300
(all you need to know?)

So... by now you either think im a mad man or just plain crazy, either way i would really appreiate some help on any of my problems.


Thanks All

D

---

### Post by Zorael on 2008-04-17
Could you post the contents of your xorg.conf? (you seem to know where it is. **/etc/X11/xorg.conf**)

---

### Post by Nunu on 2008-04-17
> **Zorael said:**
> Could you post the contents of your xorg.conf? (you seem to know where it is. **/etc/X11/xorg.conf**)

Sounds to me like xorg just might need to bee reconfigured.

---

### Post by dan0z on 2008-04-17
Hey, 

Thanks for your quikc reply, sadly im at work and for some unknown reason i cant seem to connect to my home PC :/ Therefore i cannot paste the file, I should hopefully be able to get it on here within the next hour.

Thanks again.

Dan

---

### Post by zvacet on 2008-04-17
Did you tried [this?]("https://help.ubuntu.com/community/FixVideoResolutionHowto") Or type in terminal 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and select **vesa** driver.Aftr that you can go search driver for your video card.

---

### Post by dan0z on 2008-04-17
Lost count how many times i have tryed that... sadly it either makes no difference or make's it so that the res is too high for my monitor. The only thing i do notice is it stops it using the restricted driver for my Gfx card, but even if i turn it back on and reboot, still the 800x600 :(

[EDIT] Missed the link in your post, will try running through that page as soon as i get home [/EDIT]


D

---

### Post by Zorael on 2008-04-17
> **Nunu said:**
> Sounds to me like xorg just might need to bee reconfigured.

Perhaps, but if it's a resolution issue, would it help? Knowing the contents we should be able to tell.

Modelines have wreaked havoc before. Won't reconfiguring it make it poll the monitor again and generate the exact same modes?

---

### Post by Woody1987 on 2008-04-17
What graphics cards do you have? go to administration->restricted drivers manger and make sure its enabled. If its nvidia open a terminal ad type 

```
sudo nvidia-settings
```

You should be able to set the resolution in there and update the xorg.conf automatically. If your using an ATI card there will probably be a similar app for it too, and if its intel then i dont believe there is a gui for setting it but you should be able to by manually editing the xorg.conf.

---

### Post by kelvin spratt on 2008-04-17
I think you need to remove the resticted drivers totally by purging them
and install the latest ATI drivers. The ATI card you are using works really well with the proper ATI drivers at least for me.

---

### Post by dan0z on 2008-04-18
Sorry for the late reply everyone,

Very greatfull for all your help, just to add.... tried booting this morning (have touched nothing so far) and not only can i not see anything but the unsuported resolution thing on my monitor, but pressing ctrl+alt+F1 or F2... dont work. I would normally then edit the needed files from within windows, but now when i mount the ext partitions, then try and open them, windows just wants to format them :/

Looks like i may just have to start again, this time tho, maybe someone here could help as I dont have much time and would like to get it all working: red alert 2 (for the LAN tomorrow) and compiz-fusion, but i think if i tried with no help i would be looking at about 5 hours or something stupid.

Kelvin - I thought the restricted driver's Ubuntu installs where the best one's you could get lol! Are ATI actually making linux drivers now then?

Thanks all!

Dan

---

### Post by finferflu on 2008-04-18
You can still use the LiveCD to boot into your install. From there you can access and manually edit the Xorg settings.

---

### Post by dan0z on 2008-04-18
Well, i assume that the partitions will still be ok :/ 

Up until today i could read them fine in wondows but now i cant :/

I have tried over and over again to edit the xorg.conf file... either im doing something wrong or it just will not work.

It takes.... maybe 15mins to install Ubuntu, maybe it would just be so much easier to just do that, then i can just get help with installing compiz-fusion (i want more effects not just the one's that come with Ubuntu) that was what started most if this in the first place, trying to get that to work. A search on google brings up loads of pages all with completley different guide telling you to do completeley different things to enevertably produce the same outcome.

So now i suppose my querstions to all of you would be...

1. Is compiz really that hard to get setup and working without messing things up?? (if so, could you advise the best way of going about this?)

2. Should my computer be upto the task of all the fancie effects? (i know its getting a bit old now, am planning on replacing soon ;))

3. Kelvis earlyer post suggested not to use the restriced drivers Ubuntu suggest and use ATI one's, would you also suggest this? are they stable?

4. Is it better to install the 64bit opperating system?? Would it make my life easier or harder??

Thanks

D

---

### Post by dougleduck on 2008-04-18
Sounds like a problem I've had before.

I found the link [here]("http://www.geocities.com/randomnumbergenerator2001/xorg.conf.breezy.txt") useful I think I basically removed all the other resolutions from xorg.conf and just left the relevant one).

I think it would be helpful if you could attach your copy of xorg.conf

---

### Post by dan0z on 2008-04-18
Sadly as stated in an earlier post, i cant get to the file atm. Im at work currently and alothough im connected to my home machine, vista is loaded atm, and i cant seem to access my ext partitions atm. As soon as i finnish work i shall boot the live Cd then post the file.

Dan

---

