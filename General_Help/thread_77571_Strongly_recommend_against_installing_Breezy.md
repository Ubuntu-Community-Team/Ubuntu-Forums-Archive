---
title: "Strongly recommend against installing Breezy"
date: 2005-10-17
forum: General Help
---

### Post by pico303 on 2005-10-17
I've used both Warty and Hoary on my laptop to great success, but Breezy is a nightmare.  Nvidia restricted drivers seem to be broken and lock the machine up (hard crash) after a few minutes.  Reverting to the nv driver lets the machine stay alive a little longer, at which point just the keyboard locks up (mouse still works).  Things seem to hiccup all over the place.  The entire distribution just feels broken.

I think this one was a big boff, guys.  I love Ubuntu, but after the nightmarish day I've had with Breezy, I'm honestly considering Fedora again.

By the way, this was a clean install.  Had to, 'cause the upgrade horked in the middle with some weird error about two packages sharing the same file.  Pretty much blew my installation to pieces.  Thank god I'd backed up before trying the upgrade.

Congratulations if you got your installation to work well.  Judging by the number of new posts cropping up seemlingly by the minute, I'm guessing the successes with Breezy are a rarity.

---

### Post by Pablo_Escobar on 2005-10-17
I'm sorry to hear that Breezy does not work for You. From my point of view You just need a little stubbornes and a need to do the config right.
Many people here complained about Radeon 9550 giving them problems. Well, I have ATI 9550 card and it has been giving me a lot of trouble. 
I have to admmit I was think also about installing Fedora. My love for Ubuntu won. Do You really want to end up in the FC-yum-repository hell ?? :)
I made a clean install of Breezy, fiddled around and voila, my ATI 9550 and 3D acceleration works :) 
You need to be more patient. What if Fedora places some broken hardware RPM ? You're going to revert to some other distro ? 
Problems are there to be solved, every distro has them, and with great support here almost every problem can be fixed.

Just my 0,02 EURO :D

---

### Post by BobDoLe on 2005-10-17
Hi, new user here (just installed tonight) and I am also having problems with X server locking up. I've had to ssh into the machine to reboot (I use usb keyboard and mouse). In the past, I've found remedy for this type of lock by commenting out RenderAccel (I also use nvidia), however this time around I am looking for help. I was hoping to install a different version of xorg and compile the nvidia drivers, however, the kernel source is nowhere to be found :???:

---

### Post by pico303 on 2005-10-17
You know, I think that's my real problem these days:  just keep fighting with it, and eventually it will work.

I'm really tired of that philosophy.  I'm completely discouraged that the Linux community, vendors included, can't seem to get it together and build a good distribution that just works.  Everything is version 0.6 or 0.3 or 1.2beta1, and none of it ever works smoothly.  

I understand the PC market is such that you can't test it on everything, but I've got a pretty standard system:  P4, Nvidia 5200 GeForce4 Toshiba laptop.   It doesn't seem that out of the ordinary to me, nor that cutting edge.  Has Linux just gotten so delicate that the slightest thing sends it whirling out of control?  Sounds like Windows 95 to me.

Thankfully I have a Mac at home (which I'm writing this on now, as my work laptop reinstalls Hoary), or I think I would go completely insane.  I'd just like to actually do something on the computer, not spend all this time mucking about in configuration files trying to tweak it so it will run without crashing. 

At least I'll be able to get something done on the Mac tomorrow while I reload all my software onto the laptop.  I think Linux is a great server environment, but I'm about ready to throw in the towel and go back to Windows (until I can convince my company to buy me a Powerbook) on the desktop.  Hate to say it, but XP is far more stable than Linux these days when it comes to desktop apps.

---

### Post by merlyn on 2005-10-17
I'm also sorry to hear that you have been experiencing problems, and that I don't have any helpful advice.

Is this a laptop install problem perhaps?

I've been running 'breezy' since the repos opened hard on the heels of hoary, and have had a few problems, though nothing insurmountable.

Also to see how things have been going since the final release, I did a fresh install on my secondary hard drive, (my trusty testbed), installed the nvidia drivers etc. 

Everything happened smoothly, so I did a fresh install on my primary drive, after backing up my data.

Once again, it all went without a hitch.

I certainly hope that whatever is causing your problem is resolved soon, sounds frustrating.

---

### Post by ikd69 on 2005-10-17
[QUOTE=pico303]I've used both Warty and Hoary on my laptop to great success, but Breezy is a nightmare.  Nvidia restricted drivers seem to be broken and lock the machine up (hard crash) after a few minutes.  Reverting to the nv driver lets the machine stay alive a little longer, at which point just the keyboard locks up (mouse still works).  Things seem to hiccup all over the place.  The entire distribution just feels broken.[/QUOTE]

It seems that you hit the jackpot big time :D Sorry for your troubles, however, you base your argument on a laptop which has very specific characteristics.
I have just dist-upgraded from hoary to breezy both boxes a PIII and an AMD64.  Both cases worked like charm.

[QUOTE=pico303] Has Linux just gotten so delicate that the slightest thing sends it whirling out of control? Sounds like Windows 95 to me.[/QUOTE]

No, linux has not gotten any more delicate, but only a few years back, your situation would have been "mainstream".  Maybe we are all getting comfy with our distros and don't take just enough time to look elsewhere.  If ubuntu doesn't work for you, try suse, fedora or some other distro.

The choice is yours.

Cheers,

ikd

---

### Post by gregh on 2005-10-17
I have a Toshiba A70 laptop and I found Breezy installed better thean either warty or Hoary (which were ok apart from some tweaking)

wireless, sound, widescreen etc all just worked.

I am pleased with Breezy and congratulate all concerned.
There are some minor issues if i try to use the binary ATI driver, but the xorg ati driver works fine.

If you are a new user considering trying Breezy, don't let this thread put you off, if you are currently trying breezy out and get a few problems, post something useful so people can help you out (they *will* help),

If you think everything in the MS world *just works* go back and try installing a non-OEM version of XP on your Toshiba laptop (I have tried it) and see how *easy*  XP (out the box) actually is.


-Greg

---

### Post by shadow on 2005-10-17
Funny how 99% of updates have went without a hitch, and you're basing the statement "Strongly recommend against installing Breezy" off a few bad experiences.

---

### Post by afonic on 2005-10-17
[QUOTE=pico303] Hate to say it, but XP is far more stable than Linux these days when it comes to desktop apps.[/QUOTE]

ROFL!

Seriously, I am sorry that you have trouble, but Breezy has updated many important components (X.org and more) that most people don't realise, so when they have problems they just say "Breezy" is buggy. 

Being an experienced Linux user, I was able to get Breezy running like a charm both in my PC and laptop. I had to mess with some settings and spend about a day testing, but in the end I have a system a 100 times more stable than what Windows will ever be.

If you want to use Linux, accept you need to spend some time configuring everything, it's really rare to get what you need just after the installation. 

Good luck.

---

### Post by cloudr on 2005-10-17
I have upgraded 2 laptops and  2 desktop pcs to breezy without any major hic cups. Yes on one of them at some point half way through distrib-upgrade it stopped complaining two packages were using the same file. I completely removed both packages since they were hardly relevant anyways and did apt-get update --missing && apt-get distrib-upgrade and things resumed nicely

It has to be said that the PC where I had this trouble had a few non-ubuntu reps at some point of its life and I am convinced that was the reason two packages ended up sharing a file.

---

### Post by blackant on 2005-10-17
I upgraded to breezy just yesterday...
the only problem I got is the putting in the new repositories list.

But I got it sort out by reading around the forum. :P
Another error I received is something to do with the locale.. then again it only shows it during the upgrading process.. so far my system is running fine.

Maybe I am just lucky. :D

---

### Post by plumcreek on 2005-10-17
[QUOTE=BobDoLe]I was hoping to install a different version of xorg and compile the nvidia drivers, however, the kernel source is nowhere to be found :???:[/QUOTE]

That there is the problem with the nvidia drivers from the "restricted" repository. They're not open source. They come from Nvidia and you're just going to have to trust them that they're OK. Ubuntu and/or Canonical have no control over their quality. 

That said, they work quite well for the **majority** of the people who have Nvida graphics cards. Much better, actually, than the open source nv drivers. I use the nvidia drivers on my Breezy box at home, and have **never** had any trouble with them.

---

### Post by BLTicklemonster on 2005-10-17
Hi sorry to hear about your problems, but Habib here can levitate all day long, we don't understand why you can't. You must be doing something wrong old boy. Sorry to bother you have a nice day.

I'm going back to hoary.

---

### Post by plumcreek on 2005-10-17
[QUOTE=pico303]I'm completely discouraged that the Linux community, vendors included, can't seem to get it together and build a good distribution that just works.  Everything is version 0.6 or 0.3 or 1.2beta1, and none of it ever works smoothly.[/QUOTE]

**None** of it ever works smoothly? I'm going to have to take umbrage with that statement. That's like saying all Americans are pigs, the French are all snobs, and Germans are elitist. While any of those labels may be appropriate for any number of any given population, you can hardly apply any of them to a single population as a whole without coming off looking stupid.

I'm not trying to be offensive, so please don't take this the wrong way. I just could not let that kind of gross over-generalization pass without some sort of comment. 

[QUOTE=pico303]I understand the PC market is such that you can't test it on everything, but I've got a pretty standard system:  P4, Nvidia 5200 GeForce4 Toshiba laptop.   It doesn't seem that out of the ordinary to me, nor that cutting edge.  Has Linux just gotten so delicate that the slightest thing sends it whirling out of control?  Sounds like Windows 95 to me.[/QUOTE]

Laptops are notorious for having custom hardware and bios bits that are unique to specific models. The only way to get a totally standard system is to assemble it "off the shelf" -- literally by walking into a computer parts retailer and picking all the parts needed for a system up off of the shelves, buying them, taking them home, and finally assembling the system yourself. 

This just isn't possible with laptops. There are whitebox laptops that you can buy without memory, hardrives and processors, but the rest of the system is still pretty custom, just like all other laptops.

In fact, **any** system you buy from a large computer manufacturer (Apple, Dell, IBM, Toshiba, HP, etc....) has custom parts and chips. None of them can be said to be "totally standard" and many of them fail the "pretty standard" test, especially when it comes to laptops.

Linux has made great strides in the past few years when it comes to laptops, but it has been a manufacturer by manufacturer and model by model (and sometimes model revision) process. This has been made easier due to the overall trend in computer manufacturing of trying to use standardized components whenever possible (manufacturers aren't building custom CD-ROM drives anymore, for example), but there are still improvements that can be made.


All of that said, could you post the specific error messages you're getting? or what you are doing when it is crashing? I'm sure the dev people would be more than happy to help in getting the problems you're seeing fixed. Toshiba is a big maker of laptops and if something in Breezy is borking them, it needs to be addressed. The main challenge is to isolate what component, driver, or other issue is responsible for the borking.

Thanks.

---

### Post by matthias_k on 2005-10-17
Don't listen to the whiners guys. He may have had trouble, but there are plenty of people who didn't. Breezy works like a champ for me. Inserted disk, installed, worked. Just as good as Hoary, only had to do the usual configuration stuff.

Only thing that didn't work out of the box was the fglrx driver for my radeon card. But I don't really need them right now, I don't play games or so in Linux. I'll look into that some other day.

---

### Post by polo_step on 2005-10-17
> **afonic] Breezy has updated many important components (X.org and more) that most people don't realise, so when they have problems they just say "Breezy" is buggy. [/quote]
There's no way for 99% of users to know where the bug is and whose responsibility it is.  They're trying to get something done and they can't because the process doesn't work.  Ultimately, the distro has to take the blame because whoever signed off on the release put the problematic stuff on the CD, whether the team wrote it or not. *Assigning blame is not meaningful to the user.*

> Being an experienced Linux user, I was able to get Breezy running like a charm both in my PC and laptop. I had to mess with some settings and spend about a day testing, but in the end I have a system a 100 times more stable than what Windows will ever be.
Actually, XP is more stable for me than 5.04, though I seem to be having undiagnosed hardware problems on one of my XP boxes that makes it seem otherwise on that particular machine, but XP was rock-solid there until something started flaking out on the board.  XP *applications* are far less trouble than Linux apps for me so far.  Hugely so.  Likewise drivers. These apparently are responsible for the sometimes very extravagant crashes I've had on 5.04.  The basic OS seems OK, but some of the third-party apps and drivers are just criminal...but there's garbage freeware for XP too, of course.

I've wasted a lot of time (and wasted a lot of other peoples' time) screwing around with Ubuntu 5.04 without ever getting some problems solved because there eventually turns out to *be* no solution for the problems said:**
> If you want to use Linux, accept you need to spend some time configuring everything, it's really rare to get what you need just after the installation. 
That's certainly true, but Linux "advocates" are often pretty schizoid about admitting this while cheerleading for their OS of choice to people who aren't expecting so much work to get stuff up and running [of course, OS advocates of any tribe are useless, dishonest, neurotic, pernicious bores who should be put on an island to flame each other to death and let normal people get on with the job].

The great thing about Linux is that you can do extensive and exotic configuration tweaking.

The horrible thing about Linux is that you'll probably have to.

As a consequence, it's a desktop OS that will always be more for people who are into process more than outcomes.  Computer hobbyists who enjoy playing with computers love Linux and rightfully so.  People who have more fixed goals and inflexible constraints in terms of work, projects, deadlines, hardware, peripherals and so forth will rightfully regard Linux as pure hell.  The latter group will always largely outnumber the former one.  In one of the numerous ways Linux is *not* free, the time-is-money user will find it an incredibly expensive OS.

I have no expectation of Linux ever doing everything I need, but I would be glad if it could just do all of my online tasks, as it is currently a much more secure OS for that.  Unfortunately, there are some apps that have no equivalent in Linux.  There is no Linux newsreader that yet comes remotely close to Forte Agent's capabilities, for example.

This is why I have four computers here running three OSs.

It's not a perfect world.

---

### Post by loki99 on 2005-10-17
Does anyone know, whether the HD performance issue has been solved in brezzy?

Only a couple of weeks ago, there was a thread about slow HD results in the brezzy development forum. Does anyone know anything?

[link](http://ubuntuforums.org/showthread.php?t=63505)

---

### Post by chunk on 2005-10-17
[QUOTE=pico303]I've used both Warty and Hoary on my laptop to great success, but Breezy is a nightmare.[/quote]

So why aren't you using Hoary? This isn't like Windows where you have to always be updating to avoid being infected by the latest spyware/virus. Security updates are separate for a reason.

[QUOTE=pico303]You know, I think that's my real problem these days:  just keep fighting with it, and eventually it will work.

I'm really tired of that philosophy.  I'm completely discouraged that the Linux community, vendors included, can't seem to get it together and build a good distribution that just works.  Everything is version 0.6 or 0.3 or 1.2beta1, and none of it ever works smoothly.[/quote]

The fact that you choose to run bleeding edge applications (.6, 1.2beta1) does not mean that *everything* is bleeding edge.

Stable, easy to use, current. Pick any two (this includes windows).

[QUOTE=pico303]Has Linux just gotten so delicate that the slightest thing sends it whirling out of control?  Sounds like Windows 95 to me.[/quote]

No, I think you have the wrong conception about Linux. Windows works out of the box, but don't expect it to work after 6 months without constant maintanence. Linux will take you 6 months to get working (or in the case of ubuntu, maybe 2 days), but after that it's smooth sailing. This is what is meant by stability. Not that it's easy to get it working, but that once you get it working it will continue to work.

By subjecting yourself to unecessary upgrades and reinstallations you are bringing problems on yourself. It's equivalent to purposely infecting your windows machine with viruses.

[QUOTE=pico303]Hate to say it, but XP is far more stable than Linux these days when it comes to desktop apps.[/QUOTE]

You're confusing ease of configuration with stability. If it never works properly then it isn't unstable. Unstable is when it was working properly, but then stops working.

---

### Post by matthias_k on 2005-10-17
> No, I think you have the wrong conception about Linux. Windows works out of the box, but don't expect it to work after 6 months without constant maintanence. Linux will take you 6 months to get working (or in the case of ubuntu, maybe 2 days), but after that it's smooth sailing. This is what is meant by stability. Not that it's easy to get it working, but that once you get it working it will continue to work.
This is so true, just let me second that. Debian is the perfect example for that. It always took me a full two weeks to set it up to my complete satisfaction, but after that, it ran flawlessly for over a year (would be still counting if I hadn't found out about Ubuntu at that time hehe).

In Windows however, it's only a matter of months until your registry is so wasted that you know it's time again to dump everything and do a fresh install. This can get very annoying.

---

### Post by pico303 on 2005-10-17
Just so everybody knows, I've been a Linux user since 0.9 kernel (yeah, I had an Internet connection at school when Delphi was the only way to get online for the general public).  I've done the scratch configuration for networking, and I can actually write an XFree86.conf or xorg.conf file by hand start to finish (wow, what a useless skill).  What I'm saying is I know my way around Linux; I'm not a newbie.  I also use it about 80% of the time at work, programming client/server apps.  It's not just a toy.  I try to use it to get things done.  

At the same time, I'm not a fanatic about open source:  I use the Java from Sun; IntelliJ is the best IDE I've ever used, bar none; and Visual Studio is still the way to go for C#.  Emacs is great, but TextMate (Mac) is better, at least for what I do.  And I'm o.k. paying someone for their time to develop good software.

Back to my problem:  as for error messages, there are none.  Most of the time the only thing I was running when it locked up was a terminal window trying to build some applications like rubygem.  I did have Firefox up once or twice, both the 1.0.7 default install and the 1.5 beta 2 install in my home directory.  It crashed many times without either of those applications being open.  

As for log error messages, nothing.  No dmesg, no syslog, no Xorg.log.  If I'd had those, I wouldn't have posted my problem/concern.  It just locks up, no questions asked.  

Some people said they could SSH into their machine when it had locked up.  I had no such luck.  

As for the laptop, we bought these laptops (Toshiba 17" P25's) specifically with Linux in mind.  Like I said, Hoary and Warty worked great on them, as does Fedora Core 1-4 (which is installed on four other laptops right now).  They're pretty high-end, and use a lot of standard hardware.  The most exotic thing I've found is the Atheros Wifi card, or maybe the Toshiba media buttons.  Wifi works fine, and I could care less about hitting the play button or WWW button.  I can't speak to the USB chips or the IDE controllers, but I can't imagine they're that exotic.  Nothing was plugged into USB, and no errors were thrown on either the IDE or USB controllers, so I'm guessing it has something to do with video.

For all the people with the "works on my machine" posts, I'm truly happy for you.  Honestly, no sarcasm.  I've got a friend here at work who had similar experiences:  Breezy works great for him at home, very fast, nice features.  I wish it would work on my laptop.  I wound up rolling back to Hoary, and I'll stick with that until the end of the year when I'll purchase a Powerbook myself and just use that at work.  

Maybe I should be doing a fresh install of Hoary then upgrading from there, which has worked on other distros before (Redhat 7 to 8 was notorious for that).  The other thought I have is that gcc4 may not be as stable as some would like to believe; I know it has problems on OS X Tiger and I've had to rollback to 3.3 to compile some apps there.  I don't know how much of Breezy was actually compiled with 4, so maybe that's not even an issue.

Thanks in advance for any suggestions as to what might be the issue.

---

### Post by pico303 on 2005-10-17
Have to say I've had a Windows XP installation running well and clean for over two years now (with many installs and uninstalls), and before that I had a Windows 2000 install that ran for 3 without slowdown.  Just as Windows advocates exaggerate about Linux, I think Linux advocates tend to exaggerate the same way about Windows.

---

### Post by aysiu on 2005-10-17
My XP runs perfectly well on my eMachines computer. But why is that surprising? The parts manufacturers had Windows in mind when designing their parts and creating drivers for them. eMachines made sure through extensive testing that Windows XP would run perfectly on it, and they even created a restore disk, so I wouldn't have to go through the pain of installing Windows should I want to reinstall. Why is it surprising Windows would run well on machines that it was designed to run well on? That's like saying, "It's amazing that my custom-made dress fits me perfectly, but this dress I bought at Banana Republic only sort of fits me."

The computer probably was not designed for Ubuntu, and Ubuntu was not designed for your computer, either. People who complain about Linux just don't know that installing any OS is a pain. They just don't have to install Windows, usually.

That said, I do have to agree with the original recommendation--Breezy's buggy. I had almost no problems at all with Hoary, but Breezy's been buggy, even with a fresh install.

---

### Post by BLTicklemonster on 2005-10-17
I can tell you that the biggest problem is people coming in wanting to install basics, and getting all messed up and having to start over. 

Play DVDs, Burn CDs, etc. It's not that easy, you all. You may think it is, because you are already used to it. This is all foriegn to most people.

You techies can pick these people apart and make it look like it's all their fault for ever getting near an electrical outlet in the first place, but the fact remains that WINDOWS RULES IN EASE OF INSTALLATION OF DRIVERS, ETC. But ubuntu is easier to set up than Windows. odd, huh. Arguing (or as my 4 year old used to say "argling") with people who are coming in here frustrated (like me on my third reinstall of Breezy just because all I want is to have the drivers that go with my video card. now how complicated should that be?) doesn't do anything but make you think you are 1337. You aren't. You just know stuff other people will later on. (a raindrop only lasts until it becomes a river, glasshoper)

These people need encouragement, not belittlement.

---

### Post by Cathbard on 2005-10-17
"Windows XP" and "stable" in the same sentence without a punchline? Have I stepped through a dimensional portal into bizaaro world? I've used Microsoft since they first rebadged QDOS and started pretending to be a software house. Stability? That it is a foreign concept to Microshaft users; it's something that Unix geeks used to talk about.
Nothing has changed except that stability is even further from Microshaft's grasp than ever and we now have Linux:p 

I've found Breezy to be excellent and the info to fine tune it is everywhere if you look. Admittedly I am using a desktop but my FX5200 is working fine. Laptops are always tricky, even for Winblows, a lot of lappies have special windows patches. Some new ones even have the OEM version burnt into a read only partition just so you don't use another version.

And of course, if you really want to go back to rpm distros then I will say a prayer to the great god of dependecy hell for you. May your Downloads folder be up to the challenge. ;)

---

### Post by pico303 on 2005-10-17
> The computer probably was not designed for Ubuntu, and Ubuntu was not designed for your computer, either. People who complain about Linux just don't know that installing any OS is a pain. They just don't have to install Windows, usually.

Yeah, like I said, I'm no newbie.  I've installed XP plenty of times, both on home-brew and off the shelf (Dell, Gateway) PCs.  I've installed Linux plenty of times.  I've installed OS X plenty of times.  

To say that "Ubuntu was not designed for your computer" is an insane statement to me.  If that's the case, Ubuntu shouldn't run on any computer, right?  Or maybe you guys need to publish specifications as to exactly what computers you're building Ubuntu on, so we know not to try it on anything else.  Or maybe you need to do like Apple did, and sell a machine that specifically works with the OS with everything already configured for us.

C'mon.

---

### Post by afonic on 2005-10-17
[QUOTE=pico303]Have to say I've had a Windows XP installation running well and clean for over two years now (with many installs and uninstalls), and before that I had a Windows 2000 install that ran for 3 without slowdown.  Just as Windows advocates exaggerate about Linux, I think Linux advocates tend to exaggerate the same way about Windows.[/QUOTE]

Stability is not how many times you need to re-install an OS. Leave Windows running for 30 days and you'll see what I mean (probably you will get a blue screen ~ day 20). When I say running, I mean light stuff - downloading, some test server etc.

---

### Post by Cathbard on 2005-10-17
Yea though I walk through the valley of Mandrake I will fear no Fedora. For Suse art with me; thy Yast and thy yum they comfort me. Thou preparest an installation before me in the absence of mine dependendies: surely caffeine and downloads will follow me all the days of my life.......amen


Sorry, I couldn't resist ;)

---

### Post by BLTicklemonster on 2005-10-17
How in the name of all that is sane can you people get anything linux up and running, yet you have so many problems with Windows. I have never had problems like what you all purport to have had with windows on any of the 4 machines I have at my house. And people who do have problems know to bring their machine over to ticklemonster's house, and I'll get it going for them, and if they follow my instructions, they won't have problems any more either. (except the know it all teenagers, they use IE and AOL instant messenger and wonder why they are always messed up)

I want to go over to linux based only on the aspect of $$$. and security. and UT plays like a mutha on Breezy. and it's something I always wanted to learn.

But really, if you fellows have that many problems with Windows (any idiot can use it, remember?), then it's a good thing you found linux.

---

### Post by Cathbard on 2005-10-17
Getting winblows to work isn't difficult. It's keeping it from choking on it's own gizzards that's the problem. Stability, security and fundamentally evil business practices are what's the problem.

---

### Post by BLTicklemonster on 2005-10-17
[QUOTE=Cathbard] my FX5200 is working fine. [/QUOTE]
Probably ought ot have read that closer before I made that last post and alienated everyone.. 

Hey, I have that card, too. But I can't get the nvidia drivers loaded for anything. What did you do? Admitedly, the nvidia-glx I had gotten using synaptic was working just fine, I don't know why I keep wanting to put the newest drivers in. 

My motherboard asus a7vx or something, I can't remember right now, has an nforce chipset on it. should I load drivers for it before loading drivers for the card? Are there any? Would you overlook my last post long enough to give me a hand? :)


*edit:
I can leave my computer sitting turned on for weeks, play games, check mail, watch dvds, you name it and never turn it off, and it never misses a lick. No crashes, no bsods nothing. The kids are worse, but since this summer, we've been on a mandatory, "TURN THEM THINGS OFF" rule around the house.

---

### Post by aysiu on 2005-10-17
I have to say I take issue with people saying XP is unstable. I happen to think XP is a great OS, and--with a few exceptions--every time I've run into a freeze, control-alt-delete works to get rid of the offending application.

I don't know about leaving a computer on, though, because for Linux and Windows I always shut down every day and reboot every day anyway.

Nevertheless, I also take issue with this whole "Linux is for crazy geeks" idea. I've had few problems using XP, and I've had few problems using Linux (Ubuntu, Mepis, and others). I've tried to install XP once from scratch and Windows 2000 once from scratch, and both times were a disaster (try playing DVDs without codecs in Windows--you can't just *sudo dpkg -i libdvdcss2.deb*). I've had to use recovery disks, and that's the only way I've been able to successfully install Windows without tearing my hair out.

The worst situations I've encountered with Linux have been bad screen resolution. I asked around, did a little research, and now I know to just add two lines to my /etc/X11/xorg.conf file.

I'm not a computer programmer, sys admin, or whatever. I don't know Java, Perl, Javascript, C++, Python, or any of that crap. I'm just a regular user who plays DVDs, listens to music, organizes pictures, surfs the web, and checks email. I've been using Linux for six months and trying to help other newbies like me.

And as for the remark about Ubuntu not being made for your computer, all I meant is that there are any number of configurations out there, and these hardware manufacturers don't have Linux in mind all the time (releasing source code or Linux versions for drivers might actually help Ubuntu and other Linux distros make themselves for "your" computer). Am I going to buy a Lexmark printer for my Linux computer? Probably not. This is what Poofyhairyguy calls "the true cost of Linux." You buy hardware for the operating system, not vice versa. When my wife and I went to find a printer for her computer, we were looking specifically for Mac-compatible ones. We didn't just buy whatever and then complain when it didn't work with her computer.

---

### Post by Cathbard on 2005-10-17
I did this:
> 
Originally Posted by Shabba

Simply open terminal and follow this ...

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.cong /etc/X11/xorg.conf_backup
sudo nvidia-glx-config-enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

copy this into the file you just created

[Desktop Entry]
Name=NVIDIA Settings
Comment=Change various aspects of your NVIDIA Graphics
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Applications;System;

(then select save)

Now, hold down Ctrl+Alt+F1 and type in your username +password

Type the following

sudo nano /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf

Scroll down to the label "Modules" then comment out using # the following lines

Load "Dri"
Load "GLcore"

(if either on neither can be found then don't worry)

Scroll down and find the section called "Device". Make sure Driver="nvidia" and not Driver="nv"

Directly after you see the line BusID "PCI;1:0:0" add the following

Option "RenderAccel" "On"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "On"
Option "Accel" "On"
Option "AllowGLXWithComposite" "Off"

Press down Ctrl+o then press the enter key
Press down Ctrl+X

type..

sudo reboot

But you saw this already no?

---

### Post by BLTicklemonster on 2005-10-17
Yeah, as a matter of fact, it's printed out sitting on top of my computer from last Friday. Forgot to take it home this weekend. You can bet it's going home with me tonight, though. 

Hey, is there anything special I should know, like anything nv related that ought not be on there?

Thanks.

---

### Post by polo_step on 2005-10-17
[QUOTE=afonic]Stability is not how many times you need to re-install an OS. Leave Windows running for 30 days and you'll see what I mean (probably you will get a blue screen ~ day 20). [/QUOTE]
That type of stability has always been Unix's strong suit and why it's a great industrial OS, but it's not relevant to most home users as most of us turn our computers off when not in use anyway.  Six months out of the year I have to, just because of the heat.  The computer in my recording studio heats the whole room in winter and defeats the air conditioning in summer. :)

---

### Post by pico303 on 2005-10-17
[QUOTE=afonic]Stability is not how many times you need to re-install an OS. Leave Windows running for 30 days and you'll see what I mean (probably you will get a blue screen ~ day 20). When I say running, I mean light stuff - downloading, some test server etc.[/QUOTE]

When I say installs/uninstalls, I'm talking about applications, not the OS.  My wife's computer has a 2 year old installation of XP on it, and the only time we reboot that is when we go on vacation, so a total of maybe five times in two years (I've got a pretty big battery backup on it, so power outages don't tend to affect it).  That's with heavy usage:  QuarkXPress, Photoshop, Outlook, Word, WinFax, Firefox, etc., not to mention Fast User Switching over to my account to play Half Life 2 and Doom 3.

The only machine I ever shutdown or reboot is my laptop (Linux/Windows), and my Mac every time there's a software update.  I don't tend to install Windows security patches, as they often do more harm than good.

---

### Post by polo_step on 2005-10-17
[QUOTE=aysiu]
Nevertheless, I also take issue with this whole "Linux is for crazy geeks" idea. 

[...]

The worst situations I've encountered with Linux have been bad screen resolution. I asked around, did a little research, and now I know to just add two lines to my /etc/X11/xorg.conf file.

I'm not a computer programmer, sys admin, or whatever. I don't know Java, Perl, Javascript, C++, Python, or any of that crap. I'm just a regular user who plays DVDs, listens to music, organizes pictures, surfs the web, and checks email. I've been using Linux for six months and trying to help other newbies like me.[/QUOTE]
There's a word for people like you:  *Lucky.*:)  As they say, "being lucky doesn't make you right." Or typical.

You might want to defer to my experience.  I've been trying to get a full-function Linux box up for *six years.*

Ubuntu is the first distro to come close, and I think much of that is because I installed it on a brand-new, purpose-built Linux box that came running with OEM Linspire [spit!].  I bought the computer on the spot simply because I didn't believe that a real 100% functional general-purpose Linux box was even possible. It turned out that I was right, as the Linspire was an incredibly stripped-down installation that could do little more than access their site online so that they could pump you for money for access to their repository...but at least the hardware was supported.

Ubuntu 5.04 Live worked reasonably OK (Kubuntu Live crashes -- go figure) so I gave it a shot.  It's OK.  It typically needs what I consider to be a lot of work and unfortunately most of it has to be done by the user for now, but it's not as hopeless as the distros I tried before.  That's progress -- slow progress, yes, but progress.

Some of the packaged applications have produced some absolutely spectacular crashes, the likes of which I haven't seen in nearly twenty-five years of daily computer use.  Maybe on another machine they work flawlessly. [shrug]

It looks like 5.10 will be less of a headache for me on this machine than it seems to be for everyone else, but there are already some known problems that dissuade me from doing an install because they pertain to hardware that I either have or plan to add. This is too bad, because some of the unresolved minor problems I have with 5.04 are not there in 5.10 Live. [sigh!]

I really wonder how many people beta-tested 5.10.  It can't have been that many, and it certainly doesn't seem to have been anywhere near enough.  This is one of the inherent problems with a basic OS with a chaotic few *hundred* different distributions -- no distro's new version achieves the ubiquity needed for really meaningful pre-release testing.  On the other hand, I've read that by the time XP v1.0 was put on sale over a **million** users were running either authorized betas, copies of them or leaks of the commercial release.

---

### Post by egon spengler on 2005-10-17
[QUOTE=polo_step]There's a word for people like you:  *Lucky.*:)  As they say, "being lucky doesn't make you right." Or typical.

You might want to defer to my experience.  I've been trying to get a full-function Linux box up for *six years.*

Ubuntu is the first distro to come close, and I think much of that is because I installed it on a brand-new, purpose-built Linux box that came running with OEM Linspire [spit!].  [/QUOTE]

Honestly I would think that Aysiu's experience is more common than yours. It can't be at all typical that Linux would manage to install only once in 6 years of trying

[QUOTE=BLTicklemonster] Play DVDs, Burn CDs, etc. It's not that easy, you all. You may think it is, because you are already used to it. This is all foriegn to most people.[/QUOTE]

Ubuntu does not support DVD playback out of the box for legal reasons. Personally I found it very easy to enable DVD playback (I just followed the steps in ubuntuguide) but the even easier step is installing an OS that comes with DVD support like Mepis or PClinuxOS

[QUOTE=BLTicklemonster]You techies can pick these people apart and make it look like it's all their fault for ever getting near an electrical outlet in the first place, but the fact remains that WINDOWS RULES IN EASE OF INSTALLATION OF DRIVERS, ETC. But ubuntu is easier to set up than Windows. odd, huh. Arguing (or as my 4 year old used to say "argling") with people who are coming in here frustrated (like me on my third reinstall of Breezy just because all I want is to have the drivers that go with my video card. now how complicated should that be?) doesn't do anything but make you think you are 1337. You aren't. You just know stuff other people will later on. (a raindrop only lasts until it becomes a river, glasshoper)

These people need encouragement, not belittlement.[/QUOTE]

I don't really recall seeing any of that in this thread, perhaps you are just saying that based on you perception of what annoying pricks Linux users are. I would argue that Windows does not rule in terms of driver installation though, most Linux distros auto recognise most hardware whereas with Windows installations you need all of the cds. I'd say the Linux installation sounds easier

---

### Post by sk545 on 2005-10-17
simply put, linux/ubuntu has a looong way to go (10 or so years).  The reason why its the way it is because of driver issues.  Manufacturer's just don't make enough/good enough drivers for linux, and we have to rely upon hacked/reverse engineered drivers.  Sometimes, they just don't work right.

You want something that will "just work"? Use Windows.  Yeah, you will get viruses and crap, but its guaranteed that your hardware has drivers for it.

Other than drivers, i don't find anything particularly wrong with Ubuntu Desktop.  Its just as simple to use (ok, maybe it doesn't have every single application made for it like windows has, but it has enough).

Oh, and that "linux for human beings" will go in effect in about 10yrs time (hopefully).

---

### Post by chunk on 2005-10-17
[QUOTE=pico303]When I say installs/uninstalls, I'm talking about applications, not the OS.  My wife's computer has a 2 year old installation of XP on it, and the only time we reboot that is when we go on vacation, so a total of maybe five times in two years (I've got a pretty big battery backup on it, so power outages don't tend to affect it).  That's with heavy usage:  QuarkXPress, Photoshop, Outlook, Word, WinFax, Firefox, etc., not to mention Fast User Switching over to my account to play Half Life 2 and Doom 3.

The only machine I ever shutdown or reboot is my laptop (Linux/Windows), and my Mac every time there's a software update.  I don't tend to install Windows security patches, as they often do more harm than good.[/QUOTE]

You won't install Windows security patches, but you upgrade Ubuntu on the day of release and blame Ubuntu when you have problems? Am I the only one that sees something wrong with this?

According to you, you're a seasoned veteran. You should know better than to jump in head first on release day. It's not even a good idea to install Windows on release day (remember all the nightmare stories from people installing Service Pack 2 of Win XP?).

Anyway, I can't speak for anyone else, but when I speak of Windows instability I'm talking about the fact that you need to be constantly running virus/adware scans to keep your system working. This is the main problem plaguing windows right now. You can't just use your system. You have to constantly take care of it.

---

### Post by sk545 on 2005-10-17
> you need to be constantly running virus/adware scans to keep your system working. This is the main problem plaguing windows right now. You can't just use your system. You have to constantly take care of it.
Not really, after MS released their "Antispyware beta" it sorta takes care of the problem.  Ofcourse you also have to run a virus program in the background as well and do complete cleaning (temp cleanup, defrag, scandisk, complete adware/virus scan, heck even have to reinstall it if your registry is badly clogged up) every few months regardless.  The virus/adware will propogate to linux as well...its just that its not as popular yet, so its not a target by crackers.  The question is: should linux just stay a niche, or should it become popular and then become "like windows", in other words be a target?  Heh, a dilema, isn't it?

---

### Post by MetalMusicAddict on 2005-10-17
[QUOTE=aysiu]I have to say I take issue with people saying XP is unstable. I happen to think XP is a great OS, and--with a few exceptions--every time I've run into a freeze, control-alt-delete works to get rid of the offending application.

I don't know about leaving a computer on, though, because for Linux and Windows I always shut down every day and reboot every day anyway.[/QUOTE]
I still like XP I dont like MS though and will not go to Vista.

I have a server based on a *VERY* stripped down XP Pro (legal). Before a power outage I had it goin for 161 days no problems. I run all my media from it and now 3 Ubuntu PCs are samba'd to it no prob. Im thinkin about going to Ubuntu but I have a very nice new HP printer that I will not get full use out of if I do. 

So far for me Breezy has been a little thorn. Some apps like [gDesklets]("http://www.ubuntuforums.org/showthread.php?t=77402") and [WINE]("http://www.ubuntuforums.org/showthread.php?t=76537") arent working as before. Ill get through it though. ;)

---

### Post by polo_step on 2005-10-17
[QUOTE=egon spengler]Honestly I would think that Aysiu's experience is more common than yours. It can't be at all typical that Linux would manage to install only once in 6 years of trying[/QUOTE]
What part of "full-function" don't you understand? ;) 

Some distros *installed,* but were only marginal in terms of operation.  Many wouldn't install at all, and most just couldn't do the stuff I needed done at the time or work with my hardware.  None were remotely satisfactory and all were far more trouble than they were worth in my situation, and I went through a bunch of different distros. 

As of the moment, there are still some gaps in available Linux applications for stuff I need done, so even given a wildly hypothetical 100% operation, hardware compatibility and slick install, no Linux distro can be "full function" for my needs even now.

Progress is being made, though, as just very recently is there such a thing as a grammar checker in a Linux word processing program, for example.  I don't know how (or if) it works yet, because it's in 5.10 which currently has known bugs with hardware that I either have or plan to use.

---

### Post by egon spengler on 2005-10-17
[QUOTE=sk545]its just that its not as popular yet, so its not a target by crackers.  The question is: should linux just stay a niche, or should it become popular and then become "like windows", in other words be a target?  Heh, a dilema, isn't it?[/QUOTE]

As I understand it's not just a case of safety through obscurity. Linux is pretty popular as a server shouldn't that be impetus for hackers to target it? I'm sure tht most hackers know of the existnece of Linux, wouldn't there be even just a few Linux viruses (that work as more than just proof of concept) to go a long with the 100s for Windows?


[QUOTE=polo_step]What part of "full-function" don't you understand? ;) 

Some distros *installed,* but were only marginal in terms of operation.  Many wouldn't install at all, and most just couldn't do the stuff I needed done at the time or work with my hardware.  None were remotely satisfactory and all were far more trouble than they were worth in my situation, and I went through a bunch of different distros. 

As of the moment, there are still some gaps in available Linux applications for stuff I need done, so even given a wildly hypothetical 100% operation, hardware compatibility and slick install, no Linux distro can be "full function" for my needs even now.[/QUOTE]

Somehow I would be surprised to find tht Linux ever meets your stringent criteria for "full functionality". I think you want Windows, why not just use Windows? In the mean time I can't help but wonder why on earth you think it is that Aysiu should defer to your experience? His computer works perfectly well for him yet for some reason he is supposed bear in mind that polo_step is displeased with a lack of a grammar checker and so he should refrain from mentioning that he finds Linux very usable? An absurd idea

---

### Post by bhishma on 2005-10-17
[QUOTE=pico303]You know, I think that's my real problem these days:  just keep fighting with it, and eventually it will work.

I'm really tired of that philosophy.  I'm completely discouraged that the Linux community, vendors included, can't seem to get it together and build a good distribution that just works.  Everything is version 0.6 or 0.3 or 1.2beta1, and none of it ever works smoothly.[/QUOTE]


I agree with what you said here.

Last year I gave my first go at Linux by trying to install Red Hat, Mandrake and SuSE, but none of those distributions could give me both GUI and network on boot. And then I was very disappointed at the advices I got from the linux community, because they all involved editing some files in vi or emacs. Guess how surprised I were to find out that Ctrl+S doesn't save the file in vi. :???: And it certainly didn't help that one of my postings somehow ended up as a vi vs. emacs thread.

Well this summer I gave another go at Linux by trying Ubuntu (Hoary), and now I'm running it at my main office desktop. I was delighted to find a Linux distribution that finally could detect the hardware properly.


I have been thinking about upgrading to Breezy for the past week, but after following the postings at the forum, I think I'll wait another month or two. I'm quite convinced that Breezy was rushed and is not ready.

When you need to get work done, you want a system that's stable and predictable. And if an OS cannot provide that, then it should still be called a beta, not a release version.

---

### Post by chunk on 2005-10-17
[QUOTE=sk545]Not really, after MS released their "Antispyware beta" it sorta takes care of the problem.  Ofcourse you also have to run a virus program in the background as well and do complete cleaning (temp cleanup, defrag, scandisk, complete adware/virus scan, heck even have to reinstall it if your registry is badly clogged up) every few months regardless.  The virus/adware will propogate to linux as well...its just that its not as popular yet, so its not a target by crackers.  The question is: should linux just stay a niche, or should it become popular and then become "like windows", in other words be a target?  Heh, a dilema, isn't it?[/QUOTE]

It's not a dilemma for me. I use Linux because I prefer dealing with bad drivers than viruses. Sure it would be nice if I could have my cake and eat it too, but I'm fairly content with the ways things are now.

Also, I don't see any reason to be so sure that the whole virus/spyware situation would go down the same way with Linux as it has with Windows. Remember, computer security can't be fully understood on technical qualities alone and, in my opinion, the social interactions of all the stakeholders (os/application writers, end users, malware writers, etc.) play a much larger role.

The main form of program distribution is completely different between Linux and Windows. On Windows you usually just download programs from completely untrusted websites, but on linux you usually download them from central repositories. I believe that the central repositories would be much less susceptible to exploit (although not completely immune), not to mention all the potential that has yet to be unlocked in the linux-style distribution system that could very well be used to combat malware. Furthermore, it is debatable whether virus writers would even have the same motivation to exploit a free os.

Besides, progress for Linux results in progress for all opensource unix-like operating systems. So if linux ever becomes overrun with viruses like windows, then we can always retreate to OpenBSD, which I believe would be a tougher nut to crack. Even in the worst case, the sheer variety of opensource unix-like OSes provides a tremendous amount of protection. Lack of a software monoculture and differences in implementation are a greater hinderance to malware writers than writers of useful software.

---

### Post by polo_step on 2005-10-17
[QUOTE=egon spengler]
Somehow I would be surprised to find tht Linux ever meets your stringent criteria for "full functionality". I think you want Windows, why not just use Windows? [/quote]
Of course, for some stuff I still have to.

One of the big brick walls for Linux application development is obviously the lack of profitability in turning out complex, bug-free and well-documented suites.  Unless you can find a corporate sugar-daddy to underwrite an open-source freeware Linux project, you'll starve long before you get it done.

Good, big programs don't grow on trees.

>  I can't help but wonder why on earth you think it is that Aysiu should defer to your experience? His computer works perfectly well for him yet for some reason he is supposed bear in mind that polo_step is displeased with a lack of a grammar checker and so he should refrain from mentioning that he finds Linux very usable? An absurd idea
It's an absurd and malicious misrepresentation of what I said, too. :rolleyes:

---

### Post by chunk on 2005-10-17
[QUOTE=egon spengler]As I understand it's not just a case of safety through obscurity. Linux is pretty popular as a server shouldn't that be impetus for hackers to target it? I'm sure tht most hackers know of the existnece of Linux, wouldn't there be even just a few Linux viruses (that work as more than just proof of concept) to go a long with the 100s for Windows?[/quote]

You're forgetting the fact that servers are usually run by experts. How effective a virus is has much more to do with the users than the software. Its mostly a problem "between the keyboard and the chair" :).

However, (as I mentioned before) there is the additional factor that no version of linux is the same. Many many malwares exploit problems in the implementation, not in the official specifications. Just having 10 different implementations (such as different distros) reduces the effectiveness of this kind of exploit by 1/10th. As a security measure, I personally find that very impressive.

[QUOTE=egon spengler]Somehow I would be surprised to find tht Linux ever meets your stringent criteria for "full functionality". I think you want Windows, why not just use Windows? In the mean time I can't help but wonder why on earth you think it is that Aysiu should defer to your experience? His computer works perfectly well for him yet for some reason he is supposed bear in mind that polo_step is displeased with a lack of a grammar checker and so he should refrain from mentioning that he finds Linux very usable? An absurd idea[/QUOTE]

"Full functionality" is also in the eye of the beholder. When I first started using Linux exclusively I would not have describe it as "fully functional", but now I wouldn't describe Windows as "fully functional" (where is the ssh client? where is the package manager? where is the support for batch processing like shell scripts? etc. etc.)

---

### Post by chunk on 2005-10-17
[QUOTE=polo_step]Of course, for some stuff I still have to.

One of the big brick walls for Linux application development is obviously the lack of profitability in turning out complex, bug-free and well-documented suites.  Unless you can find a corporate sugar-daddy to underwrite an open-source freeware Linux project, you'll starve long before you get it done.

Good, big programs don't grow on trees.[/QUOTE]

But why do you need big programs? I mostly prefer cascading small programs, each of which does a small job very well, to using large programs which do many things, but poorly (or at least cumbersomely).

Big programs are overrated. I don't care what anyone says; my mother does not need photoshop just to resize and print her pictures.

---

### Post by Antman on 2005-10-17
[QUOTE=matthias_k]
In Windows however, it's only a matter of months until your registry is so wasted that you know it's time again to dump everything and do a fresh install. This can get very annoying.[/QUOTE]

Indeed.... people need to learn to setup non-admin accounts in XP in order to prevent this from happening.

---

### Post by gpw797 on 2005-10-17
I have been using Breezy for a couple months and it works great for for me and no hardware issues (other than 64 bit version and I have since reverted to 32 bit version)

---

### Post by andril on 2005-10-17
I wouldn't "Strongly recommend against installing Breezy" but I too have not been as fortunate to win the Linux Lottery this time. I was able to install Warty 4.10 & Hoary 5.04 without errors or issues. I paitently waited for Breezy 5.10 to be released to final - I installed the following morming to run into some Xorg issues - so I backed my data up and did a fresh install! That's where I began to see the big picture, from missing packages to random errors (which have been already mentioned in the forum). I began to regret the update. But with an open mind I realized that it's new - give it a chance. I beg anyone that got the installation to work flawless-ly to inform me of the steps taken. Also point me in the correct direction to working repoitories. Thanks In Advance!

---

### Post by evilmrt on 2005-10-17
I have used Ubuntu since the early days, but this release seems like it was rushed...

I don't have any sound for the first time since Ubuntu was public! Rediculous!

---

### Post by bluck on 2005-10-17
[QUOTE=pico303]  Hate to say it, but XP is far more stable than Linux these days when it comes to desktop apps.[/QUOTE]

i cant agree with that. out of the box, XP is compromised in seconds, if you havent a firewall, nevermind the 3 hours of patching after install.

i've been able to install breezy on a couple laptops, and many desktop machines.
one of the laptops had some video driver issues, nothing major.

the thing to remember about laptops is their hardware components are often adapted for that particular line or model of laptop.

for example, the radeon mobility drivers from ATI dont work for the compaq evo n610c,  you have to get the radeon drivers from HP. this is true even for windows.

having said all that,  what was the output from your X server?

---

### Post by 11hjpphty76lkjj on 2005-10-17
[QUOTE=MetalMusicAddict]I still like XP I dont like MS though and will not go to Vista.

I have a server based on a *VERY* stripped down XP Pro (legal). Before a power outage I had it goin for 161 days no problems. I run all my media from it and now 3 Ubuntu PCs are samba'd to it no prob. Im thinkin about going to Ubuntu but I have a very nice new HP printer that I will not get full use out of if I do. 

So far for me Breezy has been a little thorn. Some apps like [gDesklets]("http://www.ubuntuforums.org/showthread.php?t=77402") and [WINE]("http://www.ubuntuforums.org/showthread.php?t=76537") arent working as before. Ill get through it though. ;)[/QUOTE]

What sort of printer do you have?  You should check out [http://hpinkjet.sf.net](http://hpinkjet.sf.net) this software is designed  to give your printer most of the functionality.  If you need help installing it let me know.  But if you have a newer printer it should work.  Features that work for a lot of printers are; printing, scanning, media cards, and fax is in the works.  Please do not stay with Windows because you can't get your printer to work, if it's newer it should work with HPLIP.  Your printer can work in Ubuntu!  I've tested many printers with Ubuntu Hoary and I'll be giving Breezy a round very soon.

Aaron

---

### Post by MetalMusicAddict on 2005-10-17
[QUOTE=kalosaurusrex]What sort of printer do you have?  You should check out [http://hpinkjet.sf.net](http://hpinkjet.sf.net) this software is designed  to give your printer most of the functionality.  If you need help installing it let me know.  But if you have a newer printer it should work.  Features that work for a lot of printers are; printing, scanning, media cards, and fax is in the works.  Please do not stay with Windows because you can't get your printer to work, if it's newer it should work with HPLIP.  Your printer can work in Ubuntu!  I've tested many printers with Ubuntu Hoary and I'll be giving Breezy a round very soon.

Aaron[/QUOTE]
Thanx man. Ill be pickin' your brain for sure. Its a PhotoSmart 8400. I network to it via my (Ubuntu/Dell) laptop.

I have seen things on that link you sent but Im not sure I understand it all. Ill PM you tomorrow to talk further.

Dont wanna hijack the thread. ;) Thanx.

---

### Post by Gezzer on 2005-10-17
i have a 3 system home network all running ubuntu
2 systems have been upgraded to breezy from hoary and are running fine
the 3rd system will be updated this week, so far so good ...

---

### Post by actinic on 2005-10-17
Buggy is a good description, or what am I'm missing?

I can open txt & html files but not jpg, bmp, or pdf's! They're all housed
on another linux box (Mepis) and in the SAME directory.  I get a
spinning disk whenever trying to open these, then it stops and gives up.

Ditto when housed on a Windows share.

When those files are on my Ubuntu box they open fine.

They also open just fine if housed on my Arch Linux box.  

Explain that one to me.

Bug, no?

---

### Post by cowlip on 2005-10-17
dbus seems so very buggy, mounting floppies gives me hell, and I have to disable it to burn cds.  Hoary never gave me this problem.

---

### Post by aclaunch on 2005-10-17
Just to expand this Linux vs Windows theme-my biggest complaint is in documentation and being able to fix things that don't work. My wife's Win laptop doesn't connect to the networked printer, something causes a crash, the wifi card decides it can see my network but cannot connect-what do I do? I'm basically SOL.

In Linux, I can open a terminal, check config files, read error logs and search the internet and find multiple suggestions/solutions. Linux allows you to follow the processes of the underlying system and fix things (or set up things). What do you do when the Win instructions say "click yes to connect" and it doesn't connect and there's no place to figure out why? And the MS knowledgebase is no more than a rehash of "click yes to connect" and "make sure your computer is turned on" kind of "knowledge".

That said, I think Breezy is very nice. I've been using Linux for about 6-7 years-first Suse, then Slackware and now Ubuntu (and an OpenBSD home network). Hardware detection is excellent (plug and use digital cam-rivals my Powerbook), apps work as I expect, and it took about 1 hour to config/set up all the little details after a dist-upgrade from Hoary.

YMMV, but I definitely think Ubuntu is "ready for the desktop".

Alan

---

### Post by BobDoLe on 2005-10-17
[QUOTE=pico303]Just so everybody knows, I've been a Linux user since 0.9 kernel (yeah, I had an Internet connection at school when Delphi was the only way to get online for the general public).  I've done the scratch configuration for networking, and I can actually write an XFree86.conf or xorg.conf file by hand start to finish (wow, what a useless skill).  What I'm saying is I know my way around Linux; I'm not a newbie.  I also use it about 80% of the time at work, programming client/server apps.  It's not just a toy.  I try to use it to get things done.  

Back to my problem:  as for error messages, there are none.  Most of the time the only thing I was running when it locked up was a terminal window trying to build some applications like rubygem.  I did have Firefox up once or twice, both the 1.0.7 default install and the 1.5 beta 2 install in my home directory.  It crashed many times without either of those applications being open.  

As for log error messages, nothing.  No dmesg, no syslog, no Xorg.log.  If I'd had those, I wouldn't have posted my problem/concern.  It just locks up, no questions asked.  [/QUOTE]


I totally hear you. I've been a linux user for years and the xorg lockup was ridiculous. I was working on correcting it for an hour or so, but I was so put off by how it happens right after starting x on the fresh install. 

I switched back to gentoo last night, let my machine compile everything (from scratch - almost) for about 16 hours straight and I have a fully loaded system that runs great. 
Ubuntu's install is quick and easy, but I felt helpless when it came to correcting the problem. I didn't even have access to the kernel source (and running apt-get install kernel-source could not help as the sources available were incompatible). I dont know what you people see in Ubunto though - no offense.

---

### Post by egon spengler on 2005-10-18
[QUOTE=polo_step]It's an absurd and malicious misrepresentation of what I said, too. :rolleyes:[/QUOTE]

[QUOTE=polo_step]There's a word for people like you:  *Lucky.*:)  As they say, "being lucky doesn't make you right." Or typical.

You might want to defer to my experience.  I've been trying to get a full-function Linux box up for *six years.*

Ubuntu is the first distro to come close.[/QUOTE]

Errr.. no. It's precisely what you said. Sorry but you're not the universal barometer of how "fully functional" an operating system is. Many people find that Linux meets their needs and so they are fully at liberty to publiclly state as much regardless of how unsatisfied you may be

---

### Post by ikekrull on 2005-10-18
I too have had Nvidia lockup problems, with both the nvidia-glx and the nvidia-legacy-glx packages.

And of course the last stable drivers (6629) don't compile with Breezy's 2.6.12 kernel.

Not only that but firewire removable disks didnt work out of the box due to sd_mod not being loaded when it should be.

There seems to be something severely wrong with hal/udev/hotplug - devices that are plugged in are assigned different device names from Hoary, and (Under KDE) don't automount at all and there are strange things happening under GNOME as well (multiple devices shown in nautilus for a single device - e.g. for a firewire ipod - /media/ipod /dev/sda1, /dev/sda3 only one of which is a 'real' device, and two of whhich pop up an error dialog when clicked on. Trying to diagnose and fix udev/hal/hotplug problems is just a nightmare.

My hard drive is constantly blinking with Breezy, I have no idea what is causing this as the system load is minimal and there seems to be no easy way to tell which processes are busiest w/regard to disk i/o. No excess logging output which i would normally think of either. Possibly this is the reason for slow HDD performance reported by others.

GNOME smb share browsing now prompts me for authentication (credentials i dont even have) just to browse the network, while kde browses it anonymously with no problem. Hoary worked fine.

I agree with the parent poster. Breezy has real problems, and I think you'd be a fool to install this distro if you expect a positive and smooth user experience at this point.

This isn't Linux for Human Beings, its Linux for nerds with way too much time on their hands, because I can't see how anyone else would be happy with this distro.

---

### Post by Cathbard on 2005-10-18
[QUOTE=BLTicklemonster]Yeah, as a matter of fact, it's printed out sitting on top of my computer from last Friday. Forgot to take it home this weekend. You can bet it's going home with me tonight, though. 

Hey, is there anything special I should know, like anything nv related that ought not be on there?

Thanks.[/QUOTE]

Not that I know of. Mine is just like I posted and it seems to work fine.

Back on topic:

I think that Ubuntu's philosophy of distributing software free is reason enough to support it. If you find things broken I'm sure the developers would love to hear CONSTRUCTIVE criticism. Isn't that the whole idea of open source?
I live in the Australian bush out of the range of broadband even. i couldn't be more remote unless I moved to Easter island. Regardless of this they will gladly send me a pile of professionally printed discs for free. And it's REAL free, they don't even charge postage. Who else does that?
Computing for real people. A chance for everybody to have a working computer without being raped and pillaged by corporate software houses. Keep that in mind before you start bashing Ubuntu. Be constructive, you're getting a LOT more than you are paying for.

---

### Post by TiMBuS on 2005-10-18
Personally, I've found Breezy to be FAR superior to Hoary.
Hoary couldn't detect my sound card, Hoary couldn't dualboot windows (didn't map hd1 to hd0), Hoary had display issues, Hoary often crashed when I used PPPoE, and Hoary spat the dummy with kernel module compilation. Breezy is just fine with all of that (except I needed to get gcc-3.4) and maaan, am I happy I'll never have to remake and reinstall ALSA drivers again.

---

### Post by entangled on 2005-10-18
Although there are obviously people with problems I have to say my install of Breezy has been easy and completely error-free. 

I installed the preview iso and then did the final upgrade using Synaptic.

I found that sound worked well (it was flaky before), networking with windows was fine - my wireless card now works all the time instead of intermittently, video is OK, DVD burning is good (now using Graveman), printing is OK, camera is detected, card reader is detected, flash detected, DVDs mounted, etc. All this with no configuration from me.

This is the most trouble-free (boring?) workstation installation I have seen, and I install and set up Windows boxes, of several kinds, for a living. 

Congratulations to the Ubuntu developers and packagers.

---

### Post by entangled on 2005-10-18
Just a thought on those who have problems. 

If you are running on a chipset that Linux didn't recognise (too new, or too specialised or just failed to read info from motherboard) you will get very inefficient disk operation and the system will misbehave. You will get lockups, clock running slow, hang ups. This might be the cause of the problem for some people.
If your system worked before but not now then it may just be bad luck during the early stage of a new install. You could try again.

Has there been anyone who had a working install that has been wrecked by an apt-get upgrade? The chipset problem is less likely to happen in that case.

---

### Post by BLTicklemonster on 2005-10-18
Ubuntu sets up initially with absolute total ease. Better than Windows could ever try to be. On my machine when loading XP, I have no sound until I install my soundblaster drivers. Ubuntu not only loaded up with everything working great (my biggest problem is that I can't leave well enough alone, well, actually, the video drivers aren't good enough for gaming, but are great for every day use), but this ALSA thing is absolutely in-freaking-credible. For the first time, I have access to the surround sound functions my card supports at all times. The headset is just stereo, but the sound when set to surround is absolutely beautiful.

I can say that no matter my missgivings, if things go the way they are, Mr. Gates needs to find himself another field of endeavor. This is the way things should be. If knowlege should be exchanged freely, then the means to exchange it ought to free as costless as possible. Ubuntu and the like go a long way towards this.

How primitive a machine will ubuntu work on? Can you imagine all the old machines out there that kids in impoverished neighborhoods could be using if they had an OS that wasn't technically Illegal?

---

### Post by mriedel on 2005-10-18
[Breezy Badger upgrade destroyed two of my machines]("http://www.ubuntuforums.org/showthread.php?t=78363") and [the livecd doesn't work for me]("http://http://www.ubuntuforums.org/showthread.php?t=78366")

> Strongly recommend against installing Breezy

It seems there are a lot of problems with Breezy. I think it shouldn't have been released in this condition.

---

### Post by Psquared on 2005-10-25
[QUOTE=afonic]ROFL!

Seriously, I am sorry that you have trouble, but Breezy has updated many important components (X.org and more) that most people don't realise, so when they have problems they just say "Breezy" is buggy. 

Being an experienced Linux user, I was able to get Breezy running like a charm both in my PC and laptop. I had to mess with some settings and spend about a day testing, but in the end I have a system a 100 times more stable than what Windows will ever be.

If you want to use Linux, accept you need to spend some time configuring everything, it's really rare to get what you need just after the installation. 

Good luck.[/QUOTE]

I'd pretty much agree with everything above. Xpee is still on my laptop, but I only use it when i want to play backgammon. That's not to say I have not had issues with Breezy - mainly it was getting wireless to work. Now that I'm over that hurdle the only thing that noodles me is power management and font displays. My linux fonts always look fat. Windows fonts are sharp and crisp. I've fiddled with the font settings and I have it about as good as I can get it -- which is really not too bad.

---

### Post by BLTicklemonster on 2005-10-25
I have had the absolute rottenest time getting ubuntu set up, but I wouldn't have traded all the cussing and fretting for anything in the world. 

I have learned so much in the past few weeks, it's incredible. I never thought I'd be able to do the stuff I can do now. If Ubuntu hadn't been so easy to set up in the first place, I'd have never persued it. 

But now I'm satisfied with it enough that I'm going to put it on my kid's two computers. Gonna have to do a hard sell on mama, but that's okay if she wants to stay with MS, because she's addicted to those silly MSN games, unlike that silly UT game I'm addicted to.

I'm happy now.

---

### Post by MetalMusicAddict on 2005-10-25
[QUOTE=BLTicklemonster]I have had the absolute rottenest time getting ubuntu set up, but I wouldn't have traded all the cussing and fretting for anything in the world. 

I have learned so much in the past few weeks, it's incredible. I never thought I'd be able to do the stuff I can do now. If Ubuntu hadn't been so easy to set up in the first place, I'd have never persued it.[/QUOTE]
This is how I felt after finding Ubuntu. In the past I had no luck with most linux distros. You need those little victories to see how things work to apply then to other problem. Ive learned so much that Ubuntu will have a place in my home for a long time. ;)

I didnt convince my wife. I made her. Now she doesnt care. She mostly surfs. :)

---

### Post by JasonH on 2005-10-27
Obviouisly Breezy wasn't exactly the best name to give this distro version.  Right now my computer is completely unusable due to the upgrade to Breezy (I'm using a friends computer at the moment), but the only way I'll be changing is if I can't fix the problem.  I have a friend that said he could SSH into my computer and install SuSe for me.  I'd really much prefer Ubuntu because it's what I'm used t and it's what I like.  The real Ubuntu fans will fight it out and work through the problems.  These bugs could be considered tests of loyalty to the distro.

---

### Post by ipn1nj4 on 2005-10-27
Sorry to hear about your troubles. I hope you don't go back to the evil that is Fedora ( I am a former Fedora user as well)

I've had no problems with my any releases of Ubuntu so  far

/me knocks on wood

---

### Post by BLTicklemonster on 2005-10-27
[QUOTE=JasonH]Obviouisly Breezy wasn't exactly the best name to give this distro version.  Right now my computer is completely unusable due to the upgrade to Breezy (I'm using a friends computer at the moment), but the only way I'll be changing is if I can't fix the problem.  I have a friend that said he could SSH into my computer and install SuSe for me.  I'd really much prefer Ubuntu because it's what I'm used t and it's what I like.  The real Ubuntu fans will fight it out and work through the problems.  These bugs could be considered tests of loyalty to the distro.[/QUOTE]
I had two hard drives with Ubuntu, one with Hoary, one with Breezy. The problems I was having was trying to get nvidia drivers installed, and I decided to use Breezy for that, and leave Hoary alone. Once I found Automatix, I got the nvidia driver set up correctly (aaaactually, I probably could have done well enough from synaptic, I just never noticed until later that if you install the nvidia drivers, that it says you have to enable them manually or whatever. my bad after all).

I then decided to upgrade Hoary (it was on a larger newer drive than Breezy was on). That messed things up right there. So I just installed Breezy on it, set things up the way I now know how to, and I have no problems. 

I'm sorry to hear that you had the same problem with upgrading, (actually, my problem was just networking, not system wide, but I had nothing to lose but time, and knew it would be a big pain ita to try and figure it out, to I just installed over what I had) and hope you will give Breezy a chance as a fresh installation. It's every bit as stable as Hoary was for me. (but then I'm in this for the like 3rd week or so now, so I'm not a pro)

---

### Post by BLTicklemonster on 2005-10-27
[QUOTE=Psquared]My linux fonts always look fat. Windows fonts are sharp and crisp. I've fiddled with the font settings and I have it about as good as I can get it -- which is really not too bad.[/QUOTE]


And how was that? I'd really like to know how.

(see? I told you I can't leave well enough alone!!!

"what happened?"

"I don't know, he was just fine, then he said something about fonts, and his head exploded" 

)

---

### Post by billyjac on 2005-10-27
Well have to say I have used windows 98 and windows xp with great success,had a few problems but who doesn't. This is the very first time i have tried anything other than windows and to say yes i had a few problems but the fourms here have helped my get things fixed right. I have even crashed this distro of linux many times this last month just trying to get it the way i  wanted it to work and so far still have lots to learn about linux,,,, eg. using the command line... have no clue when i first tried using it fill like i am back in school but it time to get back to my desktop and see what else the copy of breezy can do......and by the way I love breezy the one the easiest so far to set up from what i have seen

---

### Post by jesseman on 2005-10-28
[QUOTE=JasonH]Obviouisly Breezy wasn't exactly the best name to give this distro version.  Right now my computer is completely unusable due to the upgrade to Breezy (I'm using a friends computer at the moment), but the only way I'll be changing is if I can't fix the problem.  I have a friend that said he could SSH into my computer and install SuSe for me.  I'd really much prefer Ubuntu because it's what I'm used t and it's what I like.  The real Ubuntu fans will fight it out and work through the problems.  These bugs could be considered tests of loyalty to the distro.[/QUOTE]

I'm sorry, I have only read the first 4 pages of this topic, but I must add my 2 cents. I currently have a 4 year old laptop next to me, running Fedora Core 4. This laptop has flawlessly installed many a distro, including all of the major ones, as a testbed for my a64 desktop. All things being equal, Fedora is a great distro at default, as well and SuSE, Mandriva, and the like. However, any experienced linux user will tell you that rpm hell is real. 

Your problems with Breezy sound easily fixed with competent Googling and use of the Ubutu wiki. Nothing good comes without effort, as many WinXP users will attest. Going from Ubuntu to Fedora sounds the same. The benefits of the Debian system far outweigh its problems, and if you're having difficulty in Ubuntu you can only dig yourself deeper by moving to an rpm based distro (experience, not this poster, is talking).

The appropriate use of error logs and accurate descriptions are necessary. Blanket descriptions of Breezy as unusable are unproductive and useless. Instead of getting worked up, state your problem clearly and this insanely huge userbase WILL solve your problem.

Goodluck with linux, and I hope all your gaming/office/desktop/eyecandy needs are satisfied nearly as well as mine have been under Breezy. Enlightenment, Fluxbox, Openoffice, Wine, CedegaCVS, alien ... where do the possibilities end?

---

### Post by ratsalad on 2005-10-31
I'm not sure if anyone has said this or not. I had some issues with the Nvidia driver in restricted on my Athlon XP system. What I did was upgraded the kernel and restricted modules from the default installed -386 version to the -k7 versions and it works fine.

As for this Linux versus Windows talk, you guys have to remember that up until just a few years ago it wasn't so much about pleasing the average computer user. The general attitude had always been more like "RTFM, if you can't take the heat stay out of the kitchen". The concept of bringing Linux to the desktop, easy for all is still pretty new (in my mind at least). But it's undeniable that some pretty amazing progress has been made over the last few years. I just think you end users need to keep in mind, none of this was ever really intended for you. This is a fairly new direction for Linux.

I'm sorry if this sounds like a lecture. Me being new to the Ubuntu forums and all, this is some way to introduce myself :)  I may get on my soapbox from time to time in response to something like this. To offer some explanation; I've been a Linux user for nearly 10 years now, started out on Slackware Linux, and in more recent years Gentoo, Debian, and now Ubuntu.

---

