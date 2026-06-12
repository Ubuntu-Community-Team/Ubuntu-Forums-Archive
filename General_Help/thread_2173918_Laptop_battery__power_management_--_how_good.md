---
title: "Laptop battery / power management -- how good?"
date: 2013-09-11
forum: General Help
---

### Post by Coder88 on 2013-09-11
How good is Ubuntu at managing laptop battery power, compared to Windows 7? I have an ultranotebook with long battery life, important for writing out and about. I am thinking of just making it an Ubuntu laptop, but I would hate to lose too much battery life if Ubuntu is not good at managing the battery. Any feedback, thoughts, advice on this?

---

### Post by mastablasta on 2013-09-12
well there are some additional programmes such as tlp ([http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html)) that will help manage battery really good. but i guess it also depends on how well hardware is supported i guess. 

at first i thoguht it uses more battery on my average use. then i calculated (Kubutnu shows battery power drain in percentages) a bit. and realised that if there is a difference it is a small one. perhaps 30 min compared to windows. in windows the battery lasts abotu 7h - 7h 30min, while in linux it was about 6h 30-7h. i only calculated the use based on 1 hour work & battery drain.  i might install tlp later on if i need it.

otherwise screen gets dimmer automaticly when i don't work for a while. hibernation, suspend seems to work on in 13.04 on this hardware. i just hope the same will be true in 14.04 LTS.

i am not convinced that power management is as good as in windows 7 but it it preety good i guess. again it iwll depend on hardware. if oyu already have it installed you can give it a try and see what happens. you could use a battery test programme to compare.

---

### Post by QIII on 2013-09-12
Something else to consider is that proprietary graphics drivers are often much better in this area than the open source drivers at power management.

This is problematic, however, with hybrid graphics arrangements (Intel/ATI or Intel/NVIDIA) in the Linux world.  Unfortunately, the OEMs have left us in a difficult position at the moment.

---

### Post by DJonsson2008 on 2013-09-12
Will disabling uneeded services such as sound, and wifi significantly extend battery life?

---

### Post by su:bhatta on 2013-09-12
The use of Fglrx in my case gives me same if not better battery life in Ubuntu/Debian. Running Windows 8, I have seen that battery left was for 1hour 5 mins and when rebooted to Ubuntu the battery showed to last for 1 hour 13 mins... This happened a week back to me. But then again, I dont have an Ultrabook, but a plain laptop.

the open source drivers in my case consumes battery like anything, a full charge barely lasts for an hour, but I have AMD processor & GPU, it should be different for Intel based chips, which I understand have far better openSource drivers.

Also, DJonsson2008: Sound I don't know about, but I used to regularly shut off my Bluetooth to conserve battery, but found out doing that actually gives me only 10-15 mins extra.
Mastablasta gave a good link, am looking into it now, thanks for sharing that.

Coder88, Guess you'll have to try out and see with your specific hardware.

---

### Post by Coder88 on 2013-09-12
> **bhattabhishek said:**
> ...
Coder88, Guess you'll have to try out and see with your specific hardware.

Well that is the problem-- to try out linux on my laptop means i would have to destroy the laptop's raid0 and windows7, then install linux and see what happens. i do have rescue discs to restore if it goes bad or if i don't like the battery life from linux. But it is not so easy as installing ubuntu to a partition on the laptop, that is not doable (I have another thread on that). so i am in a place of indecision, I would like to try all linux on the laptop, just not go through all that work if i know beforehand that battery life would suck in so doing. but it sounds like it might be worth a try, i just might pull the trigger today and do it.

---

### Post by DJonsson2008 on 2013-09-12
With Windows XP home I was easily getting 6-8 hours on my Aspire one Atom Intel machine with a 6 cell battery.
Presently with a 95% battery charge the battery icon in Xubuntu is telling me 5 hours left.  If the Battery panel
is reporting correctly this seems that the margin was better with XP Home.

Given though the tweakabilty of Ubuntu/Xubuntu I'm curious what can be done to increase battery life if anything.

Would Lubuntu be easier on power?
Can CPU speed be limited to draw less power?
Can services be stopped to help with power?

Please advise

---

### Post by Coder88 on 2013-09-12
So i wiped my laptop clean of anything Redmond, it now has only Ubuntu 13.04, and I apt-get'ed several power/battery management apps as suggested in this thread (thank you), will be trying out the laptop at the coffee shop in the morning, see how the battery does, etc. I will report back!

---

### Post by montag dp on 2013-09-12
I get better battery life in Linux than in Windows 7, but I have hardware that is well-supported (a Thinkpad) and I use TLP.  I highly recommend TLP, by the way.

---

### Post by varunendra on 2013-09-13
> **Coder88 said:**
> So i wiped my laptop clean of anything Redmond, it now has only **Ubuntu 13.04**, and I apt-get'ed several power/battery management apps as suggested in this thread (thank you)

Assuming you mean the default Ubuntu with Unity, I'd suggest to install XFCE  (sudo apt-get install xfce4) and use that as your default desktop environment. Its simple graphics environment should consume less battery power than Unity.

I have a dual-boot with Win7 and my laptop (a simple Asus X54C) gives 'almost' same battery backup (3:40-50 vs 3:40-4 hrs.) while using Unity when all the fancy compiz effects are off and am doing simple text editing type work (browsing with chromium seems to drain a lot of power).

Windows7 uses the drivers and power saving application supplied with the laptop, Ubuntu uses all open source one. But like I said, it is just a simple laptop with simple hardware (Intel 3000 graphics).

For additional measures, I run "powertop" (sudo powertop) when on battery power, and make all settings look "Good" in its interface. This works only for the running session (will have to be run again on next boot) but increases the backup time to roughly 10-15 minutes.

---

### Post by mastablasta on 2013-09-13
> **Coder88 said:**
> So i wiped my laptop clean of anything Redmond, it now has only Ubuntu 13.04, and I apt-get'ed several power/battery management apps as suggested in this thread (thank you), will be trying out the laptop at the coffee shop in the morning, see how the battery does, etc. I will report back!

yes it is realyl difficlut to say something in general, because it all depends on hardware and even same model laptops can have different hardware. sometimes the hardware support is really good and battery lasts as much as in windows. other times it's really bad an dit drains battery a  lot. propper drivers are key. and opensource GPU drivers (as mentioned) can often fail in this respect. in fact they often have descent or good support for desktop GPU but not for mobiles.

> **DJonsson2008 said:**
> With Windows XP home I was easily getting 6-8 hours on my Aspire one Atom Intel machine with a 6 cell battery.
Presently with a 95% battery charge the battery icon in Xubuntu is telling me 5 hours left. If the Battery panel
is reporting correctly this seems that the margin was better with XP Home.

Given though the tweakabilty of Ubuntu/Xubuntu I'm curious what can be done to increase battery life if anything.

have you tried tlp?

also sometimes those battery indicators are not so good. i remember once i was on low battery for quite some time. :-)

> 
Would Lubuntu be easier on power?
Can CPU speed be limited to draw less power?
Can services be stopped to help with power?

Please advise

might be but probably not by much.
CPU speed can be limited but i think it is not the solution.
yes you can stop services. which is why perhaps lubuntu might do better (less services). i remember on an old laptop i've got much better battery life with linux than in default windows xp install (i used Chrunchbang on that old thing). turning off wi-fi, blue tooth and such if when you are not using them will extend battery life a lot.

you might also try some other distro and see how it goes. perhaps they have different settings, drivers etc. there are a couple out there specifically oriented towards netbooks (e.g. joli OS). KDE also has netbook plasma, but i haven't tried it yet to see how well it does on netbook with regards to power managemnet.

---

### Post by DJonsson2008 on 2013-09-13
Thanks for not above.  I am running Xubuntu (my prefered desktop) on the Acer Aspire Atom machine.
Lowering the brightness slightly provided a slight increase per the battery meter.
I've turned off bluetooth.

Using powertop visibly added another 20 minutes. 

In all honesty my 6-8 hour benchmark on this 6 cell battery Atom are for writing only with Windows XP Home.
(I'm sometimes write magazine articles and need the computer for this.) 

My current tests involve WIFI browsing which seems to eat considerable power. 

Since there seems to be no integrated gui for these sort of adjuments, I'll likely load the TLP app mentioned above.

But still am wondering if 

* Is there a gui app that helps in this regard?
* Does 12.* include CPU management in the OS?
* Is there anyway to control CPU for better battery usage?

---

### Post by DJonsson2008 on 2013-09-13
Checking this out it appears Ubuntu is very much on power management case.
The URL below details ; tweaks, current solutions being tested, and improvements
ongoing being added. [https://wiki.ubuntu.com/Kernel/PowerManagement](https://wiki.ubuntu.com/Kernel/PowerManagement)

I can say this, Windows XP Home was slow as molasses in an Alaskan February compared
to Xubuntu which runs like greased lightining -- so a 10-15% percent change in battery life 
may be a small price to pay.

In anycase will not know until I turn off Wifi for a few hours on a train trip and use
this netbook for a word processing terminal only for 4 or 5 hours.
 
 Per the link above I did load powerstat which gives a report on the wattage being used,
its good to see a solid electrical measurement on the screen rather than the general
more dumbed down your machine is at X% sort of thing.

Lastly it does not seem like it would be rocket science to provide a more informative
and proactive/useful GUI on power for Ubuntu/Xubuntu linux.  In anycase between
powertop, powerstat and tlp perhaps what is needed is possible.  

I've yet though to install TLP has anybody on this thread good experience with it.

---

### Post by mastablasta on 2013-09-13
i haven't tried TLP yet, but from other threads it seems like a good thing. It is command line tool, but it comes with some default setups which (again i only read) are quite good.

---

### Post by Coder88 on 2013-09-13
Got at least the equivalent battery life on my laptop this morning in Ubuntu as I would have using Windows so no problems (once i did that tweak to get the screen dim function working).
:)

---

### Post by fyfe54 on 2013-09-13
+1 for tlp.  Works really well on my Dell.

---

