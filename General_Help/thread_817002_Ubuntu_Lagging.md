---
title: "Ubuntu Lagging"
date: 2008-06-03
forum: General Help
---

### Post by decipher on 2008-06-03
Hi There

I am Windows user trying to move over to Ubuntu. I have been developing PHP for a while now and thought it was about time to start developing my apps on the correct platform. (sad isn't it?)

I am trying my utmost best to make the transition but it seems Ubuntu is just not happy with my box. 
I'm using Ubuntu 7.10, my Box is an HP Pavilion Slimline with AMD Sempron 3600 processor, 800mb RAM, Nvidia GeForce 128MB Graphics Card. It was a bad decision purchasing this crappy thing as I cannot add more ram/change any of the cards because of the way the box is built (it's a really small desktop pc). 

So the problem is that my windows keep freezing and the whole systems lags repeatedly. For example, when using FireFox, I try to connect to a website, the browser will lag before actually trying to connect. When switching between tabs the browser will lag, even freeze, for a couple of seconds. When i'm developing using the standard Ubuntu Text Editor, sometimes the cursor lags. This makes life impossible for me, there is obviously something wrong with my setup.

I wanted to know how I can troubleshoot my issues. To me it seems like it's a ram issue, but surely I have enough ram. It appears all my hardware drivers ares setup correctly, so i'm lost as how to solve this issue.
I have Windows Vista on my partition and it runs smoothly with none of these issues.
Do you think installing Ubuntu 8 will solve this issue? 
I have delayed posting on this forum for some time, but now this is my last resort before moving back to developing on windows. Any suggestions would be greatly appreciated :)

---

### Post by Kevbert on 2008-06-03
Firstly, try and run the memtest on your PC.  It's an item in the Grub bootup menu.  Run it for at least 1 hour so it performs two or more passes.  Windows can run with dodgy memory (as I've found out myself).  If you think your machine is a bit slow with Ubuntu try installing Xubuntu (I'm running it on an old 512Mb PC).  It can be downloaded from [here ]("http://www.xubuntu.org/get")

---

### Post by danwood76 on 2008-06-03
If Vista runs smoothly then I would have thought GNOME should run better than it (it does on my laptop)
You could try upgrading to the latest version, it may have better support for your hardware.

-- edit --

It could be a graphics driver issue, which drivers are you using?

---

### Post by decipher on 2008-06-03
@Kevbert, i will try the memtest, i'm just installing some updates after which I will post back the results of the memtest. I have thought about trying out xubuntu, although I would like to stick with ubuntu if possible. 

@danwood76,  
I go to System>>Administration>>Screens and Graphics>>Graphics Card>>Driver = nvidia

---

### Post by danwood76 on 2008-06-03
Are you running compiz? (desktop effects)
Switching desktop effects off might help you.

---

### Post by Kevbert on 2008-06-03
Regarding Firefox.  I assume you're running 2.0.0.14 and not 3b5 (which can give problems).  You could try Swiftweasel which is supposed to be a streamlined version of Firefox.
If you're running Compiz, not installed by default(7.10), you're better off without it as it will eat resources.  Uninstall with Synaptic Package Manager.  It comes with 8.04 and is installed by default.
How big is your swap partition ?  I'd make it 2.5 x RAM = 2Gb.  You can use this to hibernate the system which will improve boot-up times.

---

### Post by decipher on 2008-06-03
@Kevbert, I have run memtest and it passed 2 tests successfully. I am using FF 2.0.0.14 and unfortunately I cannot switch browsers at this stage due my dependence on certain FF plugins, although I will give Swiftweasel a look, thanks for the suggestion ;)
@danwood76, although I did not have any visual effects enabled, I have removed compiz completely.

OK I have noticed something that might push me in the right direction. The point at which my windows freeze is when my CPU usage jumps to 100%, this is most distinctive when using firefox. (see attached). Notice the peaks at 100%, this is the exact point when my windows freeze. Could this be because of my crappy AMD chip or something deeper?

---

### Post by Kevbert on 2008-06-04
If you think it's Firefox, when does this occur ?   when you are looking at flash/other videos perhaps ?  A bug report was written on launchpad regarding computer lockups.  Mine occurred with FF 3b5 which came with Hardy (hence I've downgraded to Gutsy).  It may be worth having a look at [launchpad]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=Firefox+freezes&search=Search+Bug+Reports&field.scope=all&field.scope.target=") to see if a similar bug has been reported.

---

### Post by decipher on 2008-06-04
Kevbert, tbh it is most apparent when viewing Facebook, but not when actually viewing the pages, only after I close the pages, I guess it has something to do with clearing javascript variables to free them from memory? Is it normal that this requires 100% CPU usage? 
I cannot directly relate the problem to flash and videos like others have, as this problem also occurs with gmail and other webpages that may/may not use flash. 
Thank you for your help and suggestions, i'm going to take a look through the launchpad bugs and see if I can spot anything similar.

---

### Post by Kevbert on 2008-06-04
I did notice there were some java script bugs raised.  What are you using to check CPU usage ?  You may get the odd spike but if 100% is happening for a long period of time you've probably got a bug.

---

### Post by decipher on 2008-06-04
I using System Monitor to check my CPU usage, and I do get very long 100% CPU spikes, you can check my previous attachment [here]("http://ubuntuforums.org/attachment.php?attachmentid=72842&d=1212532896").

---

### Post by Kevbert on 2008-06-04
Try using 
```
top 
```
in terminal when you think you're going to get 100% CPU usage.  Press Q to quit. I've just read another post that suggests this is a known bug.

---

### Post by decipher on 2008-06-04
Yea it freezes when "firefox-bin" process peaks over 95%, I haven't been able to spot if it actually reaches 100%. 
I managed to take a screenshot just before the process reaches critical freezing point of 95%. (see attached), if this a bug, what does that mean exactly? Is there any possible way of fixing this without changing browsers?

---

### Post by Kevbert on 2008-06-05
It looks like you may need to report a bug (this may have already been reported).  Have a look at this page [[COLOR="Red"]first[/COLOR]]("https://wiki.ubuntu.com/MozillaTeam/Bugs").

---

### Post by decipher on 2008-06-05
Thanks a lot for all the help Kevbert, i do believe I am close to sorting this out. 
At this stage I am almost certain this a FireFox issue. When I notice long 100% CPU spikes (i'm constantly monitoring now), and I have my browser open & playing music etc at the same time, all I need to do is close FireFox and my CPU usage drops considerably, and ubuntu stops lagging. 

Right now I am running firefox with a fresh profile => no plugins. (Thanks for the link.) So far, it seems to be a solution, although firefox process does peak a little when viewing massive pages, it does not hang anymore, and the CPU usuage does drop back down pretty quickly. 
So, perhaps it's a FF **plugin** issue? 
Here's what I was using:
Web Developer - by Chris Pederick
HTML Validator
FireBug + Yslow (Only enabled for certain offline sites)

Not sure if anyone has had similar issues using one of these plugins? 

I'm going to keep using a fresh FireFox and see if I encounter any similar issues, if not then I have to assume it's one of the plugins munching my CPU.

---

### Post by peakshysteria on 2008-06-05
Can you post your addons and plugins please? (infolister is a nice addon for doing this automatically).

---

### Post by decipher on 2008-06-05
I was using the default FF theme, with the following addons:

[Web Developer]("https://addons.mozilla.org/en-US/firefox/addon/60") - by Chris Pederick
[HTML Validator]("https://addons.mozilla.org/en-US/firefox/addon/249")
[FireBug]("https://addons.mozilla.org/en-US/firefox/addon/1843") + [Yslow]("http://developer.yahoo.com/yslow/") (Only enabled for certain offline sites)

---

### Post by Kevbert on 2008-06-05
Hi.  Just checked your links.  It says 'HTML Validator is not available for Linux'.  Maybe this is the problem.  So you haven't got any plugins for flash  ?

---

### Post by buntunub on 2008-06-05
> **decipher said:**
> Thanks a lot for all the help Kevbert, i do believe I am close to sorting this out. 
At this stage I am almost certain this a FireFox issue. When I notice long 100% CPU spikes (i'm constantly monitoring now), and I have my browser open & playing music etc at the same time, all I need to do is close FireFox and my CPU usage drops considerably, and ubuntu stops lagging. 

Right now I am running firefox with a fresh profile => no plugins. (Thanks for the link.) So far, it seems to be a solution, although firefox process does peak a little when viewing massive pages, it does not hang anymore, and the CPU usuage does drop back down pretty quickly. 
So, perhaps it's a FF **plugin** issue? 
Here's what I was using:
Web Developer - by Chris Pederick
HTML Validator
FireBug + Yslow (Only enabled for certain offline sites)

Not sure if anyone has had similar issues using one of these plugins? 

I'm going to keep using a fresh FireFox and see if I encounter any similar issues, if not then I have to assume it's one of the plugins munching my CPU.

FF is indeed causing you some issues, or some dependencies for FF anyway. Since there are several bugs already posted against FF your best bet for now would be to use a different browser until these get sorted out in future updates. If your running Ubuntu, try using Epiphany, which is the GNOME sponsored web browser and thus, is really the best default browser to use within the GNOME environment. Its not got all the flashy-bang bells and whistles that FF has, but its very fast and efficient and does the job quite well.

---

### Post by decipher on 2008-06-05
> **Kevbert said:**
> Hi.  Just checked your links.  It says 'HTML Validator is not available for Linux'.  Maybe this is the problem.  So you haven't got any plugins for flash  ?

I think this might be where the problem lies, I have installed FireBug and it seems to be doing ok, I'm going to proceed to installing all other addons (excluding HTML validator of course) and see where that gets me. (If only I had taken the time to read the info on that page, i'm ashamed and embarrassed. :-#)
[edit] Using infolister, the following i have the following plugins:
*  DivX® Web Player
* QuickTime Plug-in 7.2.0
* Shockwave Flash
* Totem Web Browser Plugin 2.20.0
* Windows Media Player Plug-in 10 (compatible; Totem)

Although i don't believe the problem lies therein.


> **buntunub said:**
> FF is indeed causing you some issues, or some dependencies for FF anyway. Since there are several bugs already posted against FF your best bet for now would be to use a different browser until these get sorted out in future updates. If your running Ubuntu, try using Epiphany, which is the GNOME sponsored web browser and thus, is really the best default browser to use within the GNOME environment. Its not got all the flashy-bang bells and whistles that FF has, but its very fast and efficient and does the job quite well.

One of the main reasons why I use FF is for the extensions/addons, mainly for the web developer extension and for FireBug. I rely heavily on these addons for development purposes, so changing browsers at this point is really not an option.

---

### Post by danwood76 on 2008-06-05
Mozilla dont make the addons and its probably a bug in the addon when using FF 3.
Downgrade to firefox 2 and your addons might work better.

---

### Post by decipher on 2008-06-05
I am using FF2 at this stage.

I do believe the problem lies in the fact that the html validator states that it is ["not available for linux"]("https://addons.mozilla.org/en-US/firefox/addon/249") although that statement is quite brief in the sense that it did work, it just didn't work very well. If I scroll down the page I see it does state that it would work for linux. This conflicting information leads me to believe this might be the source of the issue.
Saying that, I need to do some more testing to pinpoint that indeed that is where the problem lies.

---

### Post by danwood76 on 2008-06-06
I read that page and it says:
> 
For technical reasons, the extension is available in this site only for:
- Windows
- Linux 32 bits

So I guess its compatible with 32 linux apparently.
It also says:
> 
This Website shows only the OS version that your browser uses. It contains only a limited number of platforms. (Windows, and Linux 32bits)

You can find the complete list here:

[http://users.skynet.be/mgueury/mozilla/download.html](http://users.skynet.be/mgueury/mozilla/download.html)

So it looks like you need to make sure you install the correct version.

---

### Post by decipher on 2008-06-09
I'm sad to say that this issue is not directly related to the HTML Validator plugin. Darn. :( I have been using a new profile of FF without the addon and FF continues to freeze as it munges close to 100% CPU. I must say though, this is only apparent with some sites, mostly, ahem, Facebook. I have been keeping an eye out, and in the past week I haven't been able to replicate such massive CPU usage with other sites.
To be honest, I don't think I have noticed this behaviour with any other site, or at least it hasn't affected my browser enough for me to notice. 

I'm thinking it's a flash issue as suggested (i think Facebook uses flash for their chat thing, mostly for the sounds, much like gmail), although saying that, this doesn't happen when viewing flash on other sites, eg I have no problem with youtube. 

So this is one of those "trial and error" scenarious, as I try pinpoint the exact source of the issue.. I might never find out why FF is doing this, but I know this much: there is an issue with Firefox in ubuntu. I'm going to wait for FF3 stable before I upgrade, hopefully (and that's very hopeful), this issue will be fixed with the new version.

---

### Post by abdusamed on 2009-10-11
though its a old thread.. i too having problems with laggin the thing is ..i think my computer is not able to render the windows fast enought.. cuz when i switch windows.. it looks like its creating them to show me.. i did hardware driver checkup..but it came out negative.. im using p4 with with some random intel card..plzzz help! also..i need to control my fan speed to keep it quite.. using xubuntu 9.04!

---

### Post by fela on 2009-10-11
One word: CrunchBang.

Another word: Gentoo.

Oh, maybe Arch, or DamnSmallLinux, or Puppy or...yeah.

---

### Post by abdusamed on 2009-10-12
but i like xubuntu interface..im used to ubuntu 9.04 on my dual core.. ISN'T xubuntu designed to run on slow pc...its p4 with ram 256 mb

---

### Post by 3rdalbum on 2009-10-12
Xubuntu is slightly more lightweight than Ubuntu, but it still won't be fast with old Intel integrated graphics and 256mb of RAM.

Try upgrading the RAM to 512 or more, and try Ubuntu 9.10 as the Intel drivers are in better shape.

---

