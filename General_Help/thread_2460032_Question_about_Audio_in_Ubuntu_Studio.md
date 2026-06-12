---
title: "Question about Audio in Ubuntu Studio"
date: 2021-03-31
forum: General Help
---

### Post by gamestreamer on 2021-03-31
Hello, I am not sure where this belongs

I got a question about audio line in on ubuntu studio.   I know little bit of linux, but not much. I had a windows 10 system and decided to reformat and try linux out. 

I stream games from my phone and seem to be liking linux better for streaming. 

I will try and explain the best i can, what i am dealing with.  

I have ubuntu studio installed on a precision T3500 64 bit system. I have a sound card for back ports and i have audio ports in the front. I have speakers plugged in the back and headphones with a mic plugged in the front. Everything is updated as current as can.

I stream call of duty mobile from my phone, so i have the phone audio going into the line in, in the back port.

The issue i am having is that i can hear sound from the speakers or headphones okay. When i try to play music or the game from the phone, i can't hear anything, yet i have signal coming through. 
I have looked at the sound settings and see sound coming through, i just can't hear anything from the line in.  

Is there a option to listen to device for line in, like there is on windows system?  I just thought about that, i know i had to have that checked into order to hear anything from the line in, but don't know if there is anything like that on linux.

I opened obs and set it up like i had for streaming, i have audio coming through, each section - desktop, line in, mic. When i record a video, i can hear the sound from line in, but i can't hear anything before the video is made.  I can only hear the line in sound, after i make the video.   It kind of stinks when playing a game and can't hear whats going on.

it is strange, but i am not sure what else i could do.  Any help is much appreciated. 

I did make a video on my YT channel that might help with the visual side of explaining the issues.

this is the link to that video, if i can post links.  [https://www.youtube.com/watch?v=P94-BQ12aic](https://www.youtube.com/watch?v=P94-BQ12aic)

---

### Post by CatKiller on 2021-03-31
Since you picked Ubuntu Studio, you'll already have JACK installed. It's not especially beginner-friendly, but it does let you arbitrarily route low-latency audio streams between applications, inputs, and outputs.

Otherwise you can use PulseAudio's ability to duplicate audio inputs and outputs as monitors. You'll have more latency, but it's easy enough as I recall.

---

### Post by gamestreamer on 2021-04-01
Okay, i was looking at some of those programs to see if they would help.  I think it would help if i knew more about linux and everything. :)

I do like the studio version, as it already gives the video, audio, and photography software.  I think i may like linux better for video editing, it is faster than windows. More different, but faster.

I will try those out and see how i do, i will post update, if i am able to fix my issues.  Thanks for the advice.

If there is a version of OS, i should look at, that might be better for me, i would be glad to check it out. I don't mind reformat and reinstall, i have done that many times.

---

### Post by CatKiller on 2021-04-01
When I was playing with JACK in the past, I used QJackCtl. As long as you keep in mind what you're trying to achieve (I was a sound engineer in a past life) it's fairly straightforward.

You connect whatever you want to whatever you want like this

[img]https://qjackctl.sourceforge.io/image/qjackctlGraphForm1.png[/img]

PipeWire is the future replacement for both JACK and PulseAudio, with video too, but it's not quite finished yet.

---

### Post by gamestreamer on 2021-04-01
looks interesting. I looked at the JACK and pulseaudio settings, I might have to find something that is more simple for me to understand and use.  

There is signal coming from line in (as the video showed), i just can't hear it until after i make a video.  I am guessing there is something not configured that needs to be in order for me to hear from the line in.

---

### Post by CatKiller on 2021-04-01
When you're recording, the recording software takes the signal from your line in (so it can record it) and optionally monitors the recorded signal to your speakers. By making a direct connection with JACK, or enabling the automatic duplicating of all inputs and outputs in PulseAudio (which is just a tick box, generally) you're making the connection from your line in to your speakers without the recording application as an intermediary.

---

### Post by gamestreamer on 2021-04-01
I don't see any box to check in the pulseaudio, unless i am not understanding correctly.   When i start JACK, I see the JACK source, whch is only mic input.   

Linux is fun, but lot more difficult to understand also.   

Under input devices on the pulseaudio, it shows the signal coming in.  But under playback nothing is happening, when i play audio or video from the browser it shows up under playback.  

Is there any settings for the pulseaudio or just what you see when you open the pulse control.  I see the studio set up utility, which has audio setup in it, but i don't really understand anything there.

---

### Post by CatKiller on 2021-04-01
> **gamestreamer said:**
> When i start JACK, I see the JACK source, whch is only mic input.    

That could well be your line in. Hardware manufacturers aren't terribly forthcoming with documentation, so some of it is guesswork. Try connecting it to an output and see what happens. 

> Under input devices on the pulseaudio, it shows the signal coming in.  But under playback nothing is happening, when i play audio or video from the browser it shows up under playback.   

PulseAudio works with audio streams from applications - you can send them to whatever sink you like. That's where the duplicate monitoring streams come in: they are a stream with no application, so you should be able to just point those at a particular sink. 

>  Is there any settings for the pulseaudio or just what you see when you open the pulse control. 

It's been around a while, so it's been integrated into most desktop environments. KDE's implementation is really good (they had much of the framework already set up for their own prior Phonon system) but I understand that Gnome's is really limited. In KDE you can just click on the volume widget on the panel to get access to all the options. I don't know which desktop environment you're using in Ubuntu Studio. Plus there's pavucontrol, which is kinda janky but more or less does the job, and the configuration files are well-documented. 

> I see the studio set up utility, which has audio setup in it, but i don't really understand anything there.

I've never used it. That's a thing that the devs made for Ubuntu Studio, though, right?

---

### Post by gamestreamer on 2021-04-01
while having the JACK running, i talk into the mic and i can see the level go up.  It is only picking up the mic, not the line in.  I mute the phone audio and only thing is the mic.   So JACK is only picking up mic signal.

The desktop environment is whatever it is when you install it, i haven't changed anything in that sense.  It is the latest studio version LTS.   I am thinking I may have to just have something that is a simple click to access settings and such would be the best for me.  I am trying my best to understanding what you are talking about, it is difficult to understand when don't have a visual to show what talking about.

thats probably why there is simple point and click like windows.  I don't want to install win 10, as it has so much running that doesn't need to be, but what else can i do.

Thanks so much for taking your time to help me, it is much appreciated.   I guess linux is just too much for me to understand, along with all the names of stuff that i don't really know what they are.  It is very interesting how things are named and expect people to know what they are talking about.

---

### Post by CatKiller on 2021-04-01
> **gamestreamer said:**
> while having the JACK running, i talk into the mic and i can see the level go up.  It is only picking up the mic, not the line in.  I mute the phone audio and only thing is the mic.   So JACK is only picking up mic signal. 

Well, like I said, hardware manufacturers aren't very forthcoming. The inputs for my device show up as "capture 1 & 2," but I don't need to do foldback through the computer since my sound devices can do it in hardware. 

You've said that you can record audio through your line in, you just haven't found where it is to hook it up in JACK. And it sounds like you didn't set up the monitoring channels to do it in PulseAudio. 

You can always just leave your recording going if that works for you; you don't need to actually save it. 

> I guess linux is just too much for me to understand, along with all the names of stuff that i don't really know what they are.

The names are unique so that people can easily find out about them. A Google search for "Files" (how Gnome displays the name of its file browser, Nautilus) is not terribly helpful.

No one is born knowing how to use a computer. You have to learn if you want to do it. If you'd rather use Windows, no one's stopping you. We are all familiar here with the discomfort from experiencing our own lack of knowledge for the first time, though.

---

### Post by gamestreamer on 2021-04-02
That is what comes up with mine, "capture 1 & 2".    Yes I can record audio from line in, i just can't hear it before i record.   I have looked through pulse audio and not sure if i have everything set up like i should.  I am guessing there is something missing and i am not seeing it, obliviously lol.

I guess i'm not explaining it very well. When i play music from the phone that is plugged into line in, i hear nothing, but there is signal showing in the meters from line in.  When i hit record, i still hear nothing, until i play back the video / recording, that is when i hear what was playing from the line in.

I will try and put some screenshots of the settings, maybe that will help with what i am seeing.
[ATTACH=CONFIG]288209[/ATTACH][ATTACH=CONFIG]288210[/ATTACH][ATTACH=CONFIG]288211[/ATTACH]


I am actually a network administrator, but i retired early, because 1 i moved back to my home town and not a smart thing to do as not much in the type of work i was looking for. 2 what i could find in regards to computers, they just frustrated me so much, i couldn't handle it. So i decided to retire from computers early.   Going through this whole process, is reminding me why i gave up on them.

if you good at them, thats great. I am finding they are not something i want to do, i know enough to sort of solve my problems, but i can't deal with them on a regular basics.   I pretty much got a expensive piece of paper that is just a paper weight and has put so much stress on me, in trying to pay off the stupid student loans from it.

---

### Post by CatKiller on 2021-04-02
> **gamestreamer said:**
>  When i hit record, i still hear nothing, until i play back the video / recording, that is when i hear what was playing from the line in. 

Every program that records audio will have a setting to let you hear it as you're recording. It won't be enabled by default, because feedback, but it will be there. 

I was wrong earlier, it's actually paprefs rather than pavucontrol that has the tick box for creating monitor streams for if it's not shown by your normal sound settings. It *is* included in KDE's, so it's not something I've particularly had to look for. Otherwise, I think it's "module-loopback" in the PulseAudio settings. 

Also, the JACK connection graph you've made doesn't look right to me. For your use case I think you'd want to just connect your captures to your playbacks directly.

---

### Post by gamestreamer on 2021-04-02
I know every program would allow you to hear as you are recording or such.   I should be able to just hook something up by line in and play it through the computer if wanted. I had no problem in doing so with windows.   It also makes sense you would want to hear what you are recording, to make sure it sounds right and at right levels as your recording.

I don't know where you would find that module-lookback setting.  

I found the paprefs, which i had to install, but everything on it is greyed out and it won't do anything when i click on install in the box.

the JACK connections is what was already set when i click on connect button. I didn't do any changes with it.    When i connect the system capture to the system playback, i get a buzz sound.

I tried going back to windows and i cant atm, so i am stuck with linux.  I got a usb mic that i plugged in and using a bluetooth speaker for the game audio and having it go through the mic.  I know its not an idea setup, but at least i am able to hear the game while recording.  

Hopefully i will be able to figure this whole thing out if possible.

---

### Post by CatKiller on 2021-04-02
> **gamestreamer said:**
> I know every program would allow you to hear as you are recording or such. 

And you haven't turned it on, because...? 

> I don't know where you would find that module-lookback setting.   

It's [module-loopback](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/#module-loopback). And you'd load that module by default by adding it to /etc/pulse/default.pa.

---

### Post by gamestreamer on 2021-04-14
sorry i haven't replied for while.  Been using speaker and mic for audio and recording, so i can hear game audio while i am streaming.  It works, not the best setup, but what else can i do.

I am not understanding about haven't turned it on yet.  That is what i am looking for, to be able to monitor and hear sound from line in before even recording or streaming. I just am not finding or understanding what to look for to do that.
it
I'm not seeing anything about module-loopback. I read where that link took me about modules and it was helpful, but i was completely lost.  Maybe I have reached my level of interest in linux and just want stuff that is simple to click and work.  Makes sense for anything to work.

I even tried putting ubuntu regular verison, one that you get from the ubuntu site. That i could see signal from line in and mic, but it wouldn't let me have separate controls for them. So i switched back to ubuntu studio, so far the studio version seems to be the best option, besides not hearing anything coming from the line in port.

I tried to put windows 10 back on and it works fine, but when i plug the usb cable in, i get a hum from it. I have made a video about that, explaining it best i can about that issue.
I get the hum when i am on windows, but i don't get it when using linux.  [https://www.youtube.com/watch?v=GoIKnH80urE](https://www.youtube.com/watch?v=GoIKnH80urE)

I almost feel like best thing is to go back to linux and use the speaker/mic setup that was the best solution.  Linux is much better for streaming anyways, i just wish i could figure out the sound issue.

---

### Post by gamestreamer on 2021-04-18
I was thinking for anyone to figure out how to solve my issue i am having..... here is what could do

Install a clean installation of Ubuntu Studio LTS and update of course. Connect your phone or other device with cable going into the line in, not the mic, but the line in. Play some music from the device and see if you can hear it through the speakers without recording.  You should be able to plug device into line in and play music without having to do too much.

If you are able to do that, make sure you document your steps and let me know what exactly you did.

I get signal coming through the line in, but nothing comes out of speakers from the line in. 

Good luck and hoping someone would be able to solve this issue.

---

