---
title: "Hardy: fonts look worse"
date: 2008-04-25
forum: General Help
---

### Post by joeri_83 on 2008-04-25
Hi,

I just upgraded to Hardy (from Gutsy), and now my fonts looks worse. They are sort of blurry. I might be more noticeable in Firefox but I am not sure if that's just me tricking myself. Any ideas? Msttcorefonts are installed.

---

### Post by priegog on 2008-04-25
yeah, try system>preferences>appearance> fonts tab
from there try different options... I set it up to the LCD settings and they look great

---

### Post by joeri_83 on 2008-04-25
Had already done that, and as I switch it between the options it seems as if it does not affect firefox, and it makes other things looks worse (I had it at LCD too). Also, I am pretty sure that the terminal looks worse as well (not just FF in other words).

---

### Post by priegog on 2008-04-25
In that case I'm afraid I can't help you. It surely seems like a conflicting upgrade... did you make some weird tweaks to the fonts while on Gutsy? If that is the case you will have to repeat them, or alternatively, do a clean install of Hardy.
Also, I know it sounds dumb, but make sure your resolution is setup properly (ie, proper ratio if widescreen, etc.)

---

### Post by joeri_83 on 2008-04-25
Thanks, anyway!

I can't remember tweaking them, and the resolution seems to be right too. The fonts are not so ugly that I can't live with it, but they are a bit harder on the eyes.

---

### Post by priegog on 2008-04-25
> **joeri_83 said:**
> Thanks, anyway!

I can't remember tweaking them, and the resolution seems to be right too. The fonts are not so ugly that I can't live with it, but they are a bit harder on the eyes.

Oh. believe me, those kinds of tweaks that one does on a fresh install are VERY EASY to forget come 6 months... But yeah, I guess a clean install would do the trick.

---

### Post by joeri_83 on 2008-04-25
True enough. ;)

I'm sort of hesitant to do a clean install, simply due to forgetting some tweaks I've made, and programs I like...

---

### Post by priegog on 2008-04-25
> **joeri_83 said:**
> True enough. ;)

I'm sort of hesitant to do a clean install, simply due to forgetting some tweaks I've made, and programs I like...

I feel ya, but take it as a ways of not losing your edge and knowledge. Also, I've found that MANY of the tweaks I've had to make in past releases just weren't necessary in the newer ones.
Also, If you mean stuff like settings, gnome skins and stuff, if you backup your /home folder (or better yet, move it to it's own partition), it'll all be just like you left it.

---

### Post by joeri_83 on 2008-04-25
I suppose I should move it to its own partition either way. Are there any good guides from doing that, for people like me who didn't do it the first time around?

---

### Post by priegog on 2008-04-25
Yeah this one looks ok [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
But when I did mine, I just copied everything to an external hdd and back to the new partition... I ran into permission problems but ultimately fixed them with chmod or something. 
...Just follow the guides :P

---

### Post by rotalever on 2008-04-25
Maybe you can upload a screenshot, so that we can see whats wrong with your fonts. There are many ways to improve the fonts: antialiasing, hinting, selecting the right fonts (!)

---

### Post by joeri_83 on 2008-04-25
[http://www.flickr.com/photos/52205555@N00/2440096527/](http://www.flickr.com/photos/52205555@N00/2440096527/)

I hope that's visible.

---

### Post by priegog on 2008-04-25
> **joeri_83 said:**
> [http://www.flickr.com/photos/52205555@N00/2440096527/](http://www.flickr.com/photos/52205555@N00/2440096527/)

I hope that's visible.

holy **** what language is that? Anyways, I don't see any rendering problems, thus supporting the theory that it's a video problem. Anymore opinions?

---

### Post by joeri_83 on 2008-04-25
Hehe, it's Swedish. ;)

---

### Post by priegog on 2008-04-25
> **joeri_83 said:**
> Hehe, it's Swedish. ;)

Ahh... Some hot chicks you got up there :) I envy you. Anyways, I'm afraid I can't be of more help

---

### Post by rotalever on 2008-04-25
For me rendering looks perfect. Others do not like hinting. Maybe you should try to use the option "slight hinting" in the font settings and change subpixel antialiasing to grayscale.

By the way: Is the resolution of your screen 1280x1024? ;)

---

### Post by joeri_83 on 2008-04-25
That is the resolution, indeed. Are there particular issues with it?

I tried slight hinting and that makes the menus awful (imo) and the firefox window the same. It is especially bad trying to render that particular font though.

---

### Post by rotalever on 2008-04-25
> **joeri_83 said:**
> That is the resolution, indeed. Are there particular issues with it?

No, but sometimes people do not use their native screen resolution ;)
> **joeri_83 said:**
> 
I tried slight hinting and that makes the menus awful (imo) and the firefox window the same. It is especially bad trying to render that particular font though.

Hmm, it is hard to help you, because I do not know what you would like to have. Sharp fonts? Antialiased and hinted (try to use Bitstream fonts)? Antialiased unhinted (blurry look)?

---

### Post by joeri_83 on 2008-04-25
It is the native resolution of the screen. :)

What I would like are sharper fonts, sort of like how they look on a mac for instance. Is it the font selection or settings I should alter?

---

### Post by rotalever on 2008-04-25
> **joeri_83 said:**
> It is the native resolution of the screen. :)

What I would like are sharper fonts, sort of like how they look on a mac for instance. Is it the font selection or settings I should alter?

Ok sharper fonts. Like the font in the chat window? => Change the fonts of Mozilla Firefox and the terminal and you are done. Even sharper (not like mac...)? Go to font settings and disable antialiasing (you do not want that ;) )

---

### Post by joeri_83 on 2008-04-25
Okay, thanks.

I tried setting the terminal font to the same as the chat window one, and it is way bigger even though they are both supposed to be size 10. What is up with that? Size 9 is a bit small.

---

### Post by joeri_83 on 2008-04-25
By the way, do you know if Helvetica is in any of the packages?

---

### Post by rotalever on 2008-04-25
> **joeri_83 said:**
> Okay, thanks.

I tried setting the terminal font to the same as the chat window one, and it is way bigger even though they are both supposed to be size 10. What is up with that? Size 9 is a bit small.
For the terminal you should use a font like  "bitstream vera sans MONO", so that all letters have the same width.

---

### Post by rotalever on 2008-04-25
> **joeri_83 said:**
> By the way, do you know if Helvetica is in any of the packages?
There is a package called ms corefonts or so. Start synaptic and search for "corefont". There is a package which will install standard microsoft fonts like arial, times new roman and perhaps also helvetica.

---

### Post by joeri_83 on 2008-04-25
No helvetica there, but Bitstream vera sans MONO looks good to me. :)

It is still a tad to blurry around the edges, but this I can live with. Now it's just the courier rendering that looks truly awful, but since it's not used all that often that's okay.

---

### Post by Deeta on 2008-04-25
I have exactly the same problem.

It seems as if the gnome font-settings do not influence how my QT4 apps or my Terminal displayed.

For example if I switch between 'LCD' and 'monochrome' my desktop fonts change while my terminal fonts look the same.

Can anyone confirm that this works on a new Hardy install?

P.s.:
Normal 7.10 to 8.04 upgrade here. No prior font customization done.

---

### Post by rotalever on 2008-04-25
Sometimes applications (terminal and firefox) use their own font settings. If fonts only look bad in firefox, like the courier font, you have to change it in the firefox menu.

---

### Post by pablo88 on 2008-04-25
Fonts are without a doubt the bane of my Ubuntu life.

The upgrade to 8.04 went perfectly. Not a hitch. That is what I love about Ubuntu, it just plain works and doesn't show off whilst it does it.

But the fonts . . . 

Skype, Opera and Thunderbird are zizzy and changed from my previous install (7.10). Why can't it leave my font settings alone? I had them perfect before, using Tahoma and the mstcorefonts. And all this QT4 nonsense, so much complication with fonts. And for me, if the font is bad, I cannot use the computer. It's the single most important part of the computer for me, sitting in front of it 8 to 10 hours a day.

Ah well, I am sure that somewhere on this forum there are threads that explain how to get all the fonts crisp again.

---

### Post by rotalever on 2008-04-25
I explained everything you need to optimize your fonts :confused:
This takes 1 minute for every update...

---

### Post by peterdk on 2008-04-25
I am also having font problems. I did a new hardy install, have been using Ubuntu for 2 years now, and it was always looking good on my LCD, with subpixel smoothing off, since I hate the cleartype look.

Anyway, problem is that the fonts are way to thin. This was very visible for me with the gnome-panel menu's. It's like they have anorexia or so, compared to 7.10 Really really bad. Also a bit of blurry rendering happens, especially noticable in the terminal. Whatever I change in the font menu, it doesn't work, so this is frustrating.... :|

---

### Post by T_W on 2008-04-26
> **Deeta said:**
> I have exactly the same problem.

It seems as if the gnome font-settings do not influence how my QT4 apps or my Terminal displayed.

For example if I switch between 'LCD' and 'monochrome' my desktop fonts change while my terminal fonts look the same.

Can anyone confirm that this works on a new Hardy install?

I believe I am seeing similar behavior as you report.

Additionally, I see blurry fonts for the terminal, QT apps (like Skype), and Gecko apps (Firefox, Kompozer).

Anyone found a solution?

---

### Post by rotalever on 2008-04-26
Use **Bitstream fonts** in the terminal and firefox (they have their own font settings), and everything will be ok.

If the fonts are too thin, you have to enlarge the font-size or disable hinting. But hinting will make them blurry. Anything else is NOT possible and has nothing to do with GNOME or ubuntu.

---

### Post by Deeta on 2008-04-26
It seems I found a solution for the lacking subpixel hinting in QT4 and the Gnome-Terminal.

It indeed seems it is a bug introduced in Hardy (see appendix)

Ubuntu uses several font-rendering configuration frontends.
The one we all know is the GUI one that can accessed from gnome.

The other one can be accessed by:
1. open terminal
2. sudo dpkg-reconfigure fontconfig-config
3. choose 'native' (autohinting might be ok too, but try native first :)
4. choose 'always' (as of yet autodetection seems to be broken within qt4 in hardy)
5. choose 'no' (you likely do not want to have non-scalable bitmapped fonts ;-)
6. log out and login again (X needs to be restarted, that is why ;-)

Here some further info and links:
[http://www.ubuntutips.net/node/35](http://www.ubuntutips.net/node/35)
[https://bugs.launchpad.net/gnome-terminal/+bug/190848](https://bugs.launchpad.net/gnome-terminal/+bug/190848)

Toodles :)
Deeta

---

### Post by 6205 on 2008-04-26
> **Deeta said:**
> It seems I found a solution for the lacking subpixel hinting in QT4 and the Gnome-Terminal.

It indeed seems it is a bug introduced in Hardy (see appendix)

Ubuntu uses several font-rendering configuration frontends.
The one we all know is the GUI one that can accessed from gnome.

The other one can be accessed by:
1. open terminal
2. sudo dpkg-reconfigure fontconfig-config
3. choose 'native' (autohinting might be ok too, but try native first :)
4. choose 'always' (as of yet autodetection seems to be broken within qt4 in hardy)
5. choose 'no' (you likely do not want to have non-scalable bitmapped fonts ;-)
6. log out and login again (X needs to be restarted, that is why ;-)

Here some further info and links:
[http://www.ubuntutips.net/node/35](http://www.ubuntutips.net/node/35)
[https://bugs.launchpad.net/gnome-terminal/+bug/190848](https://bugs.launchpad.net/gnome-terminal/+bug/190848)

Toodles :)
Deeta

This howto still doesn't fix ugly terminal fonts. They are still without subpixel hinting and in Gutsy they were much more pretier...

---

### Post by Deeta on 2008-04-26
> **6205 said:**
> This howto still doesn't fix ugly terminal fonts. They are still without subpixel hinting and in Gutsy they were much more pretier...

Strange, it worked for me. Perhaps try to read the links I posted (they are more in-depth) or do a forum search in the now closed Hardy development thead. There was enough Hardy based font weirdness that your problem might be among one of the solutions offered.

I tried to post the one that had the least likelihood to mess up your system :D But it seems it also only suited to fix some of the font problems.

But then, my problem was about the font-rendering and not about the fonts themselves. Oh well :) Good luck anyways :)

Toodles. Deeta

---

### Post by bsmanian on 2008-04-26
Go to preferences/Appearance/Fonts/Rendering/Hinting and select Slight and see the difference.If this does not work Choose MalOtf Book Font for all except for fixedwidth Font.That should work.For firefox go to Preferences/Content/Fonts&Colours/Default Font/MalOtf.Go to Advanced Tab and select MalOTF for Serif and Sans-serif and uncheck allow pages to choose their own fonts instad of my selections above.

---

### Post by sports fan Matt on 2008-04-26
Im using bitstream Vera Serif bold and have no problems

---

### Post by rotalever on 2008-04-26
> **6205 said:**
> This howto still doesn't fix ugly terminal fonts. They are still without subpixel hinting and in Gutsy they were much more pretier...
Have you checked the custom font preferences of your terminal? (Edit->Current Profile...->General->[x] use system fonts)

---

### Post by lamego on 2008-04-28
I have open a bug report for this issue, I would appreciate that someone else could set the bug status to confirmed:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/220568](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/220568)

For those who keep posting about font tweaking, upgrade issues and resolution please be aware that for the tests (check the screnshots on the bug report) I have used LiveCDs, the resolution was set to 1680x1050.

Thanks

---

### Post by robbie75 on 2008-04-28
> **Deeta said:**
> It seems I found a solution for the lacking subpixel hinting in QT4 and the Gnome-Terminal.

It indeed seems it is a bug introduced in Hardy (see appendix)

Ubuntu uses several font-rendering configuration frontends.
The one we all know is the GUI one that can accessed from gnome.

The other one can be accessed by:
1. open terminal
2. sudo dpkg-reconfigure fontconfig-config
3. choose 'native' (autohinting might be ok too, but try native first :)
4. choose 'always' (as of yet autodetection seems to be broken within qt4 in hardy)
5. choose 'no' (you likely do not want to have non-scalable bitmapped fonts ;-)
6. log out and login again (X needs to be restarted, that is why ;-)

Here some further info and links:
[http://www.ubuntutips.net/node/35](http://www.ubuntutips.net/node/35)
[https://bugs.launchpad.net/gnome-terminal/+bug/190848](https://bugs.launchpad.net/gnome-terminal/+bug/190848)

Toodles :)
Deeta

Thanks to your seggestion i've solved my problem: now fonts in gnome terminal and in skype (qt4 apps) looks good as usual.
Thank you!
Rob

---

### Post by bigube on 2008-04-29
Same problem. Ubuntu 8.04 "Hardy" to read fonts

---

### Post by perce on 2008-06-25
I had problems with fonts in gnome-terminal (ugly) and in skype (too small). The solution suggested in this thread fixed gnome-terminal, but not skype.

---

### Post by juamez. on 2008-06-27
> **perce said:**
> I had problems with fonts in gnome-terminal (ugly) and in skype (too small). The solution suggested in this thread fixed gnome-terminal, but not skype.

The same is still true for Opera (every version), which is a stone cold shame.

---

