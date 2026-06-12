---
title: "Blurry Screen"
date: 2007-06-05
forum: General Help
---

### Post by smylie on 2007-06-05
Hi

Since I've changed laptops, the LCD screen is really blurry/fuzzy with quite bad banding.

It's got an Intel GM965 video card running a 1680x1050 screen.

It works, and runs at the correct resolution at 24 bit color depth, but every thing is slightly fuzzy. It's like true-type text being off focus, but **everything** is blurred. It's not just the text, but the cursor,  straight lines on the screen (eg borders) is all blurred out.

I did try playing round with the Ubuntu font section under Preferences, but none of the setting made any difference, and I stopped when I noticed it wasn't just text having the problem . . . 

The screen looks nice and crisp in Windows XP running at 1680x1050, so i'm fairly sure it's a configuration thing.

xdpyinfo states:
```
screen #0:
  dimensions:    1680x1050 pixels (331x207 millimeters)
  resolution:    129x129 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
```

So i'm pretty sure it's running at the right resolution. 

The relevant part of my xorg.conf: 
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
```

Has anyone got any idea why my screen could be so blurry?

Thanks
Dave

---

### Post by renzokuken on 2007-06-05
its probably caused by using the wrong driver. check you SECTION "DEVICE" part of your xorg.conf and let us know what driver it is using.

there is an intel driver in the repos that should improve video all round

---

### Post by smylie on 2007-06-05
> **renzokuken said:**
> its probably caused by using the wrong driver. check you SECTION "DEVICE" part of your xorg.conf and let us know what driver it is using.

there is an intel driver in the repos that should improve video all round
Sorry - I should have specified . . .
I tried the i810 driver (x wouldn't even start), so I'm currently using the most recent (well a week old maybe), intel drivers from their git repository . . ..

---

### Post by bimbo on 2007-06-09
What happens when you use VESA instead? It's gonna be painfully slow but it might help?

---

### Post by smylie on 2007-06-09
Unfortunately I can't get it to run with VESA at all - I had to get the latest intel drivers from their git repo to get any sort of X at all.

```
(II) VESA(0): Total Memory: 119 64KB banks (7616kB)
(II) VESA(0): Generic Monitor: Using hsync value of 64.08 kHz
(II) VESA(0): Generic Monitor: Using vrefresh value of 60.11 Hz
(II) VESA(0): Not using mode "1680x1050" (no mode of this name)
(II) VESA(0): Not using mode "1280x800" (no mode of this name)
(II) VESA(0): Not using mode "1280x768" (no mode of this name)
(II) VESA(0): Not using mode "1200x800" (no mode of this name)
(II) VESA(0): Not using mode "1152x864" (no mode of this name)
(II) VESA(0): Not using mode "1152x768" (no mode of this name)
(II) VESA(0): Not using mode "1024x768" (no mode of this name)
(II) VESA(0): Not using mode "800x600" (no mode of this name)
(II) VESA(0): Not using mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(WW) VESA(0): No valid modes left.  Trying less strict filter...

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: /lib/tls/i686/cmov/libc.so.6 [0xb7dece98]
2: /usr/X11R6/bin/X(InitOutput+0x9aa) [0x80a5b9a]
3: /usr/X11R6/bin/X(main+0x27b) [0x807456b]
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7dd8ebc]
5: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11.  Server aborting

```

I assume that means that there's no VESA support for this card yet either. I'm downloading gutsy gibbon at the moment - I'll  let you know if the later drivers in that make a difference

Cheers
Dave Smylie

---

### Post by bimbo on 2007-06-09
It's kinda disturbing that you get Signal 11. Usually Xorg doesn't die when it can't find a driver.

Maybe something's wrong with the hardware? You might want to run memtest for a while?s

---

### Post by apel_2804 on 2007-06-09
Hi,

i have exactly teh same problem with an dell latitude d630 with and intel x3100 and 1400x900 lcd. I used teh new xorg intel package but image is blurry. then i installed debian and compiled the intel driver but its exactly teh same issue. external devices don't have these problems!

---

### Post by tpg on 2007-06-09
Could it possibly be something to do with the refresh rate? 'Fuzzy' on a laptop (i.e. lcd) screen suggests to me that it is forcing the refresh rate to, say, 75Hz, when a lot of LCDs run at 60Hz.

---

### Post by smylie on 2007-06-09
> **tpg said:**
> Could it possibly be something to do with the refresh rate? 'Fuzzy' on a laptop (i.e. lcd) screen suggests to me that it is forcing the refresh rate to, say, 75Hz, when a lot of LCDs run at 60Hz.
Yeah - could well be. 
I'm not sure how I'd tell though - Preferences -> Screen resolution reports it as 60hz, so I'm assuming that's what it's actually running at . . .

Cheers
Dave Smylie

---

### Post by tpg on 2007-06-10
You could have a look in xorg.conf to see if the "VertRefresh" option is set in the "Monitor" section. If not, add something like
```
Section "Monitor"
  ...  
  VertRefresh 60
  ...
EndSection
```
which should force the refresh rate to 60 (If it isn't already at 60).

---

### Post by ramjet_1953 on 2007-06-10
There are a couple of options for video driver for Intel chipsets.

Follow this link and try whichever one suits:


[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

Regards,
Roger :cool:

---

### Post by smylie on 2007-06-11
> **tpg said:**
> You could have a look in xorg.conf to see if the "VertRefresh" option is set in the "Monitor" section. If not, add something like
```
Section "Monitor"
  ...  
  VertRefresh 60
  ...
EndSection
```
which should force the refresh rate to 60 (If it isn't already at 60).
No difference - guess it must have already been running at 60.

Thanks anyway.

---

### Post by smylie on 2007-06-11
> **ramjet_1953 said:**
> There are a couple of options for video driver for Intel chipsets.

Follow this link and try whichever one suits:


Thanks Roger

Still no luck though as I'm already running the latest intel drivers from their git repository, and 915resolution only supports older intel cards. 

Cheers
Dave Smylie

---

### Post by eklitzke on 2007-06-11
You might want to try the intel (not i810) driver. I have a friend who had the same problem, and that fixed it for him. In fact, with my monitor (also running at 1680x1050) I couldn't get the i810 driver to output the correct resolution at all. The downside is that xv support is currently broken in the intel driver. The package to install would be xserver-xorg-video-intel.

---

### Post by smylie on 2007-06-11
> **eklitzke said:**
> You might want to try the intel (not i810) driver. I have a friend who had the same problem, and that fixed it for him. In fact, with my monitor (also running at 1680x1050) I couldn't get the i810 driver to output the correct resolution at all. The downside is that xv support is currently broken in the intel driver. The package to install would be xserver-xorg-video-intel.
Thanks for the suggestion eklitzke, but as mentioned, I'm already running the latest intel drivers direct from their git repository.
It's only using these drivers that I can get X to go at all (even with fuzziness/banding)

Cheers
Dave Smylie

---

### Post by hatolf on 2007-06-14
I've the same problem using a new Latitude D830 with a  Intel X3100 GPU. 
xpdyinfo says the resolution is 1680x1050, but everythings looks blurred (like when the display is not driven with it's native resolution).

Any new hints?

---

### Post by Nehvrook on 2007-06-14
Whenever I swap between Windows and Ubuntu my screen goes all fuzzy and out of focus. I'm not using a laptop and I don't know if this will help much, but my moniter has an auto button to find settings and screen placement and stuff. Pressing that usually gets the screen displaying properly again. So is there any way you can check settings on your montier it's self rather than OS software.

---

### Post by sambehera on 2007-06-14
im having this blurry screen issue as well... using a dell inspiron 1501 with ati xpress 1150 graphics chipset... any help would be appreciated...

---

### Post by smylie on 2007-06-15
> **Nehvrook said:**
> Whenever I swap between Windows and Ubuntu my screen goes all fuzzy and out of focus. I'm not using a laptop and I don't know if this will help much, but my moniter has an auto button to find settings and screen placement and stuff. Pressing that usually gets the screen displaying properly again. So is there any way you can check settings on your montier it's self rather than OS software.
Hi Nevhrook

Unfortunately laptops don't usually have anything in the way of external controls. (If you're lucky you might get brightness up/down).

The search for a solution continues . . 

Cheers
Dave Smylie

---

### Post by smylie on 2007-06-15
> **hatolf said:**
> I've the same problem using a new Latitude D830 with a  Intel X3100 GPU. 
xpdyinfo says the resolution is 1680x1050, but everythings looks blurred (like when the display is not driven with it's native resolution).

Any new hints?
No new solutions yet.
I'm currently trying to get the git intel video drivers, to see if they've fixed the issue, but since I did this last time, they seem to have introduced a dependancy on xorg which I'm having a hell of a time trying to get to compile.

Just out of curiousity, were you able to install normally from a live cd, or did you have to use the alternate cd also, and then tweak your video drivers?

Cheers
Dave Smylie

---

### Post by smylie on 2007-06-15
> **sambehera said:**
> im having this blurry screen issue as well... using a dell inspiron 1501 with ati xpress 1150 graphics chipset... any help would be appreciated...
Hi sambehera

I'm not sure if yours is the same problem as ours - this seems to be tied to the intel x3100 965gm chipsets, and is hopefully just due to it being new hardware . . .

What is your laptops native resolution? 
What does xdpyinfo report regarding the resolution?
Is it just the fonts that are blurry, or is it the whole screen?

Cheers
Dave Smylie

---

### Post by hatolf on 2007-06-15
> **smylie said:**
> 
Just out of curiousity, were you able to install normally from a live cd, or did you have to use the alternate cd also, and then tweak your video drivers?


I had to use the alternate cd to install (and use the kernel parameter all_generic_ide to make the system boot from cd, there seems to be an issue with the sata controller and optical drive).

I've also tried out Fedora 7, and the screen is also blurry, so it's not an ubuntu specific issue.

Maybe we should make a bugreport to the intel driver people

---

### Post by ramjet_1953 on 2007-06-15
You need to load-up the correct video driver for your card.

If you follow this link, it offers you two options:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

Regards,
Roger :cool:

---

### Post by smylie on 2007-06-15
> **ramjet_1953 said:**
> You need to load-up the correct video driver for your card.

If you follow this link, it offers you two options:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

Regards,
Roger :cool:
Hi Roger

I appreciate you're trying to help, but this is the second time you've suggested using the (outdated) drivers from the ubuntu repo's. As I replied last time (and at the start of this thread),  I'm using the latest drivers compiled myself from the intel git repository on freedesktop.org.

But thanks for the input all the same - better than being ignored =)

And for future reference, the 915resolution solution isn't an option for the  newer intel cards (ie 965GM) - support for native resolutions for these is rolled into the new intel video driver

Cheers
Dave Smylie

---

### Post by cnshzj007 on 2007-06-15
I can make sure that I can't install U704 from a live CD sent by OFFICAL.

---

### Post by njmurphy on 2007-06-15
Have you seen this bug?  It sounds pretty similar.

[https://bugs.freedesktop.org/show_bug.cgi?id=8706](https://bugs.freedesktop.org/show_bug.cgi?id=8706)

For the record, I'm experiencing the same thing with a Thinkpad T61 at 1440x900.

---

### Post by njmurphy on 2007-06-15
I got it!  Thanks to the incredibly terrific ThinkWiki, I found this:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61)

Simply follow his instructions for patching the xserver-xorg-video-intel package, install the replacement, et voila!

---

### Post by shadowarts on 2007-06-15
Heh, I was just looking for this post as I was going to post that here as well.  I am also using a ThinkPad T61 (1440x900) but im having some other graphics issues still.  OpenGL stuff and aiglx/compiz seem really unstable...  When ever i move a window the the edge of the screen with compiz, X11 just hardlocks...  Are you experiencing this as well? I know its not the change to the driver that does it, because when I had the 'fuzzy' screen symptom this was happening.  Are you running 32-bit or 64-bit Ubuntu? Let me know if you have that same issue, thanks!

**Also, (offtopic) can you get the sound working?***

---

### Post by smylie on 2007-06-16
> **njmurphy said:**
> Have you seen this bug?  It sounds pretty similar.

[https://bugs.freedesktop.org/show_bug.cgi?id=8706](https://bugs.freedesktop.org/show_bug.cgi?id=8706)

For the record, I'm experiencing the same thing with a Thinkpad T61 at 1440x900.
That does sound pretty damned close - identical in fact.
the only thing is that (in my case at least), I'm using the latest intel drivers, which I think now includes the modesetting code, so theoretically, I shouldn't be getting this . . .

---

### Post by njmurphy on 2007-06-16
> **smylie said:**
> the only thing is that (in my case at least), I'm using the latest intel drivers, which I think now includes the modesetting code, so theoretically, I shouldn't be getting this . . .

I believe the modesetting code is still a separate branch.  That said, have you tried that little patch?  I'm guessing it's exactly what you're looking for.

---

### Post by shadowarts on 2007-06-16
> **smylie said:**
> That does sound pretty damned close - identical in fact.
the only thing is that (in my case at least), I'm using the latest intel drivers, which I think now includes the modesetting code, so theoretically, I shouldn't be getting this . . .

It is not a mode setting issue, it an auto scaling issue.  By changing the code as I described on the think wiki article, it will disable auto scaling, which will 'clear up' the issue. :D

---

### Post by smylie on 2007-06-17
> **njmurphy said:**
> I believe the modesetting code is still a separate branch.  That said, have you tried that little patch?  I'm guessing it's exactly what you're looking for.
that was exactly what I was looking for =)

some how i missed seeing the bit about the patch the first time I read it.

took a few goes to get it to compile properly, but it looks much better now.

cheers for that.

---

### Post by cnshzj007 on 2007-06-17
i386's DEB package is available here, which can fix the problem that X3100 with 965GM.

---

### Post by cnshzj007 on 2007-06-17
DELL D630 i386's DEB package is available here, which can fix the problem that X3100 with 965GM.

---

### Post by smylie on 2007-06-17
shadowarts + njmurphy - seriously, thanks again for helping me get this sorted.

About a day later, and I still can't get over how much more usuable this screen is now

My eyes thank you =)

Dave Smylie

---

### Post by hatolf on 2007-06-18
Many thanks, this community really rocks :)
Now I can use my Latitude D830 without getting headache.

---

### Post by RaggedEdge1 on 2007-06-20
Ok, the patch made my text better on my D830 and is really appreciated, but I still have banding as if it is not really displaying in 24 bit color.  The default Feisty wallpaper shows the bands, and if I select System then Quit, the fade out of the desktop is not smooth, it fades in increments of color.    Anyone else seeing this?

---

### Post by Voland666 on 2007-06-20
Yes. The banding problem shows up in my Dell Latitude D630 also (Intel 965GM X3100, 1440x900 AU Optronics panel). It is especially noticeable in (hopefully) smooth and uniform gradients (such as wallpapers, gdm logins backdrops, palette widgets...) In fact, there's apparently no difference between 16 and 24 bit video modes.
The down-upscaling related blur is gone by virtue of patching and making xorg-video-intel as suggested on the xorg mailing list.
Compiz and GoogleEarth both freeze the machine. Compiz strives to work... try moving the windows *very* slowly... they nicely wobble... Avant-Window-Navigator works fine with transparencies and everything else...

---

### Post by njmurphy on 2007-06-20
> **shadowarts said:**
> Heh, I was just looking for this post as I was going to post that here as well.  I am also using a ThinkPad T61 (1440x900) but im having some other graphics issues still.  OpenGL stuff and aiglx/compiz seem really unstable...  When ever i move a window the the edge of the screen with compiz, X11 just hardlocks...  Are you experiencing this as well? I know its not the change to the driver that does it, because when I had the 'fuzzy' screen symptom this was happening.  Are you running 32-bit or 64-bit Ubuntu? Let me know if you have that same issue, thanks!

I've noticed the patched driver is pretty unstable too; almost any GL screensaver I've tried locks my screen right up.  As for sound, there's a bugfix submitted to the ALSA folks, so it should just be a matter of time until we have support.

As long as we're off topic, have you had any luck with suspend/hibernate?

---

### Post by RaggedEdge1 on 2007-06-20
> **Voland666 said:**
> Yes. The banding problem shows up in my Dell Latitude D630 also (Intel 965GM X3100, 1440x900 AU Optronics panel). It is especially noticeable in (hopefully) smooth and uniform gradients (such as wallpapers, gdm logins backdrops, palette widgets...) In fact, there's apparently no difference between 16 and 24 bit video modes.
The down-upscaling related blur is gone by virtue of patching and making xorg-video-intel as suggested on the xorg mailing list.
Compiz and GoogleEarth both freeze the machine. Compiz strives to work... try moving the windows *very* slowly... they nicely wobble... Avant-Window-Navigator works fine with transparencies and everything else...


Thanks for your confirmation, I guess we will have to wait for Intel to work on the driver.   The good thing is, on my Latitude D830, the 1920 x 1600 resolution is high enough to almost hide the fact that it is running in 16 bit color.  If I go into Gimp and create a new graphic and do a gradient fill, I can still see the banding.  Funny I remember way back in the day when I first had a card capable of 24 bit color thinking it wasn't really that different...amazing how many years for running 24 bit color has changed my perspective.

---

### Post by smylie on 2007-06-21
> **RaggedEdge1 said:**
> Ok, the patch made my text better on my D830 and is really appreciated, but I still have banding as if it is not really displaying in 24 bit color.  The default Feisty wallpaper shows the bands, and if I select System then Quit, the fade out of the desktop is not smooth, it fades in increments of color.    Anyone else seeing this?
I'm not convinced on the 16 vs 24bit thing yet . . . (at least in my case).

The default wall paper had really severe banding, but when I installed the ubuntu wallpaper's, they all look fine - no banding at all. I'm really not sure why they'd look fine when the default wallpaper looks like such crap...

On a tangent, I can report that it runs beryl  (0.2.1) quite happily. Compiz doesn't want to load at all, but no probs with beryl.

---

### Post by jayant on 2007-06-21
cnshzj007 thanks for the deb package. worked well with my dell latitude d630.

smylie can you please tell me what you did to get beryl to work? i tried to install it by following the instructions for ATI cards from here [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29) . i know i do have an intel 965gm card. but i decided to give it a shot. Anyway this didnt work for me. After I do all the settings as mentioned on that site and I tried to move my windows, everything crashes and i have to restart.

Any help would be appreciated.

And please let me know if i should start a different thread for this

---

### Post by hatolf on 2007-06-21
> **jayant said:**
> http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29[/URL] . i know i do have an intel 965gm card. but i decided to give it a shot. Anyway this didnt work for me. After I do all the settings as mentioned on that site and I tried to move my windows, everything crashes and i have to restart.


I installed beryl via synaptic, if I start beryl-manager in a terminal beryl loads up fine. When I try to move a window, the system freezes instantly.

---

### Post by apel_2804 on 2007-06-21
with the patch the picture is now clear and crips but i still think that the color depth is not correct, i dont think its 24bit... someone with same problem left?

---

### Post by smylie on 2007-06-21
> **jayant said:**
> 
smylie can you please tell me what you did to get beryl to work?After I do all the settings as mentioned on that site and I tried to move my windows, everything crashes and i have to restart.


I wish I could tell you what I did to get it to work, but I'm not quite sure . . .
I had the same issue with it loading, then instantly freezing the screen as soon as I started to move windows around.
I tried desktop-effects, compiz and beryl from synaptic - all either crashed, or wouldn't load. Tried heaps of different configurations, versions (compiz .4 and .5 etc) with no luck :(

Eventually on the verge of giving up, I created another user and tried starting it up from that account - it all worked fine.  I went back to my main account, and did
```

$ rm -rf ~/.beryl*

```
and it started and worked fine. 

I can't think of any thing specific I did that would have caused it break or to unbreak. The only thing I can think of is that it had something to do with the blurry screen patch . .. once you've got the blurry screen thing resolved, try deleting your existing beryl config directories and see if that resolves things. . . .

---

### Post by hatolf on 2007-06-22
> **smylie said:**
> 
Eventually on the verge of giving up, I created another user and tried starting it up from that account - it all worked fine.  I went back to my main account, and did
```

$ rm -rf ~/.beryl*

```
and it started and worked fine. 


I tried this out, but it didn't help. Do you use AIGLX or XGL?

---

### Post by smylie on 2007-06-22
> **hatolf said:**
> I tried this out, but it didn't help. Do you use AIGLX or XGL?
i'm not actually sure - i just have everything set to automatic and it works.
i did just try and start it with --force-xgl and it locked my machine, so I suspect it *might* be aiglx

Do you know of a  way to find out what it's using? There doesn't seem to be a --verbose switch . . .

Cheers
Dave Smylie

---

### Post by meanimal on 2007-06-24
I'm using a T61 with Intel x3100.  I also had to patch the intel driver to avoid blurriness at native resolution.  However, there is definitely something going on with the color depth - I can verify because the VESA drivers work on my system @ 24-bit depth and the difference is visually astonishing in comparison to using the Intel drivers.  The VESA drivers show no banding or specles in photographs.

---

### Post by shadowarts on 2007-06-25
> **meanimal said:**
> I'm using a T61 with Intel x3100.  I also had to patch the intel driver to avoid blurriness at native resolution.  However, there is definitely something going on with the color depth - I can verify because the VESA drivers work on my system @ 24-bit depth and the difference is visually astonishing in comparison to using the Intel drivers.  The VESA drivers show no banding or specles in photographs.

I have a T61 with the Intel x3100 as well (I think I was mentioned in this thread for the clarity fix).  Anyway, I do notice that gradient-like patterns have some banding issues, though I haven't been able to compare it to vesa, as the vesa driver doesn't work at all.  How did you get it working? Are you running 64-bit or 32-bit?

Anyway, for the last week or so I was working on getting sound working for my laptop (which I kind of missed the obvious on but oh well) and I now intend to go back to doing more work on investigating some of the weird graphical issues.  The main things on my list are the banding and the opengl aiglx/compiz issues.  I didn't really notice the banding until I read this thread, has anyone submitted a bug report for this? If not I may.

Hopefully by the end of the week I will have this card a little bit better and I will make sure I post anything I figure out here.  Anyway I just felt obligated to say something on this thread. :D

---

### Post by smylie on 2007-06-25
> **shadowarts said:**
> I have a T61 with the Intel x3100 as well (I think I was mentioned in this thread for the clarity fix).  Anyway, I do notice that gradient-like patterns have some banding issues, though I haven't been able to compare it to vesa, as the vesa driver doesn't work at all.  

 The main things on my list are the banding and the opengl aiglx/compiz issues.  I didn't really notice the banding until I read this thread, has anyone submitted a bug report for this? If not I may.


I'm about to log two bug reports for this - one with the intel driver team re the banding, and one with ubuntu regarding the installation cd not detecting the card correctly (forcing me to use the alternate install cd).

On that note - was anyone else with this card able to install normally? (or was I the only one who couldn't . . .).

I can confirm also I can't get the VESA driver to work at all.

Also, I've upgraded to the latest Compiz Fusion, and can confirm that works ok with this card.

Cheers
Dave Smylie

---

### Post by ddexter on 2007-06-26
Hi everyone, I'm new to Ubuntu (was a gentoo user until gentoo couldn't recognize my harddrive), so I'm still not really familiar with the internals of ubuntu.  Anyway, when I try to
> apt-get install source xserver-xorg-video-intel
I get
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package source


Also, besides the fuzziness, the only resolutions I can pick from are 1024x768 and 800x600.  I want to run my monitor at 1440x900 (it can reach that resolution).  Does anyone have any advice?

---

### Post by VeloSol on 2007-06-26
I had the same problem with the wrong resolution - I had used
```
sudo dpkg-reconfigure xserver-xorg
``` 

And set the i810 driver and then chose the higher resolution that was appropriate for my monitor and it worked about half the time.  After investigating the xorg.conf before and after (I was having the issue where I810 complained that there was no device at PCI0:02:1, hence why I was doing this), the only thing that seemed to change was the driver name and the resolution list - it had added 1280x800 (my monitor's native resolution) and changed the driver from vesa to i810.

I would try using your favorite editor (vim is below) and just add your resolution to all the bitdepths in xorg.conf:
```

sudo vim /etc/X11/xorg.conf
``` gets you to:
```

#Written from memory, may not be the exact area or syntax
Section "Display"
     ...
     bitDepth 8
     resolution "1440x900"  "1024x768"  "800x600"  "640x480"
    
     bitDepth 16
     resolution "1440x900" ...

```

Save and then restart the x server (I believe you can crash it using Ctrl+Alt+Bkspace and then use startx to restart it, but I have never tried that - I just rebooted, or if I was using Kubuntu I restarted the xserve from the login screen).

Hope this helps, if not, post back!

-VeloSol

---

### Post by shadowarts on 2007-06-26
It should be apt-get source ....

not 

apt-get **install** source ...

---

### Post by ddexter on 2007-06-26
Either way.  When I type 
> apt-get source install xserver-xorg-video-intel

I still get

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for install


EDIT:
I had already did apt-get install <intel-driver> , which was why it was giving me an error.  I did apt-get source <intel-driver> and it worked just fine.
Thanks for the help all

---

### Post by hecato on 2007-06-26
About the graphics try this 1 [http://ubuntuforums.org/showpost.php?p=1388643&postcount=14](http://ubuntuforums.org/showpost.php?p=1388643&postcount=14)

Also you can try in /etc/X11/xorg.conf search for the horizontal and vertical refresh of the monitor and change them to  a larger resolution (you will see the change in Xorg.conf accepting some resolutions and forgeting others because they don't enter in the horizontal or vertical refresh rate.

then search for the actual resolutions, xorg.conf is configured (writed) to have only 1024x768 max by default, you should add 1440x... like the other resolutions, save the file, restart the X (hit CTRL+ALT+DEL) get back to the session.

See that you can change your resolution at runtime with CTRL+ALT+ "+" (of the keypad) or 
"-"




About the not able to find the package, you should look at apt-cache find ... if not, you should update your sources list... dont remember the file, but open synaptic and in configuration->repositories enable all of them and do a refresh of the available packages.

---

### Post by meanimal on 2007-06-27
> **shadowarts said:**
> I have a T61 with the Intel x3100 as well (I think I was mentioned in this thread for the clarity fix).  Anyway, I do notice that gradient-like patterns have some banding issues, though I haven't been able to compare it to vesa, as the vesa driver doesn't work at all.  How did you get it working? Are you running 64-bit or 32-bit?


I installed using the 32-bit Feisty alternate CD, anticipating after reading these forums that I would have graphics problems.  However it somehow setup a bootable xorg.conf!  I don't think there was anything too specific, just the following lines:

```
Driver "vesa"
BusID "PCI:0:2:0"

```

Also, per the alternate installation menus, each color depth was setup for only my native resolution: 1680x1050

24-bit color worked fine, although I prefer to have faster graphics than 24-bit color, so I'm continuing to use the broken Intel driver.

Perhaps the PCI bus needs to be specified?

---

### Post by mr.snuff on 2007-06-28
Hi,

I also have a Thinkpad T61 with Intel X3100 graphic chip. I followed your steps in the Thinkwiki, shadowarts, and it solved the blurry problem. I haven't tried to fix the sound until now but will do that soon. Thanks for publishing your solutions! :)

Beryl or Compiz are not running for me at the moment. Both of them make my system freeze completely after a few seconds. Really sad since I would like to have some eye-candy. It hurts to know that you have one of the newest laptops and are not able to use stuff like that!

Unfortunately I'm totally new to Linux and can't really figure out how to solve the problems on my own. Actually I wanted to use Ubuntu as my main operation system and thus replace Windows. But so far I had quite some problems with my T61 and Ubuntu...
Hope they can be solved in the next time.

So please write in this thread if you have figured out something new!

Thanks!

Edit: Because of the installation CD: I was able to use the normal, graphical installation CD by changing the resolution and color depth to the lowest possible option (600x400 vga or so). Just insert the CD and when the menu comes up press F4 and change it.

---

### Post by albertonym on 2007-06-29
Any news about the banding problem? Have the same issue here.

On a different note, do you guys have DRI enabled? That's from my /var/log/Xorg.0.log: 

> 
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
(II) intel(0): [drm] drmOpen failed
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI.


---

### Post by albertonym on 2007-06-30
OK, I've solved the DRI problem by compiling my own intel driver. However, I do not have GLX support. glxinfo returns 

>  Error: unable to open display (null)

Does anyone have the same problem?


> **albertonym said:**
> Any news about the banding problem? Have the same issue here.

On a different note, do you guys have DRI enabled? That's from my /var/log/Xorg.0.log:

---

### Post by albertonym on 2007-07-05
OK, I solved banding issue (actually, it was solved by itself). Still have to GLX/DRI/DRM support. Any thoughts?

---

### Post by Voland666 on 2007-07-07
Try the latest intel driver from here (deb attached)
[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)

---

### Post by cacycleworks on 2007-07-20
FYI: I just started up kubuntu from the gutsy tribe 3 install on my new Dell D630 laptop. 1440x900 @ 24bits no problem. I did alt install then lots of aptitude upgrades and dist-upgrades for anything BUT KDE, which I did last. The xorg server install included 1440x900 and it is crystal clear. MUCH better than my first install. btw, wireless worked too. 

no sound and probably no cd-rom without some tweaks. 

me=happy

---

