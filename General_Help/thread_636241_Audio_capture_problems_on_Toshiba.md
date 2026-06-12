---
title: "Audio capture problems on Toshiba"
date: 2007-12-09
forum: General Help
---

### Post by watson!!!! on 2007-12-09
I have a Toshiba Satellite and run Gusty, and this is but one in a long line of sound issues. I unfortunately have the HDA Intel sound card that Ubuntu is riddled with bugs for, and although I was able to finally get audio playback working, I'm still unable to get any audio capture, either through my internal microphone or my line in jack. I've been trying to record a microkorg synthesizer into audacity that is connected through the line in, but no matter what I try, it's as if it wasn't receiving any signal at all.

I'm not good with linux, so I'm pretty lost when it comes to technical issues like this. The only place I know where to start is this: whenever I try to test audio capture in Preferences>Sound, I get this error message:

Failed to construct test pipeline for 'gconfaudiosrc !
audioconvert ! audio resample ! gconfaudiosink profile=chat'

What can I do?

---

### Post by omarabdelhaleem on 2008-03-20
Any luck solving the audio capture problem with the Toshiba? I've just joined the forum; basically having the same issue (got the audio playback on speakers and headphones, but can't record anything). I'm hoping you were able to solve it since your post; please let me know -- and thanks in advance!

---

### Post by omarabdelhaleem on 2008-03-21
Watson: Take a look at Ubuntu user jjalocha; go to Search here at the Ubuntu forum and type in ''Microphone Input Solution''. Read especially the following section: 

[B]The solution needs the alsamixer and amixer command line tools. If they aren't installed already, you need to install the 'alsa-utils' package (using for example Synaptic).

From the command line, you can use alsamixer. Use TAB for selecting the 'Playback', 'Capture' or 'All' window, and use LEFT/RIGHT to select the desired control. You have to make sure you get the following settings right (all of them):

    * All channels must be non-zero (use UP/DOWN).
    * 'Capture' must be enabled (use SPACE).
    * Select the correct 'Input Source' if you have more than one. (I only have 'Mic'.)


In my case, i had to enable 'Capture'. This is how it looked before the change (not-working). Note dashed line above 'Capture':[/B]

To install alsa-utils, do the following: Go to the menu bar at the top of your Ubuntu desktop, then System --> Administration --> Synaptic Package Manager. Type alsa-utils in the search window and see if Synaptic finds it; if not, then you need to change your settings in repositories. Reply and I can show you how to do that.  

After you've installed alsa-utils, close Synaptic and then go to the command line. The ''command line'' is found by following the menu bar at the top: Applications --> Accessories --> Terminal. Type in alsamixer at the prompt and then follow the rest of the instructions. To change the levels on the bars, you will need to press the UP and DOWN arrows on your keyboard. Go to 'Capture' and press the UP arrows until you are ''in the green''. Close the alsamixer window and try recording your voice on Sound Recorder; you should be able to hear yourself. Good luck! :popcorn:

---

### Post by fabietto0102 on 2008-03-21
Hi,

I have a Toshiba Satellite too and can't get the microphone to work properly. I adjusted all settings as described (Capture is 100%, see screenshot) but to hear my voice I need to yell at the microphone. That is to say, the mic works but it records at a too low volume. 

Please any help how to higher the volume is highly appreciated. 

Thanks
Fabio

---

### Post by pinballkid on 2008-04-20
I've just installed Hardy beta on the same laptop and I can confirm the problem. Is there a launchpad bug for this?

---

