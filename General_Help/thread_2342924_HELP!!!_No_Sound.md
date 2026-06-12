---
title: "HELP!!! No Sound"
date: 2016-11-11
forum: General Help
---

### Post by sasafrass452 on 2016-11-11
My sound is gone for some reason. All I can hear is my Thunderbird notification. I can't hear music or video, not even online. I checked my sound settings, & nothing is muted or turned all the way down. Even my headphones don't work. What do I do? PLEASE HELP!!!

---

### Post by RobGoss on 2016-11-11
Hello and welcome to the forum

Open up a terminal and run this command

```
 alsamixer
```

Make sure all the level are up

This may also help with your problem 
[https://wiki.ubuntu.com/Audio/Alsamixer](https://wiki.ubuntu.com/Audio/Alsamixer)

Hope this helps

---

### Post by sasafrass452 on 2016-11-11
This was no help. I don't see anything to check volume levels, & no way to select anything. It's totally useless.

> **RobGoss said:**
> Hello and welcome to the forum

Open up a terminal and run this command

```
 alsamixer
```

Make sure all the level are up

This may also help with your problem 
[https://wiki.ubuntu.com/Audio/Alsamixer](https://wiki.ubuntu.com/Audio/Alsamixer)

Hope this helps

---

### Post by RobGoss on 2016-11-11
If you take the time to read the help page I posted about how to increase and decrease, the  volume on the Alsamixer you would see how to accomplish the changes

---

### Post by sasafrass452 on 2016-11-11
I tried that, & nothing happened. Like I said, I couldn't see any settings or select anything.

> **RobGoss said:**
> If you take the time to read the help page I posted about how to increase and decrease, the  volume on the Alsamixer you would see how to accomplish the changes

---

### Post by RobGoss on 2016-11-11
What distrobution of Ubuntu are you currently running?

When you ran the Alsamixer command from the terminal were you able to launch the mixer?

---

### Post by sasafrass452 on 2016-11-11
I'm using Ubuntu 16.10

No, I didn't see the mixer.

> **RobGoss said:**
> What distrobution of Ubuntu are you currently running?

When you ran the Alsamixer command from the terminal were you able to launch the mixer?

---

### Post by RobGoss on 2016-11-11
Have you check in the sound setting to see if your device is listed on the output? in most cases your device should be hight lighted as the default device

---

### Post by sasafrass452 on 2016-11-11
Yes, it's listed there.

> **RobGoss said:**
> Have you check in the sound setting to see if your device is listed on the output? in most cases your device should be hight lighted as the default device

---

### Post by RobGoss on 2016-11-11
Try running this command 

```
   lspci 
```

Post the output using the code tags

it should show what sound card your machine is using it will be helpful for others to trouble shoot your issue as well

Another thing I was thinking of maybe you need to install the necessary drivers for your sound card

You can open up **software & updates,** and choose **Additional drivers**,  choose the appropriate drivers for the device you have

---

### Post by sasafrass452 on 2016-11-11
Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller

I already have the necessary drivers. The sound was working yesterday.

> **RobGoss said:**
> Try running this command 

```
   lspci 
```

it should show what sound card your machine is using it will be helpful for others to trouble shoot your issue as well

Another thing I was thinking of maybe you need to install the necessary drivers for your sound card

You can open up **software & updates,** and choose **Additional drivers**,  choose the appropriate drivers for the device you have

---

### Post by RobGoss on 2016-11-12
Were there any changes you might have made to the system that may have caused the sound to stop working?

---

### Post by sasafrass452 on 2016-11-12
No, unless it was an update. But I would think that's unlikely. I really need to fix this asap, I hope someone can help!

> **RobGoss said:**
> Were there any changes you might have made to the system that may have caused the sound to stop working?

---

### Post by RobGoss on 2016-11-14
I've try to provide as much help as I can but I'm wondering what happen if you try to view YouTube videos have to checked to see maybe the video it self is muted?

Hopefully someone else might have some insight on this issue.

Also have you tried running a live USB to see if you have sound available

---

### Post by sasafrass452 on 2016-11-14
As I said in my original post, nothing is muted. The sound was working before, but suddenly went silent. I need this fixed asap, I hope someone can help!

> **RobGoss said:**
> I've try to provide as much help as I can but I'm wondering what happen if you try to view YouTube videos have to checked to see maybe the video it self is muted?

Hopefully someone else might have some insight on this issue.

Also have you tried running a live USB to see if you have sound available

---

### Post by nothingspecial on 2016-11-19
Post a screenshot of sound settings and alsamixer

---

### Post by sasafrass452 on 2016-11-19
As I've said before, NOTHING was muted or changed(other than possible update) when this problem occured. It just seemingly happened out of nowhere. Screenshots are attached.

> **nothingspecial said:**
> Post a screenshot of sound settings and alsamixer

---

### Post by nothingspecial on 2016-11-19
```
lspci | grep Audio
```

---

### Post by nothingspecial on 2016-11-19
oh, you already did this, sorry

---

### Post by #&amp;thj^% on 2016-11-21
Sorry to hear this.
And as a late comer to this thread have you tried:
```
sudo alsa force-reload
```
And it would be good idea to reboot after this has ran...(it usally takes a few seconds to minute to complete.)
Now if that brings no joy. you can also try this method:
```
sudo apt-get remove --purge alsa-base pulseaudio
```
Followed by:
```
sudo apt-get install alsa-base pulseaudio
```
And force reload Alsa again:
```
sudo alsa force-reload
```
Restart and Hopefully enjoy your sound again.

---

### Post by sasafrass452 on 2016-11-22
I tried all of this, & things just went from bad to worse. I still have no sound. The sound icon on the upper right corner disappeared. I managed to reinstall it, but my system settings manager(or whatever it's called) is gone. The icon is missing from the launchbar on the left side of the screen, & if I click on the wheel in the upper right corner & choose "system settings", nothing happens. How do I get it back?

> **1fallen said:**
> Sorry to hear this.
And as a late comer to this thread have you tried:
```
sudo alsa force-reload
```
And it would be good idea to reboot after this has ran...(it usally takes a few seconds to minute to complete.)
Now if that brings no joy. you can also try this method:
```
sudo apt-get remove --purge alsa-base pulseaudio
```
Followed by:
```
sudo apt-get install alsa-base pulseaudio
```
And force reload Alsa again:
```
sudo alsa force-reload
```
Restart and Hopefully enjoy your sound again.

---

### Post by #&amp;thj^% on 2016-11-22
Well this is certainly not the normal results...I suspect something a muck with the install.
This is the way to reset Unity if you are running Ubuntu Unity...and if not I will need to know what desktop you are running.

```
sudo apt-get install unity-tweak-tool
```

And then to reset Unity run this:

```
unity-tweak-tool --reset-unity
```

And post back the results of this:
```
 apt-cache policy unity-control-center
```

And just one question...is there a reason you need to run a point release? IE Yackkety(16.10)
16.04.1 has been a rather smooth experience for myself anyway. Plus 5 year support (and i know you already know this)

---

### Post by sasafrass452 on 2016-11-22
That's it!!! The unity control center. I had to reinstall it, but my settings are back now!!!

Now, about the sound issue.... What else can I try?

> **1fallen said:**
> And post back the results of this:
```
 apt-cache policy unity-control-center
```

---

### Post by #&amp;thj^% on 2016-11-22
Well let me see what it thinks is installed.
```
inxi -A
```
Post back the results from the above.
And you may have to install "inxi"
```
sudo apt install inxi
```
Mine looks like this:
```
inxi -A
Audio:     Card-1 NVIDIA GF106 High Definition Audio Controller
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel
           Card-3 Creative Labs SB Audigy driver: snd_emu10k1
           Sound: Advanced Linux Sound Architecture v: k4.4.0-49-generic


```

---

### Post by #&amp;thj^% on 2016-11-22
The Forums seem to be a little ify today...And i have some things to get done so I will check back in few hours.
See this if you want...and I was going to suggest the same anyway.
[http://askubuntu.com/questions/163225/how-do-i-install-new-intel-hda-sound-drivers](http://askubuntu.com/questions/163225/how-do-i-install-new-intel-hda-sound-drivers)

---

### Post by sasafrass452 on 2016-11-22
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] Kabini HDMI/DP Audio
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.8.0-27-generic

> **1fallen said:**
> Well let me see what it thinks is installed.
```
inxi -A
```
Post back the results from the above.
And you may have to install "inxi"
```
sudo apt install inxi
```
Mine looks like this:
```
inxi -A
Audio:     Card-1 NVIDIA GF106 High Definition Audio Controller
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel
           Card-3 Creative Labs SB Audigy driver: snd_emu10k1
           Sound: Advanced Linux Sound Architecture v: k4.4.0-49-generic


```

UPDATE: I previously had my Thunderbird notification sound, but now that no longer works, either. I appreciate any help I can get to fix this!!!

---

### Post by #&amp;thj^% on 2016-11-22
Ok going back and re-reading this whole thread...and where it was suggested to run in the terminal
"alsamixer" and you had said... and I quote
> I tried that, & nothing happened. Like I said, I couldn't see any settings or select anything.
Leads me to again wonder about this install being good. But that said I can see no reason that your sound is not working...I have a similar card built in audio..." Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)   driver: snd_hda_intel" and yours shows the driver is installed.
Now for one last attempt at getting you some sound have you yet installed "PulseAudio Volume Control (pavucontrol) "
And if not install it with:
```
sudo apt install pavucontrol
```
Now open the pavucontrol and check under the Configuration tab at the top (Click that) you may have to resize or scroll to right to see that tab.
Now in the Center of that window you see your cards (Or you should see your sound cards) and you may have to cilck and have it show "Analog Stereo Duplex"
Now if everything is good you "should" now have sound.
Screenshot included.

---

### Post by Yellow Pasque on 2016-11-22
If pavucontrol doesn't help, try clearing pulseaudio settings (and restarting pulseaudio):
```
rm -r ~/.config/pulse* ~/.pulse-cookie
pulseaudio -k
```

More info may help:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by sasafrass452 on 2016-11-23
Pavucontrol is set to "Analog Stereo Duplex". What next?

> **1fallen said:**
> Ok going back and re-reading this whole thread...and where it was suggested to run in the terminal
"alsamixer" and you had said... and I quote

Leads me to again wonder about this install being good. But that said I can see no reason that your sound is not working...I have a similar card built in audio..." Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)   driver: snd_hda_intel" and yours shows the driver is installed.
Now for one last attempt at getting you some sound have you yet installed "PulseAudio Volume Control (pavucontrol) "
And if not install it with:
```
sudo apt install pavucontrol
```
Now open the pavucontrol and check under the Configuration tab at the top (Click that) you may have to resize or scroll to right to see that tab.
Now in the Center of that window you see your cards (Or you should see your sound cards) and you may have to cilck and have it show "Analog Stereo Duplex"
Now if everything is good you "should" now have sound.
Screenshot included.

"No such file or directory". Now what?

> **Temüjin said:**
> If pavucontrol doesn't help, try clearing pulseaudio settings (and restarting pulseaudio):
```
rm -r ~/.config/pulse* ~/.pulse-cookie
pulseaudio -k
```

More info may help:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Yellow Pasque on 2016-11-23
> Now what?
Give the info requested: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by alan-q on 2016-11-23
In solidarity with the original poster, and in the hope that this might help... 

I have a similar problem on Ubuntu 16.04 MATE 64bit AMD. 

I suspect an update bug as I too changed nothing before it happened. 

No sound on Firefox or Chromium when watching videos -- both YouTube and Vimeo. 
No sound on games -- eg LBreakout2 and Trigger. 
No sound on anything running on Lubuntu16.04 running under Virtualbox. 

Sound OK on VLC media player, and (most thankfully) on Arora web browser (arora-browser.org) -- YouTube and Vimeo work fine.

---

### Post by sasafrass452 on 2016-11-27
Ok, this is interesting.... Wednesday morning, I had no sound. I left home for 3 days, & this morning I turned on my computer, & the sound is back!!!!! I don't remember if there were any updates before I left, but I was pleasantly surprised when I opened thunderbird this morning & the notification played!!! I then opened vlc & tried playing music, & it works!!! Then I tried youtube, & that works as well!!! I can only guess that an update was responsible, but who knows? I'm just glad this problem has been resolved!!!

---

### Post by alan-q on 2016-12-01
Lucky you,[**[COLOR=#000000] sasafrass452[/COLOR]**]("https://ubuntuforums.org/member.php?u=1885555"). I still have mostly no sound.

---

### Post by #&amp;thj^% on 2016-12-01
> **alan-q said:**
> Lucky you,[**[COLOR=#000000] sasafrass452[/COLOR]**]("https://ubuntuforums.org/member.php?u=1885555"). I still have mostly no sound.

@ alan-q It might be helpful to start your own thread With **"No sound with Ubuntu 16.04 MATE 64bit AMD"** and following what Temüjin advised: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
Might give (Us or Someone) a clue in how to proceed.
Starting your own thread helps keep this one and yours clean and far easier to understand.
And just curious if you have tried all the above posts already?
Kind Regards and Good Luck

---

