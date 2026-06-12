---
title: "No Sound - Fresh Install"
date: 2016-07-14
forum: General Help
---

### Post by blackhawk871 on 2016-07-14
Hey team,

Over the past four days I have frantically trying to install Ubuntu 16.04 onto my hard drive so that I can dual boot that and Windows. I've managed to install it a few times now and each time I run into a few deal breaking issues. 

One issue I am running into is that sound doesn't seem to be working at all. I have followed a few tutorials that reinstall and setup alsa but these don't seem to have made much of a difference (the sound still isn't working). In sound settings it is detecting two devices (the mixer and "Headphones") but when I test each of these or generally play audio I can't hear anything.

To combat these I have tried reinstalling 16.04 twice, trying 14.04 and even trying Fedora 24 Workstation, but the problems remain persistent across all operating systems. Furthermore, I have tried numerous online solutions for each problem with no avail.

My current hardware is:
[LIST]
[*]CPU: i5 6600k
[*]Motherboard: ASUS Maximus VIII Hero
[*]RAM: 16gb Corsair LPX 3200Mhz
[*]Sound Device: Realtek HD Audio
[*]GPU: GTX 690
[/LIST]

I'd love to get Ubuntu working so that I can use it as my OS for developing on (I am a university student). 

Let me know if you have any ideas or need anymore information. The current OS I have installed is Fedora so if you need Linux information I can use that or reinstall to Ubuntu. I'd prefer to be running Ubuntu in the end.

---

### Post by Bucky Ball on 2016-07-14
Welcome. I can't help much with your issues, but this post can act to bump the thread and also to advise you that you will have more success if you edit one of your issues out of this thread and post a new thread specifically about that.

One issue, one thread is the policy here and you will find that is what brings the most success. Trying to work on more than one on the same thread only gets confusing.

Good luck. :)

(PS: I wouldn't diddle too much with installing ALSA and blindly following guides at this point. I'd wait for some assistance there as you may make a cobweb we then have to unravel to get back to square one. You may only need to tweak Pulseaudio Volume Control to fix sound. PAVControl is okay when you're used to it but can be a bit confusing if you've never used it before. Not sure if it comes default with Ubuntu, but PAVC can be installed via Ubuntu Software/Gnome software/Synaptics/terminal.)

---

### Post by T.J. on 2016-07-14
First, welcome to the forums. =) I sincerely hope your time with us will be pleasant and productive.


> Over the past four days I have frantically trying to install Ubuntu 16.04 onto my hard drive so that I can dual boot that and Windows. I've managed to install it a few times now and each time I run into a few deal breaking issues. 

Sorry to hear that, friend.  Your troubles (to my experience) are rather rare these days.
 
> Firstly, using the default nouveau graphics drivers I am able to have both of my monitors plugged in via DVI and working (although the mouse is flickery and disappears a little), however as soon as I install the NVIDIA drivers (any version that is and with secure boot disabled) Ubuntu can only detect one of the monitors and when I activate the other one in Nvidia X Server Settings (which does detect it), it turns on but remains black (I can move my mouse onto it but it displays a big X). I have tried follow some tutorials online but had no success.

I'd need more specific information on your hardware before I can help you.  For example, what video card or cards, you are using, how they are installed, and if you configured them manually. I realize you said the 690, but what model, what ports?Most Nvidia cards these day have but a single DVI port. Are you using two cards, with a monitor hooked to a DVI port on each card?

> The second issue I am running into is that sound doesn't seem to be working at all. I have followed a few tutorials that reinstall and setup alsa but these don't seem to have made much of a difference (the sound still isn't working). In sound settings it is detecting two devices (the mixer and "Headphones") but when I test each of these or generally play audio I can't hear anything.

Most likely, this is the result of a PulseAudio channel being disabled.  Messing with ALSA directly is inadvisable if you don't have experience with sound hardware.  It can render your installation a challenge to repair.

> I'd love to get Ubuntu working so that I can use it as my OS for developing on (I am a university student). 

Once we get your problems solved, that should be easy.  I am a developer myself and would be happy to answer your questions.

> The current OS I have installed is Fedora 

It is your choice naturally, but I recommend not using Fedora.  It's "bleeding edge" meaning not as tested and has bugs.  Ubuntu is a decent selection for development, as long as you are using an LTS.  With respect to the fact we are speaking on an Ubuntu board, if you are considering working with straight up, server based development, it is my opinion that you should consider Debian Stable instead.  It is considerably more conservative and tested for stability more than any other community Linux.  It is equal to or superior in stability to RedHat Server.

---

### Post by blackhawk871 on 2016-07-14
First of all, thank you both for the prompt replies. General activity and friendless go along way; appreciate it!

> **Bucky Ball said:**
> One issue, one thread is the policy here and you will find that is what brings the most success. Trying to work on more than one on the same thread only gets confusing.

Will do. Thanks for the advice.

> **Bucky Ball said:**
> (PS: I wouldn't diddle too much with installing ALSA and blindly following guides at this point. I'd wait for some assistance there as you may make a cobweb we then have to unravel to get back to square one. You may only need to tweak Pulseaudio Volume Control to fix sound. PAVControl is okay when you're used to it but can be a bit confusing if you've never used it before. Not sure if it comes default with Ubuntu, but PAVC can be installed via Ubuntu Software/Gnome software/Synaptics/terminal.)

Noted. I'm about to do a fresh install, so I'll make sure I don't tinker with anything until a clearer idea of the problem and solution is worked out.

> **T.J. said:**
> First, welcome to the forums. =) I sincerely hope your time with us will be pleasant and productive.

Appreciate it!

> **T.J. said:**
> I'd need more specific information on your hardware before I can help you.  For example, what video card or cards, you are using, how they are installed, and if you configured them manually. I realize you said the 690, but what model, what ports?Most Nvidia cards these day have but a single DVI port. Are you using two cards, with a monitor hooked to a DVI port on each card?

Sure thing. I currently have one GTX 690 (Part Number: 04G-P4-2690-KR), although from what I understand the GTX 690 has two chips on the one card so it may be that Ubuntu is treating it as two cards (in NVIDA X-Settings it does state GPU 0 and GPU 1). The 690 is plugged into the first PCI slot on my motherboard. In terms of the inputs the back of the 690 has three DVI slots (see [http://images10.newegg.com/ProductImage/14-130-781-10.jpg](http://images10.newegg.com/ProductImage/14-130-781-10.jpg) for reference). My individual setup is that I have a DVI cord coming from each monitor into the two DVI slots on the same level (pictured [https://goo.gl/photos/3GMAUdoKnxw1fUYX9](https://goo.gl/photos/3GMAUdoKnxw1fUYX9)). In terms of configuration, they have just been plugged in and then had the drivers installed. 

> **T.J. said:**
> Most likely, this is the result of a PulseAudio channel being disabled.  Messing with ALSA directly is inadvisable if you don't have experience with sound hardware.  It can render your installation a challenge to repair.

Sounds good. As I said above, I'll do this fresh install and then hold off making any changes until there is a solution worked out.

> **T.J. said:**
> Once we get your problems solved, that should be easy.  I am a developer myself and would be happy to answer your questions.

It is your choice naturally, but I recommend not using Fedora.  It's "bleeding edge" meaning not as tested and has bugs.  Ubuntu is a decent selection for development, as long as you are using an LTS.  With respect to the fact we are speaking on an Ubuntu board, if you are considering working with straight up, server based development, it is my opinion that you should consider Debian Stable instead.  It is considerably more conservative and tested for stability more than any other community Linux.  It is equal to or superior in stability to RedHat Server.

Appreciate the insight!

For future replies, I am going to move the dual monitor issues out of this thread and to another one, but keep the sound issue in this thread. Thanks.

---

### Post by blackhawk871 on 2016-07-14
As an update, I have now reinstalled a fresh version of Ubuntu 16.04 LTS onto my machine. I'll wait to make any changes.

Edit: Okay, I lied a little, I tried a couple of things and have realized without changing anything that my speakers plugged into the back of my PC are working, however my headphones plugged into the front are not. I hope this helps.

---

### Post by T.J. on 2016-07-14
> **blackhawk871 said:**
> As an update, I have now reinstalled a fresh version of Ubuntu 16.04 LTS onto my machine. I'll wait to make any changes.

Edit: Okay, I lied a little, I tried a couple of things and have realized without changing anything that my speakers plugged into the back of my PC are working, however my headphones plugged into the front are not. I hope this helps.


Have you checked your Pulseaudio device via pavucontrol to make certain that your sound card is the default audio device?  On a number of setups, it will default to the HDMI device on the video card.

---

### Post by blackhawk871 on 2016-07-15
> **T.J. said:**
> Have you checked your Pulseaudio device via pavucontrol to make certain that your sound card is the default audio device?  On a number of setups, it will default to the HDMI device on the video card.

First of all sorry for the delay reply. The forums seem to have been down for maintenance most of the day for me. I believe I have done however if you couldd clarify how to do this I can make sure.

---

### Post by T.J. on 2016-07-16
> **blackhawk871 said:**
> First of all sorry for the delay reply. The forums seem to have been down for maintenance most of the day for me. I believe I have done however if you couldd clarify how to do this I can make sure.

No problem! =)  I know it has been down.  I am sorry you've had to wait.  I'll post a screenshot as soon as I can find some time.  I'm updating my Debian install presently and today is a work day for me.

---

### Post by Bucky Ball on 2016-07-16
> **T.J. said:**
> Have you checked your Pulseaudio device via pavucontrol to make certain that your sound card is the default audio device?  On a number of setups, it will default to the HDMI device on the video card.

If you read the posts prior to your posting, you'll notice we have actually done this and confirmed HDMI and analogue stereo duplex are where they should be if that is what you're talking about. 

There are a few hundred thousand of us out here. :)

---

### Post by T.J. on 2016-07-16
> **Bucky Ball said:**
> If you read the posts prior to your posting, you'll notice we have actually done this and confirmed HDMI and analogue stereo duplex are where they should be if that is what you're talking about. 

There are a few hundred thousand of us out here. :)


Apologies, Bucky.  As usual, I am not perfect, but I am glad it has been covered.

---

### Post by Bucky Ball on 2016-07-17
> **T.J. said:**
> I am not perfect ...

Right along with the rest of us, which is probably as it should be. :)

I'm starting to run out of ideas as to what could be going on if you've got any more we could throw about ... :-k But I will give this a shot.

@blackhawk871: Please confirm.

Open PAVControl. Play some music. Check the 'Playback' tab. Do you see the audio stream there and the level meter is moving about with the music? You can turn it up and down?

If so, please check the 'Output' tab. What device is that set to?

If not, please check the 'Configuration' tab and confirm you have the HDMI in the top selection and 'analogue stereo duplex' in the lower drop down.

If, in the 'Config' tab, you have it set up to 'Digital stereo (HDMI) output' up top and 'analogue stereo duplex' down bottom, in 'Output', you should see the HDMI control at top and the analogue (your laptop speakers or other analogue speakers that are _not_ HDMI) below. 

Your issue may be that your outputs set to go to the wrong physical output (minijack or HDMI) somewhere in the chain. Here's hoping because then it's just a matter of finding the right combination of settings for the physical hardware you have attached. 

I know it took me sometime to get my head around PAVControl when I was new to it, but when you 'get' it, it's a neat and powerful tool.  

Anyhow ... Outcome?

---

### Post by blackhawk871 on 2016-07-18
Thanks for the reply once again.

Playback Tab: [http://i.imgur.com/5uJhObE.png](http://i.imgur.com/5uJhObE.png)
Output Devices Tab: [http://i.imgur.com/A9NlhNt.png](http://i.imgur.com/A9NlhNt.png)
Configuration Tab: [http://i.imgur.com/OfxbokI.png](http://i.imgur.com/OfxbokI.png)

My settings seem to be what you've described as being the correct ones. I'll have a play with the configuration to see if I can get my Headphones working and any other input is appreciated!

**Edit:** I just noticed that if I take my headphones out of the front headphone jack the "Port" under "Build in Audio Analog Stereo" changes from "Headphones (Plugged in)" to "Line Out (Plugged In)" and vice versa when I plug it back in (the screen shots will explain it better. The entire time audio is only coming from the speakers plugged into the back.

Physical headphone jack plugged in: [http://i.imgur.com/F35XHsI.png](http://i.imgur.com/F35XHsI.png)
Physical headphone jack not plugged in: [http://i.imgur.com/4J0bHxP.png](http://i.imgur.com/4J0bHxP.png)

I suspect that this has something to do with it.

---

### Post by Bucky Ball on 2016-07-18
Ok. There's a problem, or at least an anomaly, Houston. Built-in analogue: check, but why are there two identical sound cards, GK104 HDMI, in Configuration? Have you got two identical physical sound cards in the machine? Are the options in the drop-down menus identical also? 

This device also appears in the Output tab, but can't see the whole entry. Can you have a look down and see what port that's using???

I'm presuming this is a desktop as you say you have the speakers in the back. Please explain how it is physically configured. Have you got the speakers into the audio inputs of a sound card independent of the motherboard or the audio inputs on the motherboard, all of which are sticking out the back panel?

Did you try and add/delete/modify virtual inputs, if you can remember, during your ALSA adventures?

* Idea. If the two GK104 entries are identical in every way you can see - and you haven't got two identical sound cards in the machine - go to Configuration and select 'off' from the drop-down list of one or the other (experiment). 'Shot in the dark' thought.

Don't touch anything with the analogue channel. That looks all good from what I can see.

* Ding. Another thought. Is the second entry in the Output tab routed to 'headphone' by any chance??? If so, plug the headphones into the other headphone socket!

Some desktops allow you to plug in front and back and some audio cards have headphone socket. Use the other one. Have a look around the back and see what you can see and experiment with it, or switch that second device entry 'off' in the Config, as suggested.

---

### Post by blackhawk871 on 2016-07-20
Sorry for the late reply.

For some reason, the forums haven't let me reply for the past three days.

Here is my reply: [http://pastebin.com/gvdcue54](http://pastebin.com/gvdcue54)

---

### Post by Bucky Ball on 2016-07-21
Are you talking about this being the change you made?

[QUOTE=Michael Cornelius@askubuntu]Open the terminal and enter the following commands:

cd /usr/share/pulseaudio/alsa-mixer/paths/
sudo cp analog-output-headphones.conf analog-output-headphones.bak
sudo nano analog-output-headphones.conf

Look for the section called [Element Speaker] and change it so that it looks like this:

[Element Speaker]
switch = on
volume = ignore

Save the changes and exit nano.

Create a backup of the corrected analog-output-headphones.conf:

sudo cp analog-output-headphones.conf analog-output-headphones.fixed

Now you can restore the fix if a future installation or update overwrites it.

Reboot.[/QUOTE]

? If so, please restore file to what it was as those changes didn't fix. If you try something and it fails to fix, best to put it back to how it was previously (which means copying the analog-output-headphones.bak file you created during those instructions back to analog-output-headphones.conf).

```
sudo cp analog-output-headphones.bak analog-output-headphones.conf
```

'mv' moves it, 'cp' copies it. Best to copy as if you want to have another go at the file, you still have the original backup. This is rule of thumb whenever you change a file. Make a .bak file first until/unless you are confident you know what you are doing and can remember, or have written down, the changes you've made. :)

Bit busy at mo but will look deeper a bit later. You might want to post what you have on pastebin here as it will be easier to read.

---

### Post by blackhawk871 on 2016-07-21
The file has been restored. And yeah, apologies for the pastebin reply; for some reason the forums wouldn't let me post it here.

---

