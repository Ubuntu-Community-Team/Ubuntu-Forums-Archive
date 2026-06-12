---
title: "Microphone dilema"
date: 2007-04-01
forum: General Help
---

### Post by Dream. on 2007-04-01
When I go to system/preferences/sound and click 'test' sound capture, there is a crackling noise in the background and the sound cuts in and out (intermittently but I get a few seconds of my voice and crackling then a few seconds of nothing and so on).

Sound capture is set to ALSA, the other playback settings are all on Autodetect.

My sound card is a Creative Vibra128 but the Default sound card is listed as Ensoniq AudioPCI with no other cards listed. 

If I run lspci I get this..

```
02:04.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
```

Could this be a driver issue with the system not picking up the creative vibra128 properly?


Other maybe useful information...

If I go to sound recorder and record, it then plays back fine. In volume control the device is set to Ensoniq AudioPCI.

I am using gyachi yahoo chat client where my mic also sounds terrible with crackling & cutting in/out etc.

My soundcard and microphone work fine under windows.

---

### Post by Dream. on 2007-04-01
I have been looking for more information and apparently the creative vibra 128 uses the Ensoniq ES1371 Audio PCI chip, which leads me to believe the driver would be correct.

Any other ideas anyone?

---

### Post by garybrlow on 2007-04-01
Am using a VIbra 128 and it uses Ensoniq as the default driver. It works just fine. I use to record voice using audacity. It could be a microphone issue but nowadays microphone input is broken on feisty beta but if you use dapper you shouldn't have problems. You could try the Edgy drivers. I did get nose and crackling before but it doesn't come out in the final recording.


Cheers!!!


GaryBrlow :biggrin:

---

### Post by Dream. on 2007-04-03
GaryBrlow, Im using edgy 6.10 so I figure I'm already using the edgy drivers as you suggested.

I still cannot resolve this problem and until I do its forcing me to use windows, anyone got any ideas?

---

### Post by Dream. on 2007-04-06
Can someone tell me how to reinstall or update the driver pls. 

Failing getting the mic to work, ubuntu will end up in the trash.

---

### Post by garybrlow on 2007-04-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Its an ALSA bug not a driver problem. Read, Review, Confirm here [https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531). Please register to post reports and confirmations and help Ubuntu become better.

A fix has been committed to sound capture related bugs.


Cheers!!!


GaryBrlow :biggrin:

---

### Post by Dream. on 2007-04-06
> **garybrlow said:**
> A fix has been committed to sound capture related bugs.

Thanks garybrlow, Ive just spent 45 minutes reading through the link you supplied as well as the other various links posted there, but I dont see a fix anywhere as per your comment?

I was going to ramble some more here but I will make a seperate thread.

---

### Post by PilotJLR on 2007-04-06
Dream, try appending apci=ht to kernel parameters in grub and reboot:
[http://www.linuxreality.com/forums/index.php?topic=1150.msg8450](http://www.linuxreality.com/forums/index.php?topic=1150.msg8450)


I also found a reference saying to use OSS instead, but I would try this second:
[http://puggy.symonds.net/~deep/vibralin.html](http://puggy.symonds.net/~deep/vibralin.html)

---

### Post by Dream. on 2007-04-06
Thanks PilotJLR, both those links address the sound card not working but that is not my problem.

Its the microphone not working, my sound works fine, extract from my original post...
-------------------------
When I go to system/preferences/sound and click 'test' sound capture, there is a crackling noise in the background and the sound cuts in and out (intermittently but I get a few seconds of my voice and crackling then a few seconds of nothing and so on).

If I go to sound recorder and record, it then plays back fine. 
-------------------------

This is what I don't understand...

Using sound recorder it sounds very good, clear as a bell.

But testing it under system/preferences/sound it sounds very bad, and the transmitted ouput into yahoo chat (and I presume skype etc would be same) sounds terrible also. To describe the ouput further, there is a VU meter on a yahoo chatroom window which tells you the volume level of the person talking on mic. When I try and talk, the VU meter is at maximum level yet my voice sounds very weak and there is a lot of crackling/background distortion.

From what I have read others have the same problem which can be seen by reading the link that garybrlow posted  [https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531) 

There doesn't appear to be a solution anywhere.

---

### Post by Dream. on 2007-04-07
Just a little update... I decided to overlook the microphone problem for the time being and decided to get the media apps to function correctly. 

After following all the instructions found at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and then at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) as per the instructions on the restricted formats page, guess what, dvd's will not play as the pages say they will, why am I not surprised.

So anyway, I got up this morning and thought I would tackle the microphone issue, well at least try to. I tested the onboard sound and guess what, exactly the same problem with both audio setups.

I thought hmm, so I tested my microphone on two other computers, it works fine, as it does on this computer in windows.

Bottom line... With all the hours waisted trying to get this to work I could have bought several copies of windows :) :) :) :) :) :) :)

---

### Post by bcmiller on 2007-04-07
why do you keep threatening to go back to Windows?  

do you think the ppl here are going to lose the commission?

There is an answer to this problem.  I found this thread because my mic isn't working either after a new install.  

If you don't get the answer you want look on [http://www.linuxquestions.org](http://www.linuxquestions.org) and you can also test out another linux distro to see if it's detected automatically.

If I find out the solution to my issue I'll post it back here.

---

### Post by Dream. on 2007-04-07
Im not threatening anything, ubuntu is now gone. Edit: well not quite, I will try several different cards frst.

And sincerely, good luck fixing it. 

Searching about you too will discover that you and I are not the only ones with the same problem. Funny how it happened with both my sound card and on board sound, as well as three friends of mine who also tried ubuntu.

---

### Post by llamakc on 2007-04-07
> **Dream. said:**
> Im not threatening anything, ubuntu is now gone.

And sincerely, good luck fixing it. 

Searching about you too will discover that you and I are not the only ones with the same problem. Funny how it happened with both my sound card and on board sound, as well as three friends of mine who also tried ubuntu.

Try another distro. Once you realize what is possible with Linux you'll sing a different tune. Before you do try another one, do some research and make sure your hardware is compatible.

---

### Post by duojet on 2007-04-07
It's more likely that your creative card uses a similar chipset. 
If your voice comes through weakly as well as intermittently, it might be crosstalk. 

have you checked support at the alsa website? it will often tell you which cards use similar chipsets. 

also, you might just open up alsamixer and crank stuff up. I wasn't able to make my stuff work for a week until I turned up the ADC. oops. Just make sure your speakers aren't too loud- soundcard feedback is loud and nasty.

---

### Post by garybrlow on 2007-04-08
I have an updated post containing 3 methods of  temporary fixes to this problem on the bug report. I say temporary because normally we shouldn't be doing the fixes at all. I have known Ubuntu's sound playback/capture to work out of the box ever since Dapper.


For those having problems with here's temporary fix:

Method A:
The ALSA update sets the mic input to mic number 2 so you have to return it to number 1 for default mic. Using GNOME/XFCE GUI may have no effect. You have to use the alsa mixer on by typing alsamixer on the terminal. Use the left and right arrow keys to navigate the column setting. Press left until you reach <Mic Sele> and you will see that it is set to Mic2 use up/down arrow keys to toggle the setting to Mic1. Mute Mic Column by pressing down all the way to the bottom. Go to Capture tab by pressing tab until you get there. Then go to Mic column again and press spacebar the word CAPTUR and L R appears on the column. Bring volume up by pressing up arrow(doesn't really work but another guide said to do this, taken form a Gentoo post which i have not bookmarked and don't know here to look). The Capture column should have the same markings and bring the volume up as well. You may have to use sudo if regular user can't set anything. If this has no effect use Method B. This hasn't worked for me either but it worked for others.

Here some more info by ComputerGuy56 found here [http://ubuntuforums.org/showthread.php?t=382106](http://ubuntuforums.org/showthread.php?t=382106) on a similar solution.

Method B:
Even if you use GNOME or XFCE and since their own sound control GUIs seems to have no effect including the alsamixer, install the kmix package. I know it sounds weird installing kmix and you're not even using KDE believe me strangely enough it works. After installation run kmix, it might not appear in the application menu so use terminal instead. Go to the input section locate mic and select mic 1. You should immediately hear sound input from your mic. Close kmix and you may uninstall it after this. For me and other users this actually did the trick.

Method C:
If all else fails you have to reset and cleanly reinstall ALSA and the Linux sound modules. You can even make without Method A and B and use this instead. Am not very sure about the result on this one but you could provide your experience on what happens. This method taken from the  Comprehensive Sound Probelm Solutions Guide - Getting the ALSA drivers from a *fresh* kernel section  found here   [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound). Refer to the guide first before doing anything.

Via the terminal run the following commands:

1) To remove the related packages and configuration files: 

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

This will also uninstall gnome-desktop, xubuntu-desktop and GDM on Ubuntu/Xubuntu so just reinstall them as well.

2) Reinstall those same packages: 

sudo apt-get install linux-sound-base alsa-base alsa-utils

3) Reinstall GDM and the desktop package: 

sudo apt-get install gdm ubuntu-desktop (ubuntu)
    
Reinstall GDM and the desktop package: 

sudo apt-get install gdm xubuntu-desktop (xubuntu)


All this were tested using feisty and may also be applicable to edgy and dapper. Please try it out and see what works best for you. :p


Cheers!!!


GaryBrlow :biggrin:

---

### Post by Dream. on 2007-04-09
Hi garybrlow, None of these help my situation, methods A&B to set mic2 to mic1 are of no use as I can go to volume properties and switch it in there.

> Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

The above quote, extracted from link in method C wont work either as I have tried a fresh install.

The mic works but very poorly.

I will try some different sound cards later today and post back with the results.

---

### Post by garybrlow on 2007-04-09
You have to use the command line alsamixer, volume properties have no effect, but in my case kmix did it. :) I use a Creative Vibra 128 sounds great. Newer models are better. Sadly XIFI isn't supported yet. Creative is keeping its technology secret and promised to provide Linux drivers for it. But apparently it hasn't appeared yet.

Cheers!!!


GaryBrlow :biggrin:

---

### Post by Dream. on 2007-04-10
garybrlow, my sound sounds great too, read what I am saying, 

my microphone sounds like crap, I dont need to go into anywhere and select mic1 it is already selected.

---

### Post by Dream. on 2007-04-10
I tried all three methods as per garybrlow's instructions (alsamixer, kmix, and removing/reinstalling alsa and linux sound modules) and none of them worked.

Here's my results from sound card testing:

Note: All sound cards worked as far as sound goes, but microphone was a different story....

A. I tried a Creative Vibra 128, microphone works but very scratchy, lots of static, poor quality and very low sound.

B. I tried the onboard sound (intel chip) and I got the same result as with the creative vibra128, microphone works but very scratchy, lots of static, poor quality and very low sound.

C. I tried a Creative Sound Blaster Live CT4830, could not get microphone to work at all

D. I tried a Creative Sound Blaster Live 5.1 digital Audigy4 SB0610. I got the microphone to record and ouput sound from sound recorder, but when played back sounded like a chipmunk, and when tested from system/preferences/sound I got no output at all.

This is a major bug in ubuntu that has caused me to waiste many hours now trying to get a microphone to work.

---

### Post by Dream. on 2007-04-10
I have now listed this bug at [https://bugs.launchpad.net/ubuntu/+bug/105100](https://bugs.launchpad.net/ubuntu/+bug/105100)

---

