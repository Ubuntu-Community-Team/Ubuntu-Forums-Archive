---
title: "How well does upgrading from Dapper to Edgy work?"
date: 2006-10-26
forum: General Help
---

### Post by SolidAndShade on 2006-10-26
I'd like to update my system to Edgy via synaptic, but I'm reluctant since my attempt to update from Breezy to Dapper hosed the system and forced me to reinstall from the Dapper CD. How many here have been successful updating via the repositories? Are there any things I should watch out for? I turned off all my third-party repositories, so those shouldn't be a problem. Thanks.

---

### Post by floibler on 2006-10-26
Well I'm still trying to get Edgy Working 4 hours after upgrade due to x server problem - wish I hadn't bothered now.

---

### Post by bsussman on 2006-10-26
> **SolidAndShade said:**
> I'd like to update my system to Edgy via synaptic, but I'm reluctant since my attempt to update from Breezy to Dapper hosed the system and forced me to reinstall from the Dapper CD. How many here have been successful updating via the repositories? Are there any things I should watch out for? I turned off all my third-party repositories, so those shouldn't be a problem. Thanks.

I did a dist upgrade some time around knot2 and everything worked totally without incident.

So, if you do a total backup of everthing you care about, just in case, and you are fortunate like me, you should be fine.

But that process was on my laptop which I keep pretty vanilla.

When I do my desktops, I will probably install from scratch and move things over, since my desktops started as 5.something, upgraded all the way through to 6.06 and I feel it is time for a garbage cleanup, which means from scratch for me.  Most importantly, I will hand move configs in my home, since I am sure some of the little annoyances I have are due to my not knowing stuff then that I do now :mrgreen:

---

### Post by T.Louis on 2006-10-26
The single problem I had was that gnome didn't fire up. I just fetched the offical ATI drivers, installed them, and haven't really had a problem since.

---

### Post by floibler on 2006-10-26
I have had to install vesa driver to get it to work

But now can only log in in failsafe

i'm currently downloading cd imagine to do clean install if that doesn't work i'm going back to dapper - luckily everything is backed up or on my network.

floi

---

### Post by PriceChild on 2006-10-26
Most will work... however many won't.

Backup ALL data just incase :)

Remember that there are many equal reasons to stay in Dapper.

---

### Post by Circus-Killer on 2006-10-26
i had only one tiny problem, and that was that ati doesnt support composite. but after disabling composite, i had no problems.

been a smooth ride ever since. :cool:

---

### Post by neuropsychguy on 2006-10-26
I did an upgrade yesterday and it worked flawlessly (on a Dell E1505). However, I decided to do a clean install today just to start out fresh just for fun.

---

### Post by serion on 2006-10-26
I upgraded off the alt-install RC disc, and it effing went ahead and installed KDE!  ](*,) 
Took me a few hours to download what I thought was updates, then bam! A blue desktop.  I don't know why or how, but that made me pretty mad....

---

### Post by Circus-Killer on 2006-10-26
lol, sounds like you upgraded to kubuntu 6.10 :twisted:

---

### Post by floibler on 2006-10-26
The saga continues ..

I managed to fix the problem I had that would only let me log on in failsafe - it was to do with keymotion and my linux cherry keyboard - but I was having to run on vesa as the nvidia driver did not work for my card (geoforce2 mx400).  I tried the cd (video worked) but wouldn't install - so i'm now re-installing dapper.

I'm sure edgy works for some, i'd guess it particularly does if you 've got a pretty simply set-up and well supported hardware.  But after a day of frustration I need my PC back (I better do some work this week) so I'm sticking with Dapper for now - which is a shame, I was looking forward to Edgy.

Floi

---

### Post by Paradoxdruid on 2006-10-26
Well...  I have two different computers running vanilla Kubuntu 6.04, and so far both have failed spectatularly mid-upgrade (you can see the thread [here]("http://ubuntuforums.org/showthread.php?t=285176")).

So, maybe wait a few days for issues to get sorted out (I'm glad these aren't critical computers).

---

### Post by Circus-Killer on 2006-10-27
> **floibler said:**
> The saga continues ..

I managed to fix the problem I had that would only let me log on in failsafe - it was to do with keymotion and my linux cherry keyboard - but I was having to run on vesa as the nvidia driver did not work for my card (geoforce2 mx400).  I tried the cd (video worked) but wouldn't install - so i'm now re-installing dapper.

I'm sure edgy works for some, i'd guess it particularly does if you 've got a pretty simply set-up and well supported hardware.  But after a day of frustration I need my PC back (I better do some work this week) so I'm sticking with Dapper for now - which is a shame, I was looking forward to Edgy.

Floi

sounds like you weren't using the beta nvidia drivers with composite support. as far as i know, if you using the current stable nvidia drivers, you also need to disable composite.

---

### Post by louistan3 on 2006-10-27
i upgraded from dapper to the last edgy RC.. i thnk about 7 days ago... before the final release.. and it went good.. just had an X problem.. but i just needed to do a reconfigure.. and thats it.. then i just had to DL a few when the final was released.. 

i have a sony vaio SZ.. :D

---

### Post by floibler on 2006-10-27
> **Circus-Killer said:**
> sounds like you weren't using the beta nvidia drivers with composite support. as far as i know, if you using the current stable nvidia drivers, you also need to disable composite.

Ohhhhhh!

Just as I was getting used to the idea that I wouldn't be using Edgy for a while (and have reinstalled Dapper) a susgestion that I'm just going to have to try! :mrgreen: 

Its a shame it doesn't just work 'out-of-the-box' though must put a lot of people off.

](*,) 

floi

---

### Post by floibler on 2006-10-27
:confused: 

Riddle me this ...

How come live CD works fine - including using nv xserver driver, but when I do install then x crashes - surely this is the same driver (and not the beta one) or does teh live CD do something different.

I'm typing this from Edgy live.

floi

---

### Post by lonce on 2006-10-27
I prefer a fresh install.  Its just a habit from my windows days.  The update never runs as good in my opinion as a fresh install.  It literally installed on my pc in under 20 minutes.  20 mintes later automatix2 had everything installed.

---

### Post by Boyo on 2006-10-27
I am not a newbie to Linux, coming and going since Red Hat 6.  I came to Ubuntu shortly after 5.10 was released.  I really struggled to get Linux working as I wanted and spent most of my time booting into Windows.  

With the release of 6.06 things looked up, the upgrade was flawless, wireless worked with Ndiswrapper and more importantly Firefox didn't crash for no reason!

I was really looking forward to Edgy and took the upgrade plunge at Knot 3.  This was a Big Mistake, Firefox went back to crashing out and while Network manager could see my WPA network it would not connect.

Following the final release of Edgy I did a clean install.  Wireless is still not working properly, sometimes it will connect, sometimes it will connect and for no reason stop working and sometimes I need to get out the CAT5 as the wireless is dead!

My current plan for Ubuntu is to reinstall 6.06 over the weekend as, for me, the advantages of a faster start are greatly outweighed by the fact wireless just works!!

I have a standard out of the box Dell Inspiron 5150 laptop.  Brodcom BCM4603 wireless chipset.

------------------------------------------------------------------------------------

Torchwood Rocks!
"CSI: Cardiff, that's what I'd like to see. We would be measuring the velocity of a kipper."

---

