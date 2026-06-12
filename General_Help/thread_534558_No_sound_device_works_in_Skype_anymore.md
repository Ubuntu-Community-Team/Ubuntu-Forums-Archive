---
title: "No sound device works in Skype anymore"
date: 2007-08-25
forum: General Help
---

### Post by Meroigo on 2007-08-25
Hello people :)

I had set up my Sound Device settings in Skype (1.4.0.74 Beta) correctly so that the sound worked properly. I could do a test call and hear the bot's and my own voice.

I have a 5.1 surround system using a SoundBlaster Live! 5.1 sound card. When I used Windows I could with the Creative Surround Mixer get duplicated stereo in the rear speakers when playing stereo sound. I decided I wanted to do that in Ubuntu too, so I did what's written here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_surround-sound_speakers_.285.1_and_others.29_with_ALSA](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_surround-sound_speakers_.285.1_and_others.29_with_ALSA)

It worked instantly and I was happy! But it made something not to work (I THINK it was)... The sound in Skype. Sound in all other programs work... Whatever sound device I choose there, it doesn't even connect to the test call. It just says "Call failed: problems with audio playback".

I deleted ~/.asoundrc. That didn't change a thing. And the virtual 5.1 sound for stereo files still was there. But I rebooted the computer and the ordinary stero sound was back. But the problem with Skype is still there too.

When I run Skype with the terminal, it doesn't give any hints when there's an error, so I runned Audacity with the terminal. There the microphone and sound works when I have selected "OSS: /dev/dsp", but I can't select that in Skype. So I select "ALSA: SB Live 5.1 (hw;0,1)" (as I do in Skype, and did when it once worked). When I try to start recording, I get an error message in the terminal:

```
Expression 'SetApproximateSampleRate( pcm, hwParams, sr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1108
Expression 'PaAlsaStreamComponent_InitialConfigure( &self->capture, inParams, self->primeBuffers, hwParamsCapture, &realSr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1659
Expression 'PaAlsaStream_Configure( stream, inputParameters, outputParameters, sampleRate, framesPerBuffer, &inputLatency, &outputLatency, &hostBufferSizeMode )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1783
```

What to do? I tried googling and searching these forums but didn't find an answer. And it would be awesome if I could keep the virtual 5.1 sound for stereo sound...

---

### Post by Meroigo on 2007-08-26
How very weird. I didn't seem to have the latest version, so I downloaded the latest version from Skype's homepage. I go to the settings and have sound in as my "SB Live 5.1 (hw:live,0)" and sound out and ringing as "Default device (default)".

I press on "Make a test sound". Yay! Sound! I then press "Make a test call". "Call failed: Problem with Audio Playback"... Then I press "Make a test sound" again, then before the sound has stopped playing I quickly press "Make a test call". Then it connects and it rings! And I can hear the bot and record a message and hear my voice!

This is the only way to make it work. I haven't been called yet so I don't know if I can answer calls, but if I have the Options window open and press "Make a test sound" and then quickly call someone, it seem to work. All my friends are asleep so the once I have tried to call do connect, but they don't answer so I can't check if they hear me. But the bot did, so they should to.

......It's a very very ugly hax to have the option window open and pressing a button there to then quickly press Call on someone to call them (lol). I'd really like to call people normally... Maybe a nice person on this forum could try to help me with it? I sure hope so.. =)

---

### Post by Meroigo on 2007-08-26
I think I've solved it by trying different combinations of what sound devices to use. I use the following and it works:

Sound in: SB Live 5.1 (hw:Live,2)
Sound out: SB Live 5.1 (hw:Live,0)
Ringing: Default device (default)

If you found this thread because you have the same problem, you can try my solution. You probably don't have the same sound card as me, but try to choose the options that looks something like mine; "(hw:Soundcard,X)" being the key to victory.

Funny enough, a sound doesn't play when I press "Make a test sound". But all the sound (login sound, ringing sound etc) works anyway.


....I hope that was all the problems I would have with Skype throughout my whole life. =P

---

### Post by sagara on 2007-08-26
Follow the instructions on this post: [http://ubuntuforums.org/showpost.php?p=1423407&postcount=16](http://ubuntuforums.org/showpost.php?p=1423407&postcount=16)
This fixed it for me!

---

