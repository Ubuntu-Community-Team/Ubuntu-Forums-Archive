---
title: "Problem with Firefox and YouTube! Help!"
date: 2007-05-23
forum: General Help
---

### Post by DcThePurger on 2007-05-23
I recently just upgraded to the new version of Ubuntu, which is 7.0.4 I think. Whenever I use YouTube with Firefox, sometimes the loading would just freeze on me and I would have to force the browser to close. Could anyone tell me why this happens? So far all the other sites I use work fine, but the only problem is YouTube.

---

### Post by atlfalcons866 on 2007-05-23
do you have flash?

---

### Post by DcThePurger on 2007-05-23
yes, flash is already installed in my Firefox.

---

### Post by atlfalcons866 on 2007-05-23
what do you mean by upgraded?

you upgraded from edgy eft

or you did a clean install

---

### Post by DcThePurger on 2007-05-23
it was clean install.

---

### Post by iver2435 on 2007-05-23
Try installing the "Ubuntu Restricted Extras" package and see if that helps.

Go to "Add/Remove" and then list "All Available Packages".  Click "Other" on the left and search for "Ubuntu Restricted Extras"

READ THE DISCLAIMER IT FLASHES YOU BEFORE INSTALLING.  I don't want to hear anyone say I FORCED you to install it, merely a suggestion to help troubleshoot  ;)

---

### Post by DcThePurger on 2007-05-23
I installed that extra stuff but still YouTube keeps freezing.

---

### Post by DcThePurger on 2007-05-24
I need help plz. Why is YouTube freezing on me.

---

### Post by DcThePurger on 2007-05-24
anyone out there? HELP!

---

### Post by pragmatine on 2007-05-24
It is hard to help when you don't give us any real information as to the problem. Please try and explain it in more detail - perhaps it is a problem with your internet connection and not flash itself?

---

### Post by DcThePurger on 2007-05-25
I know that it's not my internet connection because whenever I use Windows, Firefox doesn't freeze on me when I'm on YouTube. However, most of the time YouTube freezes on me when I'm using Firefox on Ubuntu.

---

### Post by DcThePurger on 2007-05-25
you guys better help me cause I'm gonna switch back to Windows if someone doesn't.

---

### Post by DcThePurger on 2007-05-25
um...any1 out there?

---

### Post by AlanRogers on 2007-05-25
I have a similar issue, in that Firefox will just shut itself down for no apparent reason, sometimes with a bug report, often not. I've filed a bug report but, even having installed DBG packages, the trace isn't apparently very helpful. I'll post the bug number and the trace file later this evening but, if there's anyone else out there experiencing similar symptoms, chime in and add circumstances, so we can try and narrow it down.

DcThePurger : Consistently bumping the thread the top in the manner that you're doing, by posting screams for help without any additional information or evidence that you're trying to get to the bottom of it yourself will likely be ignored, as it has been. Add some value to each post and people are more likely to come to your aide.

---

### Post by Big_Croc7 on 2007-05-25
> **DcThePurger said:**
> you guys better help me cause I'm gonna switch back to Windows if someone doesn't.

The following two threads might be useful to you:

[http://ubuntuforums.org/showpost.php?p=1488521&postcount=1](http://ubuntuforums.org/showpost.php?p=1488521&postcount=1)
[http://ubuntuforums.org/showpost.php?p=1488813&postcount=2](http://ubuntuforums.org/showpost.php?p=1488813&postcount=2)

---

### Post by DoktorSeven on 2007-05-25
To really help; the Linux version of Flash 9 seems to be buggy with certain setups.  It is for mine.  I've found that YouTube is particularly bad with triggering the bug for some reason.

It does seem to do so less often in Konqueror and Opera, so you might want to try those alternative browsers.  Flash 7 didn't crash on me, but it's old and won't work on all sites (and I'm not even sure if YouTube has changed over to requiring Flash 9 or not).

So basically the issue here is the Flash player, unfortunately.  You could try installing the Windows version of Firefox and Flash 9 with Wine and seeing how that works for you, alternately.  Sadly, there's no perfect solution here, and the only way to fix is to tell Adobe about it.  I've gotten to the point where I avoid Flash and YouTube as much as possible anyway.

---

### Post by AlanRogers on 2007-05-27
> **DoktorSeven said:**
> So basically the issue here is the Flash player, unfortunately. You could try installing the Windows version of Firefox and Flash 9 with Wine and seeing how that works for you, alternately.Okay, thanks for the heads-up. It also seems to affect Evolution on my machine, so I'll uninstall all Flash stuff and let you know how I got on.
 
Thanks again.

---

### Post by FerhatBingol on 2007-05-28
I had the same problem. It was about sound cards drivers. I am GUESSING the problem was this...

I setup the Ubuntu 7.0.4 and setup the FlashPayer on Firefox 2.0. After THAT I wanted to setup some Video/Audio software than I have seen that ALSA mixer is not working very well. All software using the Audio option was freezing. So I changed the setting to OSS mixer and all of the problems have gone away  accept Firefox, it continue to crash in youTube. 

I understood that the Flash Player was keeping the ALSA mixer selection in its memory I did everything to find out where to change it and finally I guessed that it might go away if I do the flash player installation again cause probably setup scripts checks for the default mixer option. 

Well, it worked... I have no problem now.. It is also in my blog (nothing more than I have written here)

Hope that helps...

[http://linux.ferhatbingol.com/?p=13](http://linux.ferhatbingol.com/?p=13)

---

### Post by AlanRogers on 2007-05-29
> **FerhatBingol said:**
> Well, it worked... I have no problem now.Thanks FerhatBingo. My efforts were to no avail, so I'll try this now. I've uninstalled Firefox Flash plugin but I wasn't aware of the ALSA issue, so I'll explore at the weekend.

---

### Post by HarveySchmidlapp on 2007-05-29
> **DcThePurger said:**
> I recently just upgraded to the new version of Ubuntu, which is 7.0.4 I think. Whenever I use YouTube with Firefox, sometimes the loading would just freeze on me and I would have to force the browser to close. Could anyone tell me why this happens? So far all the other sites I use work fine, but the only problem is YouTube.

Can you tell what version of Flash is installed?  I know there was a bug with one or more beta versions of the Flash 9 player where videos would play for two seconds and then freeze.

-- 
HLS

---

### Post by Crafty Kisses on 2007-05-29
> **DcThePurger said:**
> you guys better help me cause I'm gonna switch back to Windows if someone doesn't.

That's the best comment I've heard all day. :p

That really makes me angry, people are trying to help you and all you can say is "Help me or I'm switching back to Windows" go ahead switch. Ubuntu is 3000x better than Windows anyway, so you're just hurting yourself.

---

### Post by chriztofur on 2007-05-29
Actually, I believe I'm having a similar issue. Everything was working fine...and then I accidently corrupted my linux partition..so, I reinstalled, and for the most part, firefox + flash works fine, but if I try to watch around 3-4 youtube videos in a row, by the time i try to hit the next one, the browser just freezes..haven't figured it out yet. 

I've uninstalled and reinstalled flash to no avail. Hmm..

---

### Post by chriztofur on 2007-05-29
> **chriztofur said:**
> Actually, I believe I'm having a similar issue. Everything was working fine...and then I accidently corrupted my linux partition..so, I reinstalled, and for the most part, firefox + flash works fine, but if I try to watch around 3-4 youtube videos in a row, by the time i try to hit the next one, the browser just freezes..haven't figured it out yet. 

I've uninstalled and reinstalled flash to no avail. Hmm..

actually, i don't know about you guys, but this bug accurately describes what i'm seeing: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/98688](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/98688)

---

### Post by hungrysam on 2007-05-29
I don't think that it's a problem with the Internet connection, because the same thing happens to me, and I am probably not using any similiar Internet connection. (unless Dc is in Lima, Peru)  I can't provide many details really, but I have had Firefox just freeze up whenever it is on a site like youtube, myspace, or hi5.  The interesting thing to me is that the hi5 page didn't have any streaming av.  And like Dc, I have the restricteds installed and flash.

---

### Post by steveneddy on 2007-06-05
I found an answer and it is posted on [this thread]("http://ubuntuforums.org/showthread.php?p=2787287#post2787287").

It worked for me and should work for most everyone.

-SE

---

### Post by devicerandom on 2007-06-14
Tried. Does not work for me. Also other suggestions (depth=24 bit, Composite off) do not work

I'm using Kubuntu Feisty (x86) with Firefox. Flash videos and other heavy Flash content freezes my browser. Video card is an ATI X300SE, managed by the OSS ati drivers.

Any new hint about finding the root of this problem?

---

### Post by DcThePurger on 2007-06-27
Thanks for trying to help, but none of these tips helped me out except for the ALSA drivers one I didn't try yet. I'm still trying to figure out how to change the drivers to OSS. Can anyone help?

---

### Post by FuturePilot on 2007-06-30
Flash always freezes Firefox on me too. It's particularly bad on YouTube. It's driving me nuts. Doesn't happen in Windows:(

---

### Post by leighleigh on 2007-06-30
I'm no techie but I fixed my UToob problem and maybe this will help you too.  My problem was that I suddenly could not load UToob _at all_ with Firefox (Explorer was OK) - I kept getting the dreaded 500 Internal Server Error message.  Clearing the cache did not fix the problem but Clearing Private Data did.  (Firefox Tools > Clear Private Data).  [All that was after reinstalling Firefox and Adobe Flash Player.]  Good Luck.

---

### Post by Totentanz on 2007-07-12
> **steveneddy said:**
> I found an answer and it is posted on [this thread]("http://ubuntuforums.org/showthread.php?p=2787287#post2787287").

It worked for me and should work for most everyone.

-SE


Awesome, that solved my problem, thanks :D

---

### Post by Stoffer on 2007-08-01
My issue is that whenever I'm playing a flash video on youtube or collegehumor.com, my CPU is consistently at 100% usage.  It spikes to 100 with other flash applications.

Can someone tell me how to uninstall flash altogether and start from scratch?  I couldn't find it listed in firefox add-ons, or in synaptic.  I went ahead and installed the flashplugin-nonfree package in Synaptic, but that didnt' help at all so I got rid of it.

Any help would be greatly appreciated.  I don't know if trying to reinstall flash will fix anything, but it's worth a try.

---

### Post by capink on 2007-08-02
People having this problem can try installing two firefox extensions: flashblock and unplug. The first extension will prevent firefox from playing flash media. And the second will allow for downloading the flash movie to harddisk and play it with something like mplayer.

I know this is not the best solution, but it can be used if nothing else work

---

### Post by o2blom on 2007-08-25
Same problem here. Running Kubuntu 7.0.4 on single core CPU.

---

### Post by peebly on 2007-08-25
hello

I have had the same problem for a while.

out of interest has anyone installed the new beta version of flash from adobe labs.

wondering if the problem still exists with that version.

thanks

---

### Post by FuturePilot on 2007-08-26
> **peebly said:**
> hello

I have had the same problem for a while.

out of interest has anyone installed the new beta version of flash from adobe labs.

wondering if the problem still exists with that version.

thanks
I tried to, but it didn't work very good. I couldn't push any buttons, like Play/Pause, FF etc. They didn't do anything when I pushed them.

---

### Post by logreeval on 2007-08-27
I have the EXACT same problem :(

I will just be browsing and all of a sudden Firefox just stops, it will eventually ask me to force quit...

---

### Post by davedumas0 on 2007-08-29
i have the exact same problem i would love if somebody could help us

---

### Post by brk3 on 2007-09-01
I have this problem too, you watch a video on youtube and then click back or on another link while it is playing and the broswer just crashes. It is crazy there is no simple fix for this yet as it has being a problem for months

---

### Post by [Alsharifi] on 2007-09-03
all these people with this problem and no soultion...what have we come to..


lol im one to  talk,ive never help fixed a problem :P

good luck!

---

### Post by cs2excalibur on 2007-09-05
I have the damn same problem too.  1.) flash is installed.  2.) the problem is that, say it's loading and it'll stop at any point and basically stop.  3.) when you stream to that point the player stops and u have to wait 1-2min until it continue.  4.) half the time it doesn't continue and just stay there.  So yea this is a big big big issue if other users are having the same problem.  I would love it if i can fix it up.  I hate to use xp again...another crack xp coming up.

---

### Post by littleiffel on 2007-09-06
Hy I had the same problem as described above. Please check that There is only one instance of flash-plugin enabled.

Visit the page about:plugins in firefox.(Type ```
about:plugins
``` in Firefox as URL)

And check that there is only one Flash-Plugin enabled

---

### Post by aulio on 2007-09-06
It seems that I have both *Shockwave Flash* and *FutureSplash Player* enabled. How can I disable one of them? Which one I should keep?

---

### Post by littleiffel on 2007-09-06
No that's fine. This is one single instance of the Flash-Plugin. Don't you have another entry in 

```
about:plugins
```

like
[B]
Shockwave Flash[/B]

File name: libflashplayer.so
Shockwave Flash 9.0 r60

???

---

### Post by Joliet_Jake on 2007-09-06
this is courious.
when i start ANY flash video, it freezes on the third second.
Never happened before.
occurring both on firefox and konqueror.
just updated kubuntu fiesty.
firefox re-installed.
flash plugin Shockwave Flash 9.0 r48

---

### Post by aulio on 2007-09-06
No, I have only:

```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r31
```

So, that's not the problem.

But I still think it's flash which crashes the firefox.

---

### Post by FuturePilot on 2007-09-06
> **littleiffel said:**
> Hy I had the same problem as described above. Please check that There is only one instance of flash-plugin enabled.

Visit the page about:plugins in firefox.(Type ```
about:plugins
``` in Firefox as URL)

And check that there is only one Flash-Plugin enabled

Interesting. I found that I have two entries for that. Here's what I have. At the top of the page:
```
    File name: libflashplayer.so
    Shockwave Flash 9.0 r60
```
But down towards the bottom, I also have this:
```
    File name: libflashplayer.so
    Shockwave Flash 9.0 r48
```

How do I get rid of one of them?

---

### Post by littleiffel on 2007-09-07
Well I had the same problem(documented it in my blog). 

What I did is to locate every libflashplayer.so you have lying around somewhere

Enter in the terminal:

```
locate libflashplayer.so
```

I removed (but made backup) the two fiels within .mozilla/plugins/libflashplayer.so and .mozilla/firefox/plugins/libflashplayer.so

That worked for me!! But sometimes Firefox still crashes, but you noticed that stability is better, and firefox seems to respond faster

---

### Post by Joliet_Jake on 2007-09-07
i have to report that magically as they came, the problems have now vanished. :|
no idea of what happened.
i did nothing, just waited the next day.
maybe youtube fixed the code.
anyway, yeah.

---

### Post by imbjr on 2007-09-07
I have this problem. My work-around is to have firefox permanantly open on a youtube video that's paused. I put this in my third workspace out of the way.

I recall that this problem had something to do with transparancy and mention was made of the kernel, but it's been a while since I moved chasing that particular rabbit.

---

### Post by TheSe7enthSin on 2007-09-08
I getting fed up with all the crashes I constantly get. =[
Workarounds are ok, but permanent fixes are better. Where is the latter? T_T

---

### Post by MickS on 2007-09-08
My Firefox crashed from time to time on Youtube but I found if I stopped playback before doing anything else, then no more problems just make sure it has actually stopped before clicking elsewhere.

Mick

---

### Post by davedumas0 on 2007-09-10
or you could open the vid in a new tab then just close after it is over

---

### Post by TheSe7enthSin on 2007-09-17
> **davedumas0 said:**
> or you could open the vid in a new tab then just close after it is over

It could be a video in the same page, new tab or even new window...Once you close it out, the browser freezes. I'm so fed up with this issue =[

I have friends who go on my laptop and see Ubuntu for the first time. They fire up the browser, go to some site with flash embedded videos, and can't watch it because it freezes. They then get turned off a bit by Ubuntu because internet isn't working right. XD

---

### Post by TheSe7enthSin on 2007-10-01
Does anyone know if the new Flash9 that was released today fixes this issue?

---

### Post by berlinbrown on 2007-12-06
Same problem.  I even hung out in the Firefox world for a while, but they a billion of the firefox / flash / swf issues.  Submitting a bug would be pointless.

I am using FF3 beta, the day it came out and still the same issue.  FF2.0.0.8 from apt, I believe resolves the issue.  but ff2 sucks.

---

