---
title: "Solution to flash-related Firefox 2 crash in Edgy"
date: 2006-10-27
forum: General Help
---

### Post by distortedstar on 2006-10-27
I was sorely dissapointed when Flash caused Firefox to crash on my brand new Edgy install, but after some searching I found a solution that solved the problem for me:

In the /etc/firefox/firefoxrc file, insert this line:
```

export XLIB_SKIP_ARGB_VISUALS=1
```

I've also seen a couple more solutions that may work for you, if this doesn't:

1. Comment out the composite section in x.org
2. Change your color depth to 24 bit, if you haven't already

Hope this post helps out some other frustrated people!

Launchpad bug discussion: 
[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911)

---

### Post by unwoken on 2006-10-27
thank you distortedstar.

you are a gun.....

very happy now!  :D

---

### Post by wildframe on 2006-10-27
Yes thank you very much distortedstar

Just what the doctor ordered :D 

Cheers...John

---

### Post by davebgimp on 2006-10-28
> **wildframe said:**
> Yes thank you very much distortedstar

Just what the doctor ordered :D 

Cheers...John

Changing to 24 color depth worked perfectly.

---

### Post by teofilis on 2006-10-28
Thank you. I also had the same problem, but it's all right.

Tomas

---

### Post by Rhubarb on 2006-10-28
> **davebgimp said:**
> Changing to 24 color depth worked perfectly.
Yeah, just the 24 bit colour depth fixed it up for me too :)

---

### Post by bartbouter on 2006-10-29
Editing the /etc/firefox/firefoxrc works for me. :D 

Thnx

---

### Post by KHatfull on 2006-10-30
Fresh Edgy install...the firefoxrc edit worked here for me too.  I have a Thinkpad with Neomagic video so 24 bit color isn't an option for me as the X.org Neomagic server doesn't work properly at 24 bit.  The edit though worked just fine by itself.  Thanks.

---

### Post by nandasunu on 2006-10-30
Thanks!

---

### Post by goldenatom on 2006-10-30
What exactly does adding that line do? Just curious.

---

### Post by goldenatom on 2006-10-30
Actually, while we're at it, why does changing to 24-bit color also seem to solve the problem? Again, just sort of curious.

---

### Post by dstan on 2006-10-30
> **distortedstar said:**
> I was sorely dissapointed when Flash caused Firefox to crash on my brand new Edgy install, but after some searching I found a solution that solved the problem for me:

In the /etc/firefox/firefoxrc file, insert this line:
```

export XLIB_SKIP_ARGB_VISUALS=1
```

I've also seen a couple more solutions that may work for you, if this doesn't:

1. Comment out the composite section in x.org
2. Change your color depth to 24 bit, if you haven't already

Hope this post helps out some other frustrated people!

Launchpad bug discussion: 
[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911)

I found this with a search, should probably be a sticky.

---

### Post by bionnaki on 2006-10-30
does this work for the linux beta flash plugin? also, how do you change color depth to 24? where is that in xorg.conf?

---

### Post by Flamekebab on 2006-10-30
Can anyone figure out which file I'd need to edit for *Flock*?

Also, what does this extra line actually do?

---

### Post by lloydlloyd on 2006-10-30
Excuse my total ignorance and uselessness, but could someone please tell me how to save the file (firefoxrc) once I've edited it?
The file opens in gedit, and I add in that extra line, then when I go to save it, it tells me I don't have permission to save the file.

---

### Post by Flamekebab on 2006-10-30
You'll need superuser permissions to save it. You could open it from the command line - **sudo gedit /etc/firefox/firefoxrc**

---

### Post by lloydlloyd on 2006-10-30
Thanks for that, except it didn't help.
I was able to enter the line in, but it's still crashing.
Now for stupid question number two: How do I change the colour depth?

---

### Post by Flamekebab on 2006-10-30
```
sudo gedit /etc/X11/xorg.conf
```

Then scroll down to near the bottom of the file and change:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34M [GeForce FX Go5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
```
to:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34M [GeForce FX Go5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    **_*24*_**
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
```

Of course, yours may be slightly different, as you'll probably not have the same monitor and graphics card as me, but you get the idea, I hope.

---

### Post by lloydlloyd on 2006-10-30
Awesome! Works a treat now. Thanks for all the help :)

---

### Post by jonbeckett73 on 2006-10-31
Thanks - I was just doing a search for this too after updating to 6.10 last night.

---

### Post by Flamekebab on 2006-10-31
My question still stands though, does anyone know how to do this for *Flock*?

---

### Post by VinnyM69 on 2006-10-31
[QUOTE=distortedstar;1672572]I was sorely dissapointed when Flash caused Firefox to crash on my brand new Edgy install, but after some searching I found a solution that solved the problem for me:

In the /etc/firefox/firefoxrc file, insert this line:
```

export XLIB_SKIP_ARGB_VISUALS=1
```

This fixed the problem with Firefox 2.0 crashing for me.
Thanks dude!

---

### Post by walicarpio on 2006-10-31
Thanks Distortedstar, you are a really MOTU (Master Of The Universe)

---

### Post by vidak on 2006-10-31
I've tried everything - the color depth was already 24bit, removed and reinstalled firefox, tried The Code (export XLIB...), reinstalled flash, downloaded-and-installed flash 9 manually, bot none worked... Then I saw in a thread to use automatix for flash-install, and it solved my problem! (...this SWF-file triggered bugs... & crash). As I saw, there is an unsolved dependency like gsfonts-idontknowwhat. However, automatix helped me a lot, and now I'm happy :D

---

### Post by hikaricore on 2006-10-31
Works perfectly :) you saved my sanity.

Although swiftfox still has problems.  I'm going to try to find a solution and when I do I'll post it here.  :)

---

### Post by hikaricore on 2006-10-31
Fixed!

assuming you're using gnome and
swiftfox is install at /opt/swiftfox

```
sudo gedit /opt/swiftfox/swiftfox
```

@ line 62 replace

```
export MOZ_PIS_API MOZ_PIS_MOZBINDIR MOZ_PIS_SESSION_PID MOZ_PIS_USER_DIR
```

with

```
export MOZ_PIS_API MOZ_PIS_MOZBINDIR MOZ_PIS_SESSION_PID MOZ_PIS_USER_DIR XLIB_SKIP_ARGB_VISUALS=1
```

Save the file and launch swiftfox and goto the dreaded gmail.com (or whatever sites you know to kill firefox/swiftfox dead), after you login you should notice swiftfox does not close for no good reason. :)

Enjoy.

---

### Post by PetRock on 2006-11-01
Thanks alot! The first one did the trick for me. Was absolutly horrified of having ruined my fresh installation of Edgy Eft

---

### Post by Dave Klinzman on 2006-11-06
Thank you Thank you Thank you!  The "export" fix worked like a charm.
:D :D :D

---

### Post by jeremyk on 2006-11-06
Tank you very much. Editing /etc/firefox/firefoxrc worked perfectly for me.

---

### Post by hockalees on 2006-11-06
I will add my thanks to the ever growing list of those who were able to get Flash 7 (and eventually 9) working thanks to Distortedstar's suggestion.

I was able to have a new install of Edgy on my son's PC work fine, however my laptop Dapper->Edgy upgrade was having trouble with Flash and FF2.0.  I did everything I could find in the forums, manual and automatic installs of the flash plugin to no avail.  Once I edited the firefoxrc file as per Distortedstar's instructions, it came up like  a pro.  I was even able to get the Flash 9 beta to work.

As mentioned by previous posters, you might want to try to install the "nofree" plugin using Synaptic or Automatix so it goes and gets the needed font(s). 

Have you considered adding this to the wiki?

Thanks again, Dis!

---

### Post by aev on 2006-11-08
> **distortedstar said:**
> I was sorely dissapointed when Flash caused Firefox to crash on my brand new Edgy install, but after some searching I found a solution that solved the problem for me:

In the /etc/firefox/firefoxrc file, insert this line:
```

export XLIB_SKIP_ARGB_VISUALS=1
```

...



u da man :mrgreen: 

This worked on dapper-to-edgy upgrade with the beta flash9

Thanks.

---

### Post by Wangsta on 2006-11-08
gedit doesn't seem to be a command for me.  It says sudeo: gedit: isn't a command.  What do i do?

---

### Post by alberto666 on 2006-11-09
But... was does exactly do the first solution?

And what is the reason of hanging with ubuntu 6.10 but not 6.06?

Anyway, now I have my [Swiftfox]("http://alberto666.blogspot.com/2006/10/swiftfox-optimizacin-de-firefox.html") running with 16 bits of color and works properly, thanks!

---

### Post by adamadamant on 2006-11-09
@Wangsta, it should be "sudo gedit ..." not "sudeo gedit ...". If that dosen't work you need to install GEdit but you should have it.

---

### Post by nematocyst on 2006-11-09
Hopefully this is a temporary workaround and not a solution.  The first method did nothing for me, adding the export to either the firefoxrc file, or modifying /usr/bin/firefox directly didn't help.

I don't see any composite section in my xorg.conf file.

Changing to 24 bit color depth indeed made the problem go away.  However, I was running 16 bpp for a reason.  I shouldn't have to give up the ability to play starcraft in order to browse with flash content.

---

### Post by amanita on 2006-11-11
I have done everything on my edgy64 what was suggested (xorg.conf, flash9, etc/firefox/firefoxrc...) :evil:  (FF crashed on every second website with flash)](*,) 
so got pissed off and since using swiftfox32 no crash at all. :mrgreen:

---

### Post by jetpeach on 2006-11-11
fixed it for me! thanks!

---

### Post by helpdeskdan on 2006-11-11
A major bug - thanks so much for posting the solution!  Why isn't it fixed yet?!  For those who aren't computer savvy to figure out that this is a flash bug and google it, this is a serious problem!  An operating system with an unstable browser would make any newbie run back to Windoze!!

---

### Post by clyderino on 2006-11-12
No luck with any of the posted fixes for Firefox. I am using "Opera" without any problems so far. Will keep checking for a fix that works on my system...

---

### Post by goldenatom on 2006-11-14
When I went to change the firefox file, I already had the extra line in there. Is this normal?

---

### Post by Greg T. on 2006-11-16
This may be fixed when Flash 9 has its next release (either another beta or the final). See this [link]("http://www.kaourantin.net/2006/10/flashxcomposite-crasher-in-x11.html") for background and their fix.

---

### Post by Jongi on 2006-11-16
I've done this anyway. I've had one flash crash in many hours of use in kubuntu edgy. But if it helps so be it.

---

### Post by littledeer1974 on 2006-12-04
> **distortedstar said:**
> I was sorely dissapointed when Flash caused Firefox to crash on my brand new Edgy install, but after some searching I found a solution that solved the problem for me:

In the /etc/firefox/firefoxrc file, insert this line:
```

export XLIB_SKIP_ARGB_VISUALS=1
```

I've also seen a couple more solutions that may work for you, if this doesn't:

1. Comment out the composite section in x.org
2. Change your color depth to 24 bit, if you haven't already

Hope this post helps out some other frustrated people!

Launchpad bug discussion: 
[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911)


Thank you so much, it works for me perfectly![http://ubuntuforums.org/images/smilies/star.png](http://ubuntuforums.org/images/smilies/star.png)

---

### Post by panki on 2006-12-06
Hi there: I have 50 computers with edubuntu and FF2, and about 150 annoyed users... will try this tomorrow and let you guys know the result.

---

### Post by loopjeremyloop on 2006-12-07
would commenting out the Composite section in my xorg.conf file disable my wonderful Beryl?

---

### Post by Get_Ya_Wicked_On on 2006-12-10
yes.

---

### Post by Ola Ericsson on 2006-12-12
Thank you Thank You Thank You

---

### Post by three_sixteen on 2006-12-13
Gah, I tried the colour depth first as I figured I ought to switch it anyways.  But it didn't work.

Once I added the line to the firefoxrc file it worked just fine.

Thanks!

---

### Post by Xswitch on 2006-12-13
DefaultDepth is 24
$ sudo cat /etc/firefox/firefoxrc shows the following:

[b]b# which /dev/dsp wrapper to use
FIREFOX_DSP="none"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See [https://launchpad.net/malone/bugs/29760](https://launchpad.net/malone/bugs/29760).
export XLIB_SKIP_ARGB_VISUALS=1[/b]

Couldn't seem to locate "Composite" Section.  Is the section actually named **Composite**?    What is in the composite section?  Here are the sections that my xorg.conf has:

Files
Module
InputDevice (I have 6 of these sections)
Device
Monitor
Screen
ServerLayout
DRI

Here's what's in my "Device" Section:

> Section "Device"
	Identifier	"ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
#Driver		"ati"
	Driver "radeon"
	Option "DRI" "true"
	Option "ColorTiling" "on"
	Option "EnablePageFlip" "true"
	Option "AccelMethod" "EXA"
	Option "XAANoOffscreenPixmaps"
	Option "RenderAccel" "true"
#Option "AGPMode" "x" <- x may be 2 or 4 depending on your system
	Option "AGPFastWrite" "on"
	BusID		"PCI:1:0:0"
EndSection

**Firefox crashes randomly.**

---

### Post by Gomek on 2006-12-30
tag

---

### Post by SZF2001 on 2007-01-01
Guys, this actually made my Flash experiences worse. The Flash sites would crash half way into whatever was playing.

I got rid of the line, but changed my monitor to 32 since it was 24. I went through at least twenty flash pages (YouTube) until it finally crashed, and has gone back to it's old ways.

It's old ways? Everytime I finish a Flash site, try to close the tab, try to open a new link outside of Flash, the browser just freezes and I have to make it force quit.

This needs to be fixed - hopefully, when a fully, stable release finally comes out, this will be cleared up - but for now it's pissing me and my friends off (I converted them to Ubuntu, and are now switching back to Windowz because MySpace freezes and such).

Any other solutions?

---

### Post by distortedstar on 2007-01-01
Sorry it didn't work, man. I've noticed that the solutions I've found seem to work about 90% of the time...but then there's that 10%. I hope some of the more knowledgeable people around here will be able to offer another suggestion.

I also share your concern about he overall stability of the distro...I think (and hope) Feisty will be quite a bit more stable and ironed out than Edgy.

---

### Post by SZF2001 on 2007-01-01
Thanks for the concern, mang.

The thing is, I was running Dapper too, and Flash was doing the same thing there as it is now. Maybe with Fiesty, a stable release, and some of that Gnush (sp, not sure what they are called) support, this will all clear up.

---

### Post by Xitron on 2007-01-09
DistortedStar, you absolutely rock!  I was about to give up any hope of ever using Flash in Edgy, and one quick line in a file I didn't even know existed has it working perfectly!  Very much appreciated!

Unca Xitron

---

### Post by kyfho23 on 2007-01-13
> **hikaricore said:**
> Works perfectly :) you saved my sanity.

Although swiftfox still has problems.  I'm going to try to find a solution and when I do I'll post it here.  :)
thank you...i've spent a couple of days looking for non-existant rc files for swiftfox :).

---

### Post by tenjin1 on 2007-01-20
Hi.
I was one of the unlucky ones. I had added the export XLIB_SKIP_ARGB_VISUALS=1 to the etc/firefox/firefoxrc, even added to etc/mozilla-firefox/mozilla-firefoxrc, depth was already set to 24 in xorg.conf and composite wasn't there, had flash9 installed in ~/.mozilla/plugins and usr/lib/firefox/plugins and opt/firefox/plugins. I deleted my firefox profile, which seemed to work at first...then CRASH. I even upgraded to Firefox2 and STILL had flash problems crashing firefox EVERYTIME. Oh yeah and also installed Swiftfox which seemed to work at first then it started crashing and I never changed anything. Was using Opera 9 but didn't like it as much as Firefox. Was going to try other Mozilla browsers and just give up on firefox....then I saw [http://www.brainonfire.net/2006/05/25/firefox-crash-on-flash-content-in-ubuntu/]("http://www.brainonfire.net/2006/05/25/firefox-crash-on-flash-content-in-ubuntu/")
and did:
```
sudo apt-get remove libflash0c2
```
and all seems to be working well! Hope this helps someone!

---

### Post by ~zoey~ on 2007-02-26
Bummer; double post.  Sorry about that!

---

### Post by ~zoey~ on 2007-02-26
I have tried in dapper;

In the /etc/firefox/firefoxrc file, insert this line:
Code:

export XLIB_SKIP_ARGB_VISUALS=1

You may add the following line in your firefox starting script (/usr/bin/firefox):

export XLIB_SKIP_ARGB_VISUALS=1

sudo apt-get remove libflash0c2

[depth was already at 24]

and the weird thing is that each one works ONCE and only once.  The next time that I try to read my mail in gmail it crashes.  I guess that I should consider myself lucky because so far that is the only thing that crashes and flash seems to be working.  I am downloading my email through Evolution so I can read it, but I would like to find a solution.

zoey

---

### Post by distortedstar on 2007-02-27
> and the weird thing is that each one works ONCE and only once. The next time that I try to read my mail in gmail it crashes. I guess that I should consider myself lucky because so far that is the only thing that crashes and flash seems to be working. I am downloading my email through Evolution so I can read it, but I would like to find a solution.

The fixes I posted were for crashes due to flash. Your problem perplexes me, because gmail uses ajax--not flash--if I'm not mistaken. Have you tried "Plain HTML" option in gmail? While not an ideal solution, it may at least give you basic access for the time being, while you figure this out.

---

### Post by ~zoey~ on 2007-03-01
Hmmmm, well I wondered what flash had to do with gmail, but what do I know, I'm just a little old lady havin'  a ball with linux.   Anyway, the problem seems to be related to adblock.  I whitelisted gmail and now I can usually open the mail without a crash, although not every time.

zoey

---

### Post by bbpackwood on 2007-03-17
So I tried everything suggested and nothing worked on my Breezy :(

So I went ahead and created two script files on my desktop

revive.flash.sh

cp /home/MYNAME/Desktop/linux/flashplayer.xpt   /home/MYNAME/.mozilla/plugins/
cp /home/MYNAME/Desktop/linux/libflashplayer.so   /home/MYNAME/.mozilla/plugins/

kill.flash.sh

rm /home/MYNAME/.mozilla/plugins/flashplayer.xpt
rm /home/MYNAME/.mozilla/plugins/libflashplayer.so

When ever I get to page that needs flash I revive it, otherwise I kill it.

This is so lame, but what else.

-Bob

---

### Post by distortedstar on 2007-03-17
You may want to upgrade to Dapper, which is the latest long-term support release. I had no problems with flash in Dapper.

---

### Post by erichnewell on 2007-04-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/99163](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/99163) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**apt-get remove --purge libflash0c2 libflash-mozplugin**

This worked for me and I still have flash functionality and flashblock running. I was already at 24bit color and cannot comment on that.

I did not however make any changes to "firefoxrc" or any other files.

:-)

I had just completed upgrading from Dapper to Edgy and then immediately from Edgy to Feisty. (Seamlessly I might add) when I found that firefox would crash immediately upon loading gmail. After reading this thread and a few others, I wondered if it was indeed related to Flash at all and decided to test.

Using:

```
apt-show-versions | grep flash
```

I found only two...so I removed them:

```
apt-get remove --purge libflash0c2 libflash-mozplugin
```

I then opened firefox and gmail without any issues....oddly, I noticed that "flashblock" had loaded over an ad. Upon clicking it, I was shocked to find that I still had flash functionality.

Since everything is working fine, I have not investigated any further regarding why.

YMMV...Enjoy.

---

### Post by dotweb on 2007-04-27
Hi, this didnt work for me, I still have the same problem. My graphic card will not allow me to use 24 bit only poss. is 16 and 32 bit.

---

### Post by seamuso on 2007-04-30
I figured I'd toss this into this thread ..

Feisty Kubuntu release version .. ff random crashing, lockups, etc (doesn't crash in my Feisty Ubuntu beta install) .. I found this thread a couple days ago and tried the fixes, but the crashes and lockups still happened.

Uninstalled all flash .. still crashing
uninstalled all java .. still crashing
disabled all plugins .. still crashing

on a whim, swtched browser theme (was using BlackJapanMax .. same as my feisty beta uses) to red shift .. ff hasn't crashed yet, 3+ hours, and in this same amount of time prior to changing the theme, I was crashing at a minimum 3-5 times and hour.

Enabled all plugins, reinstalled java, etc ..

---

### Post by steveneddy on 2007-06-05
My solution [here]("http://ubuntuforums.org/showthread.php?p=2787287#post2787287").

---

### Post by mevets on 2007-07-20
> **tenjin1 said:**
> Hi.
I was one of the unlucky ones. I had added the export XLIB_SKIP_ARGB_VISUALS=1 to the etc/firefox/firefoxrc, even added to etc/mozilla-firefox/mozilla-firefoxrc, depth was already set to 24 in xorg.conf and composite wasn't there, had flash9 installed in ~/.mozilla/plugins and usr/lib/firefox/plugins and opt/firefox/plugins. I deleted my firefox profile, which seemed to work at first...then CRASH. I even upgraded to Firefox2 and STILL had flash problems crashing firefox EVERYTIME. Oh yeah and also installed Swiftfox which seemed to work at first then it started crashing and I never changed anything. Was using Opera 9 but didn't like it as much as Firefox. Was going to try other Mozilla browsers and just give up on firefox....then I saw [http://www.brainonfire.net/2006/05/25/firefox-crash-on-flash-content-in-ubuntu/]("http://www.brainonfire.net/2006/05/25/firefox-crash-on-flash-content-in-ubuntu/")
and did:
```
sudo apt-get remove libflash0c2
```
and all seems to be working well! Hope this helps someone!
thanks, this worked for me when nothing else did!

---

### Post by telemetry on 2007-10-01
For anyone using Feisty 7.04 - you will have to use    sudo gedit vi /usr/bin/firefox     as root/super user    and then  copy and paste the line      export XLIB_SKIP_ARGB_VISUALS=1           underneath the line that starts       MOZ_PROGRAM=

then save 

I hope this helps as the procedure seems different for Feisty and I'm sure there are a lot of frustrated feisty folk out there looking for a fix for flash crashing in Firefox.

hope this helps
robert.

---

### Post by telemetry on 2007-10-01
actually - use       sudo gedit  /usr/bin/firefox

drop the vi

unfortunately - although it seemed to help - still hasn't eliminated the problem for me.

---

### Post by init1 on 2007-10-07
This worked for me. I already had 24 bit, but editing /ect/iceweasel/iceweaselrc stopped it from crashing. Thank you very much!

---

