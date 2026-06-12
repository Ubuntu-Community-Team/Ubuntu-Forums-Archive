---
title: "Sound Blaster Audigy SE (Microphone problems)"
date: 2007-12-31
forum: General Help
---

### Post by ntowakbh on 2007-12-31
For the most part, this sound card has worked out of the box, the only issue that still remains is my microphone.  I've already checked, and the microphone is NOT muted.  I don't know loads about computers, so I am just using logic here:

I have the following choices for sound capture in Sound Preferences:
> 
CA0106
CA0106
CA0106
CA0106
ALSA - Advanced Linux Sound Architecture
OSS - Open Sound System
Test Sound
Silence


For all my correct options for hearing sound, it was one of the four CA0106 values that was correct.  So one would assume that one of these would have to be the one for my microphone?  I selected each option individually(even the ones besides CA0106, even the ones that made no sense), and tried to open sound recorder, sound recorder only opened for ALSA, and OSS.  When it actually did open in those, it recorded no sound.

For every other option, attempting to open sound recorder returned the following error message:
> 
Your audio capture settings are invalid.  Please correct them in the Multimedia settings.


I have honestly tried searching around the net, and have yet to find the solution.  It would be greatly appreciated if someone were able to help me fix this problem.

Thanks in advance for any help.

---

### Post by darylb on 2008-01-02
I just did the exact same thing this morning with my Audigy LS trying to get skype to pick up my headset microphone, none of the settings seemed to work.
Here is the lspci output for my card:

> 01:01.0 Multimedia audio controller: Creative Labs SB Audigy LS

In gnome's sound preferences, when I choose any of the 4 "CA0106" options, the "ALSA", or even "OSS" option for Sound Capture, and click test, I get this message:

> Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

I have on board sound as well, but that is disabled in the BIOS.
I've come across a few posts with this problem, but no solution so far.

---

### Post by rubicon on 2008-01-02
I have Audigy SE, and learned so far that this model isn't so good for Ubuntu as it is good for Win. That's why its apartments right now in my toolbox :)

But back to your problem. What I want to share with you: this four devices are stereo-channels. Quite strange, though pretty logically :) And sound is recorded either from the first item or from any of them.

Did you selected your mic in alsamixer? Tick all checkboxes in preferences and find something saying 'Input source'. It will be combobox with variants 'Line in', 'Mic' and some other. You need 'mic'. Let's see what will happen. 

If sound recorder refuse to record anything, try to enable mic as recording device, set 'record feedback' slider to max and blow into your mic :) If you hear anything, then the problem is in sound recorder.

Right now I can't say anything exactly, all this is my memories :) But if you have any questions, ask!

---

### Post by darylb on 2008-01-02
Hi rubicon,

I have already chosen the input source as "mic" in the gnome volume applet and also checked it in alsamixer. It doesn't make any difference unfortunately :(

Thanks for your tip though, I think you are right about the card and the best thing for me to do might be to remove it and try the onboard sound on my motherboard instead!

---

### Post by rubicon on 2008-01-02
Yep, that's good idea to try on-board card.

If you need to record some sound now -- try on-board. Audigy SE isn't bad, it just not always works as good as supposed so :) Me, for instance, have managed to record sound from my tv-tuner on Audigy SE (tho it took pretty much time to tune it), but Crystal SoundFusion card just refuses to record anything -- either error message shows up or signal is absent. Maybe the problem is the recording program itself!

By the way, Hardy Heron 8.04 will have new sound system, PulseAudio, tuned and turned on by default. Knowing what PulseAudio ([http://pulseaudio.org/wiki/WikiStart#Whatisit](http://pulseaudio.org/wiki/WikiStart#Whatisit) and [https://blueprints.launchpad.net/ubuntu/+spec/cleanup-audio-jumble](https://blueprints.launchpad.net/ubuntu/+spec/cleanup-audio-jumble)) is, this sounds promising!

---

### Post by darylb on 2008-01-04
I pulled the Audigy SE and enabled the onboard sound. I then discovered that I was running into the bug mentioned in this thread:

[http://ubuntuforums.org/showthread.php?t=634290](http://ubuntuforums.org/showthread.php?t=634290)

Some fiddling later and I have the microphone working in Skype with the onboard, although Sound Preferences still complains with this message when I click test:

> Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

As long as it works I am happy though :)

---

### Post by rubicon on 2008-01-04
Good news :) At least your on-board card works well!

But what about Audigy SE? Have you managed to get it recording? I'm curious

---

### Post by darylb on 2008-01-04
I gave up trying lol. Once I shut the machine down to switch over I removed the Audigy to avoid myself getting confused between the two.

When I removed it though I realised that the ports are coloured oddly on the card - the microphone port is actually blue, instead of pink. So it turns out that I may have had the mic connected to the wrong port all along! (big oops). When I had been reaching round to the back of the PC to make the connection, I put it in the pink port, which on later inspection, actually turns out to be orange (I couldn't tell in low light).

I didn't do anything extra with the onboard though to get it working in Skype, I just selected all of the audio devices in turn and tried the test call. I suspect that the Audigy would have worked (in Skype at least) if I put the microphone in the correct port. There were many more options on the Audigy though (and 4 "CA0106" entries with the same name), so I think I'll stick with the onboard as long as the quality is alright (haven't really tested it fully yet) because the setup is simpler.

---

### Post by Benthe1st on 2008-01-05
Hi guys!

We have a similar discussion in on other topic: [here]("http://ubuntuforums.org/showthread.php?t=634290&highlight=microphone+test")
and we have found that this "failed to construct test pipeline..." problem is a bug of gnome, and not ubuntu, but despite that most of the microphones work! Just the test on sound preferences gives this error message, but u can record audio.

---

### Post by ScottKidder on 2008-01-15
> **darylb said:**
> I gave up trying lol. Once I shut the machine down to switch over I removed the Audigy to avoid myself getting confused between the two.

When I removed it though I realised that the ports are coloured oddly on the card - the microphone port is actually blue, instead of pink. So it turns out that I may have had the mic connected to the wrong port all along! (big oops). When I had been reaching round to the back of the PC to make the connection, I put it in the pink port, which on later inspection, actually turns out to be orange (I couldn't tell in low light).

I didn't do anything extra with the onboard though to get it working in Skype, I just selected all of the audio devices in turn and tried the test call. I suspect that the Audigy would have worked (in Skype at least) if I put the microphone in the correct port. There were many more options on the Audigy though (and 4 "CA0106" entries with the same name), so I think I'll stick with the onboard as long as the quality is alright (haven't really tested it fully yet) because the setup is simpler.

After reading this I switched my mic to the blue port, if I move the CAPTURE feedback slider all the way up I get feedback, but Any other attempt at recording does not work (Sound Recorder, Krecord, Audacity, Skype, Ekiga) I'm stumped...

---

### Post by rubicon on 2008-01-15
What exactly happens if you try to record sound? Error/warning or just no signal?

Have you tried this with different sound systems (ALSA/OSS/PulseAudio)?

---

### Post by thundercles on 2008-04-21
Okay all these "help me get the Audigy LS/ca0106 to do basic stuff" threads are filling up all my google queries to try and figure out how the heck to make a virtual PCM for alsa that will map the 4 channels of the ADC in the card the way I want, so this is my official:
(sorry about the pictures being so long if you are on a 4:3 screen, these pics will prolly break a lot of frames)

HOW TO GET SIMPLE ANALOG STEREO OUT AND 24 BIT MICROPHONE INPUT ON THE AUDIGY LS (ca0106) CARD!

I'm going to explain it very simply then provide more info at the end for people that actually want to know the useless details. As you can see in the last picture I never run surround sound but from what I can tell if you want to run surround off just 6 sets of speakers instead of going through the digital out into a 5.1 receiver, then you'd have to make a virtual PCM for that too which is what I'm already trying to figure out how to do for this card and could possibly include that in a howto I will hopefully be able to write on mapping channels for advanced configuration of this card (it needs some howtos, the snd-ca0106 module seems to be very poorly documented online unlike it's sister emu10k1). But for now this will let you hook up headphones or speakers and hear, and let you hook up a microphone to the card and record sounds or use skype or whatever using the 24 bit recording on the card.

Okay, first off the Audigy LS I'm using is the Model: SB0410, which is marketed as the "SB Live! 24-bit." Apperently there are two other models of cards that use the ca0106 chipset: the SB0310 and SB0413., it'll be written on the card which model yours is, but if it is one of the other ones the placement or colors of the jacks on the card may be different but on the software side everything should be the same, just if the exact jack I used doesn't work, just start plugging your headphones into all the jacks until you find out which one has sound. The pictures I will be using tho will be from my SB0410 as seen below:
[IMG]http://img.photobucket.com/albums/v490/thundercles1/screenshots/img_2231.jpg[/IMG]


Okay first lets be able to hear sound, Open up System>Administration>Soundcard Detection (or whatever it says in ubuntu, this is on FC 8 which I use for music production, and I use KDE in Debian; Ubuntu is just too hardcore for this long time Debian user.) But open up what you see below and make sure that you basically see what is in the below picture: 
[IMG]http://img.photobucket.com/albums/v490/thundercles1/screenshots/Screenshot-Audioconfiguration.png[/IMG]
Now you want to test and make sure the card is even working right. A common problem I face a lot is in this window where it says PCM device nothing shows up, and I know I've had that problem in debian too, so you could have it in ubuntu. That happens because there are more then one audio device being detected and the kernel might not load up all the modules, if that's the case in the console do
```
sudo modprobe snd-ca0106
```
or just something in the effect of modprobe ca0106
then go on to the next screenshot and do THAT then for good measure click the system tag in the audio configuration and smash "reset configuration files" that should pretty much make sure that the new alsa configuration will load up the correct modules when you restart.

But if it looks just like my screenshot, then click on the PCM devices there and make sure the first one is selected as in the screenshot. I will explain what all this is in the end but for the simple explanation just choose the first one. Now plug your headphones into the green jack, it is labeled as the digital out on mine but those labels on the jacks are really arbitrary in linux (it is the jack you use if you are doing the digital 5.1 spdif crap that I never do).
Now punch that play button and see if you hear anything. If not check the repeat box and punch it again and plug the headphones all the way into ALL the other jacks and see if it is putting out sound on any of the jacks, like I said the labels are arbitrary, try them ALL. Okay by now you should have found what will be your output jack, but a note is the jacks that are enabled will have some kind of sound coming when you plug the jack in to them, you'll probably hear a soft sound like when there is just snow on your TV on what will be your mic jack. If you still don't hear anything try moving the volume up on that bar under the play button and punch it again, really if the pcm modules are showing up everything should be working at this level, the sound test bypasses your alsa configuration completly, so there is either something wrong with your modules or the card itself if this sound test doesn't work at this point.

Okay once you verified the dang thing works, you gotta make sure that your Audigy LS card is what alsa chooses to use when you start up. Click on the settings tab and look at the audio cards order.
[IMG]http://img.photobucket.com/albums/v490/thundercles1/screenshots/Screenshot-Audioconfiguration-2.png[/IMG]
 This doesn't really matter but it's good practice to make Alsas default audio card index 0, but if you don't have any usb audio devices like me you can more then likely just leave this alone, that's what I'm going to recommend for this simple howto, but I'll put a section in the bottom about usb audio devices screwing up your alsa configuration all the time and making you restart your computer right after you boot up because the alsa configuration forgot where everything is, but 90% of people reading this guide will never go through that crap. 
So for Default audio card make sure it looks just like below and make sure that the "Default PCM device" is the same one you tested and know works fine in the other tab we just went over, because I guarantee it wont be fun if you try and use the 4th PCM device and find out you have to push your jacks in halfway when you tested the first one and had to use a completly different jack all the way in. I really wish they had LABELED ALL THE DIFFERENT PCM DEVICES DIFFERENTLY as I think that crap is the source of half the confusion on this card, the other half I will get to next screenshot :D but I guess us ca0106 users don't get the luxuries that the EMU10k1 people get, oh well we get the 24 bit 4 channel ADC tho :P

when you punch apply and OK it may say you gotta restart and reload your kernel modules, if it says that, this is not like windows, you do have to restart your computer, the audio drivers are not loaded in your memory correctly at this point, but if you just changed a PCM device or or nothing you wont have to and you go right on to the next step.

Okay now you are out of that and you restarted if you have to. Now right click the lil speaker in the top right corner and open up the volume control. Go to File>change device and make sure that the radio button next to CA0106 is selected then very first and foremost thing you do, and the source of the OTHER HALF of the confusion about this card is turn off that damn IEC958 switch, **if it is on, nothing will work in analog!**. As I said, the test earlier bypassed all the configurations and just hit your card directly, you gotta configure your mixer now or things may not work right, so yes your card can be loaded up right and still might not work, you gotta have this mixer set up right, but the screenshot is below of that switch that causes lots of people to pull out hair:
[IMG]http://img.photobucket.com/albums/v490/thundercles1/screenshots/Screenshot-VolumeControlCA0106Al-3.png[/IMG]
I'm pretty sure that that is all the digital out to 5.1 receiver stuff and the alsa people probably assumed that most people will be using that or something so it normally comes on by default, and the little mixer that comes up when you left click the speaker icon will be the IEC FRONT. Go ahead in the volume control and go to edit>preferences and uncheck all the IEC stuff if you arn't using the digital out to a 5.1 receiver, all that stuff will just clutter up your mixer. Turn off any other mixers that you don't need, but definetly keep all the analogs, the CAPTURE feedback, the Line in, Microphone, the one labeled JUST IEC958 with nothing else as that is the switch and you'll want to keep it in the mixer to be sure it's ALWAYS OFF, and you'll also want Analog Source, Digital Source, and Shared Mic/Line In to all be in the mixer. now exit the preferences and your mixer should be cleaned up, your IEC958 should be off. If you used the first pcm device, then the Analog Front slider is your main volume. Go ahead and try playing a song in xmms or something and adjust the analog front to make sure it is your volume, if not try the other analogs, if you used the pcm that made the black jack play sound, that is analog rear, and the 3rd pcm device should be making it play out of analog side, but you followed the simple guide and chose the first one so of course it should be analog front. go ahead and right click the speaker icon again and select CA0106 as the device you want to control and then select analog front and the little mixer bar that pops out of that icon should now move the analog front mixer.

At this point you should be hearing the music through xmms or whatever, make sure that all your analog outs are unmuted to, which they are if there is a little x over the speaker icons, just try and make your playback tab look like this:
[IMG]http://img.photobucket.com/albums/v490/thundercles1/screenshots/Screenshot-VolumeControlCA0106Alsam.png[/IMG]


Really that's about all she wrote at this point if you don't have sound, try just going back into system>admin>soundcard and click the settings tab again and make SURE that when it FIRST pops up the audigy LS shows up and "disable specific card configs" is not checked just try and make it look like my screenshot above when you first boot up and go right to that menu and tab. If you have an onboard card like me, that pesky lil devil can try and mutiny on your Audigy and be the default ccard, so change the default back to the audigy and click apply and okay and restart again and keep tweaking crap until when you boot up and go into that menu it shows the default card being the audigy and CA0106 as the Default PCM device, make sure it's one of the first three PCM devices though on default, as implied above that 4th one is odd I havn't quite figured out that one yet.

Well appears there is an 8 image limit, doublepost time---->

---

### Post by thundercles on 2008-04-21
Now for recording, go back into your alsa mixer and first up the gain on your capture feedback (I'd recommend you use headphones at least while you set up the mic for the first time, feedback is an ugly thing but you dont' want to fire up recording software just to see if the darn thing works, but if you do intend to use speakers, turn the capture feedback all the way down when using the speakers especially if you are using skype of something cause it will echo.) that is in that last screenshot, but the next one shows the options tab set it up like this:
[IMG]http://img.photobucket.com/albums/v490/thundercles1/screenshots/Screenshot-VolumeControlCA0106Al-1.png[/IMG]
make sure the analog source is set to mic I'm pretty sure this is the mic boost but just set it to mic, shared mic/line in also set to mic in, and digital source, set that to i2s in, if you don't set it to that it will not use the 24 bit ADC, there is really no reason not to use it. I havn't tried using any other digital sources, but that's probably where a lot of your recording problems are coming from. most of the time when something doesn't work in alsa it can be fixed in the alsa mixer somehow, you have a lot of power over all your soundcards' options on it.

I have my microphone plugged into the blue jack, try plugging your into that one and blow into it and see if you hear any feedback on your headset. if not try all of the other jacks except the ones your headphones are in, those two channels are aleady being used so it wont be them. Make sure you actually turned up that feedback before saying it didn't work and make sure you set up the options right, and your mic isn't muted and is turned up like in the recording tab below:
[IMG]http://img.photobucket.com/albums/v490/thundercles1/screenshots/Screenshot-VolumeControlCA0106Al-2.png[/IMG]
unlike a lot of other cards the line in doesn't need to be muted for the mic to work, the card has 4 input channels, that's my problem is finding the other two, but the Mic slider does need to be moved up and unmuted. Here are a couple shots of the back of my card and how I plugged in to them the white cable is my mic cable and the black is my headphone cable:
[spoiler=photo][IMG]http://img.photobucket.com/albums/v490/thundercles1/screenshots/img_2243.jpg[/IMG]
[IMG]http://img.photobucket.com/albums/v490/thundercles1/screenshots/img_2245.jpg[/IMG]
And so you can't accuse me of witchcraft or any other skulduggery here is a picture of me blowing in my mic and audacity recording it, plain as day to see it's not sorcery alsa just isn't as hard as everyone thinks for basic stuff, and for more advanced stuff it's not that easy in windows either so really linux wins for sound, one more point for team GNU.
[IMG]http://img.photobucket.com/albums/v490/thundercles1/screenshots/img_2247.jpg[/IMG]
[/spoiler]
Well now you all gone and done it, the reservation cigerette peddlers are closed and I'm out, nic fit time, I hope this guide helps people out so we can all move on to the real issue at hand, how to squeeze way more then my money's worth of recording power out of that CA0106 chipset.

Oh yeah and I promised a more technical thing, well the PCM devices are maps connecting your software to hardware channels on the soundcard, the PCM devices that show up on default map your output to the green as your Analog front (first unlabeled CA0106 PCM device), Black as the Analog rear (second _unlabeled_ CA0106 PCM device). and debatably pink or red jack as your analog side (third _unlabeled_ CA0106 PCM device). alright alsa developers how hard would that have been to just put "front" "rear" and "side" instead of naming all the PCM devices the same and making question marks appear above everyone's heads? That fourth one is odd, it plays output on the black and pink/red jacks but only when you push in the jack halfway, I know from working with audio equiptment before that sometimes they do that on 1/8 jacks I forget what else I ever had to do that on tho, and I have no clue what's going on on that fourth PCM device, It could also be some kind of special 3 channel pin like the cellphone ones that incorporates stereo out and mono in, also I noticed the DAC on the card has 10 channels, if those two bottom have 3 channel capability with a special plug like I mentioned above, then you could actually probably map it out to do ten outputs, depending on whether or not they have the DAC hooked up to that blue jack on the top, I havn't managed to get playback out of it yet. I really wish I could find a copy of the Audigy LS owner's manual but no site seems to have it including Creative's site, I think one might have but they wanted to sell it to me the damn pdf of the owners manual of a product I bought so screw them, if you happen to have a PDF of the owners manual for an Audigy LS or SB Live! 24-bit please e-mail it to me:
[email]thundercles@gmail.com[/email]
I think my dog chewed mine up when she chewed the box for the card (yeah I'm actually serious) but if there is anywhere there is info on those weird bottom two ports it's in there.
I noticed that creative claims that their software for this card lets you "record from two different sources at once" which almost certainly means that all 4 channels of the ADC are mapped out to the jacks somehow since they didn't ship any cables that break the two channels in the mic jack out into their own jacks, and if there is a way I'm gonna find it, I'm way too poor to buy an expensive pro 4in/4out 24 bit card, but this could almost be as good for 20 bux as one of those 100 dollar cards if I can figure out this things' PCM.

*edit- I actually got open the manual from that forsaken chm format and found out some info, first of all I'm pretty sure that the other 3 PCM devices other then the first one are for surround sound, the card supports analog 5.1, 6.1, and 7.1 and I'm fairly certain that's what those are, which means that solves it for all you surround sound people, but I have never owned one of those systems, (which is why I had no clue they used those multi-level pins) it's just that I can't say that's what they are, because I have no way of testing it, anyone has an analog surround system that wants to try it out, fire up that tester (don't rely on using that PCM device as the "default card" I'm pretty sure there is other software needed to do full surround, but that software wont work if the PCM doesn't map all the channels for it) and plug the analog surround sound system in and where it says PCM device, the 2nd one down should be the one you test if it is a 5.1, the 3rd one down if it is 6.1, and the bottom one if it 7.1, plug it in as it shows in the users manual, with the pins with the more insane numbers of inputs on the jacks closer to the motherboard. It'd be kinda nice (since they aren't labeled after all) to figure out what the other 3 PCM devices besides the top one do, but as I'm pretty sure they are all having to do with the analog surround systems I gotta leave that in your hands. As for the 4 channel recording, while the ADC is badass and should be capable of it, they did indeed only hook all the inputs to the one blue jack, and the mic in is apparently just mono too, they make the digital i/o port the same as the input jack too, which is understandable because it looks like they pretty well routed all 10 DAC channels between the other 3. It's looking like a lost cause, but That extra internal connector for some kinda breakout box I assume might be able to tap into the cards hardware a little more directly.

---

### Post by Darganot on 2008-05-10
> **thundercles said:**
> 

Okay first lets be able to hear sound, Open up System>Administration>Soundcard Detection (or whatever it says in ubuntu, this is on FC 8 which I use for music production, and I use KDE in Debian; Ubuntu is just too hardcore for this long time Debian user.) But open up what you see below and make sure that you basically see what is in the below picture: 
[IMG]http://img.photobucket.com/albums/v490/thundercles1/screenshots/Screenshot-Audioconfiguration.png[/IMG]



This menu does not exit by default in Ubuntu.  How do I install it?

Why did you write up a how to for Fedora in the Ubuntu forums?

---

