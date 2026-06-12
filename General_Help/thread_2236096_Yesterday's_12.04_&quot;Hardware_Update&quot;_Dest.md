---
title: "Yesterday's 12.04 &quot;Hardware Update&quot; Destroyed My System"
date: 2014-07-24
forum: General Help
---

### Post by pennrabb on 2014-07-24
I'm sure this is not a place to direct my rage. However, I'm not sure where else to direct it.

My machine has been happily (and awesomely) running 12.04 for years, and 10 before that. 

I just got an update with Update Manager with a 'Hardware Update'. 

I'm not sure who thought this update would be a good idea, but I am sure that they are lucky I don't know them and they are not here now.

This 'Hardware Update' disabled my DVD burner/player, my LAN card, and erased all my nvidia settings and doesn't support my monitor's resolution anymore.

So my machine is effectively destroyed.

I'm not in the mood to 'try' anything to fix it. It looked like it did several dozen 'updates'. I will just reload it. 

But thanks, Ubuntu, Canonical,, or whomever for putting that 'update' out, with no warning of what it might affect (destroy). 

Next time why don't you think about how many user hours you're about to waste with your lousy update?

---

### Post by QIII on 2014-07-24
I understand your legitimate frustration.  You have every right to be upset.

However, I'm sure that there are a lot of users like me for whom those updates were applied without issues.

Common sources of such problems are proprietary drivers, third party repos and PPAs from which you have installed "non-standard" software.

Might that be the problem in your case?

---

### Post by pennrabb on 2014-07-24
I didn't have any third party stuff.  But is is an older AMD machine.
I saw the update running through the system removing drivers and whatnot. 
A logical approach would have been to back all that up. Maybe download a java app or text instructions to revert it should it do something like that.
Didn't see anything like that happen.

---

### Post by Frogs Hair on 2014-07-24
See the link , it may shed some light the reason for the updates. 

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)


Ask Ubuntu questions:  [http://askubuntu.com/questions/tagged/hardware-enablement-stack](http://askubuntu.com/questions/tagged/hardware-enablement-stack)

---

### Post by pennrabb on 2014-07-24
I read all that prior to the update, Nowhere does it say that the update could affect the system to the degree it has and there's no way to revert.
An upcoming event affecting the 'loss' of hardware support, that actually might cause hardware to become inactive, is something to notify and prepare for, not something to shove in an vaguely described update and send out without some kind of warning about system effect.
I'm not arguing about the necessity of the update, but hey, the users have to be given a full warning about an update that could cause a system to go down like this. 
If I would have seen a warning I would have backed off and probably updated to 14 in a much more planned manner. 

I guess that day is now today if I want to do any other work before midnight.

And that's what sucks about it.

---

### Post by grahammechanical on 2014-07-24
Two days ago I put in a fresh install of Ubuntu 12.04.4 just to test what would happen if I accepted that offer to upgrade the hardware enablement stack (HWE). Every thing went fine. But I will say this, based upon the number of people posting on this forum reporting a broken OS I cannot understand why the upgrade was pushed out to existing 12.04 users.

I can see that as new hardware comes on the market that Ubuntu 12.04 needs the latest Linux hardware stack to be able to install on the newer hardware. That can be dealt with by updating the 12.04 ISO image. Existing users have no need for a newer Linux hardware stack because Ubuntu is working on their hardware. Unless it might fix an existing hardware incompatibility problem.

Not only that but during August 12.04 will get a new point release - 12.04.5. That will have the new HWE. So, why push out an upgrade now?

And then there is the matter of the warning itself. Someone has put in a bug report about it. Some have misunderstood exactly what was reaching end of life. Was it 12.04? That is supported until 2017, surely. And was does it mean that the hardware stack will not be supported? No more security fixes for the Linux kernel?

I have to say, this could have/should have been done better.

Regards.

---

### Post by Rob Sayer on 2014-07-25
> **grahammechanical said:**
> Two days ago I put in a fresh install of Ubuntu 12.04.4 just to test what would happen if I accepted that offer to upgrade the hardware enablement stack (HWE). Every thing went fine. But I will say this, based upon the number of people posting on this forum reporting a broken OS I cannot understand why the upgrade was pushed out to existing 12.04 users.

I can see that as new hardware comes on the market that Ubuntu 12.04 needs the latest Linux hardware stack to be able to install on the newer hardware. That can be dealt with by updating the 12.04 ISO image. Existing users have no need for a newer Linux hardware stack because Ubuntu is working on their hardware. Unless it might fix an existing hardware incompatibility problem.

Not only that but during August 12.04 will get a new point release - 12.04.5. That will have the new HWE. So, why push out an upgrade now?

And then there is the matter of the warning itself. Someone has put in a bug report about it. Some have misunderstood exactly what was reaching end of life. Was it 12.04? That is supported until 2017, surely. And was does it mean that the hardware stack will not be supported? No more security fixes for the Linux kernel?

I have to say, this could have/should have been done better.

Regards.

I agree 100%.  Not impressed at all.

I have an old compaq machine with an AMD 4xxx video adapter which isn't supported in linux by AMD anymore.  And I've not been impressed by what I've seen of HWE.  Frankly it seems like a bugfest.  I think I may just install another distro that uses an older kernel.  Fortunately I don't need that machine and haven't used it for a while, but that means I haven't fully researched it yet ;).

---

### Post by HermanAB on 2014-07-25
OK, so your machine was working perfectly, for years, then you do an update...

This is why I disable automatic updates as soon as a machine is installed and working properly.  Once every year or three, I re-install it from scratch.

---

### Post by kansasnoob on 2014-07-25
> **Frogs Hair said:**
> See the link , it may shed some light the reason for the updates. 

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)


Ask Ubuntu questions:  [http://askubuntu.com/questions/tagged/hardware-enablement-stack](http://askubuntu.com/questions/tagged/hardware-enablement-stack)

+1 ...............................

Also read:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by kansasnoob on 2014-07-25
> **HermanAB said:**
> OK, so your machine was working perfectly, for years, then you do an update...

This is why I disable automatic updates as soon as a machine is installed and working properly.  Once every year or three, I re-install it from scratch.

So you run for a year or more without security updates :shock:

---

### Post by kansasnoob on 2014-07-25
> **grahammechanical said:**
> Two days ago I put in a fresh install of Ubuntu 12.04.4 just to test what would happen if I accepted that offer to upgrade the hardware enablement stack (HWE). Every thing went fine. But I will say this, based upon the number of people posting on this forum reporting a broken OS I cannot understand why the upgrade was pushed out to existing 12.04 users.

I can see that as new hardware comes on the market that Ubuntu 12.04 needs the latest Linux hardware stack to be able to install on the newer hardware. That can be dealt with by updating the 12.04 ISO image. Existing users have no need for a newer Linux hardware stack because Ubuntu is working on their hardware. Unless it might fix an existing hardware incompatibility problem.

Not only that but during August 12.04 will get a new point release - 12.04.5. That will have the new HWE. So, why push out an upgrade now?

And then there is the matter of the warning itself. Someone has put in a bug report about it. Some have misunderstood exactly what was reaching end of life. Was it 12.04? That is supported until 2017, surely. And was does it mean that the hardware stack will not be supported? No more security fixes for the Linux kernel?

I have to say, this could have/should have been done better.

Regards.

If people installed Precise using either the original 12.04 or 12.04.1 media then they'll be running the 3.2 series kernel and Precise X-stack which are supported throughout April 2017.

But if they installed using the 12.04.2 media they have the Quantal kernel and X-stack, 12.04.3 used the Raring kernel and X-stack, and 12.04.4 used the Saucy kernel and X-stack. All of those three will stop receiving important updates next month, therefore the HWE EOL.

In about two weeks 12.04.5 will be released with the Trusty kernel and X-stack which will be supported in Precise up until April 2017.

The reason this was done related to the reduction of the interim release cycle to only 9 months. They wanted to offer an LTS version that would run the latest hardware so the intent was good - the implementation was NOT.

BTW if someone wants to reinstall Precise now and not have to deal with the HWE upgrade they can get the 12.04.1 media here:

[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

But, as stated above, only the 12.04 and 12.04.1 images shipped the actual Precise kernel and X-stack!

So, things are what they are regarding Precise, we can't roll the clock back.

What we can do is try to shape Canonicals plans for 14.04.2, 14.04.3, and 14.04.4. My thought is to file a documentation bug report regarding the main download instruction page - simply recommending they offer three possible downloads instead of two; the latest interim release - the LTS w/HWE - and also the archived non-HWE LTS ;)

---

### Post by pennrabb on 2014-07-28
I'm attempting to decypher what I should do here (I had to take a couple of days away from it).

I have 12.04 running on 4 - 5 machines, most about the 2002-2008 vintage.
I haven't been using them, but when I do, I guess I should avoid the 'Hardware Update' button when it comes? Correct?

I tried loading 14 on this same box but I can't get a decent nvidia load there for my hardware, the latest thing I tried on that (apt-get install nvidia-current) made the system unbootable.
Before that when I first got it loaded it would only get 1024x768. I need 1280x1024.

So what is the deal? Is ubuntu not going to support any older hardware going forward? Could it not somehow support default resolutions beyond 1024x768?

---

### Post by kansasnoob on 2014-07-28
> I guess I should avoid the 'Hardware Update' button when it comes? Correct?

Doing so would result in running an unsupported kernel, and many kernel updates include security updates.

In less than two weeks the only currently supported kernels will be those in the 3.2 and 3.13 series:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.LTS_Kernel_Support_Schedule](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.LTS_Kernel_Support_Schedule)

So IMHO the best thing would be either a fresh install of 14.04.1:

[http://releases.ubuntu.com/14.04.1/](http://releases.ubuntu.com/14.04.1/)

Or a fresh install of 12.04.1 which still uses the 3.2 series kernel:

[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

Not an ideal situation for sure, please read what I said here:

[http://ubuntuforums.org/showthread.php?t=2236096&page=2&p=13082770#post13082770](http://ubuntuforums.org/showthread.php?t=2236096&page=2&p=13082770#post13082770)

If you're having trouble getting the drivers working for a specific graphics chip I'd open a new thread regarding exactly that - including specific graphics chip info.

I have this nVidia chip working in both 12.04 and 14.04:

> nVidia C61 [GeForce 7025 / nForce 630a] (rev a2)

I always use the Additional Drivers UI to install and setup the desired driver.

---

### Post by monkeybrain20122 on 2014-07-28
I think HWE doesn't occur with normal updates. No?

This is ridiculous. That's why I stick to the .0 release and don't do  any HWE (for people I installed LTS for, I don't stick  to LTS). I would  rather update the kernel manually and get a ppa for the graphic driver  like xorg-edgers or oibaf rather than Canonical's "supported" versions  which is not supported after a while and then you have to clean up the old HWE

---

### Post by MrSteve on 2014-07-28
now i understand why my system was blown out of the water 3 times (re-installs) and my wife&#8217;s system is as solid as a rock.

i re-installed using the ubuntu 12.04.4 ISO (new HDD) my wife&#8217;s system was installed using the ubuntu 12.04.1 ISO.
on the 4th install i used the kubuntu 12.04.4 ISO which uses the 3.2 kernel, the same as the wife&#8217;s system.

didn&#8217;t realise that i could get hold of, too install, the 12.04.1 ISO and all would be stable again.
you live and learn, now learning KDE :) ...

---

### Post by Smokin Whale on 2014-07-28
I had exactly the same thing on mu Grandma's Asus Pro31F Laptop. Not impressed at the slightest. This should not occur on a LTS release. Thankfully I was able to recover her data and install 14.04 but it was still a pain to have to go through.

---

### Post by kansasnoob on 2014-07-28
> I think HWE doesn't occur with normal updates. No?

Right, as it says [here]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"):

> Only those installing from the 12.04.2 or newer point release media will automatically receive a newer enablement stack by default. 

I knew this from reading the release notes for each and every release :biggrin:

---

### Post by pennrabb on 2014-07-29
All reloaded and happy again on 12.

Now don't ever do that to me again.

Oh and to the guy that only updates once every 1-3 years: You are a hacker's wet dream.

---

