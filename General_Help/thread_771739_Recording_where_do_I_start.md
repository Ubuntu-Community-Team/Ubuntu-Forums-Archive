---
title: "Recording: where do I start?"
date: 2008-04-27
forum: General Help
---

### Post by end-user on 2008-04-27
There are 250+ posts about recording, but nothing seems definitive. I also don't see how I can narrow down the list, my problem seems so general. So I guess I'll post my situation and hope someone knowledgeable has a look.

I feel like I've tried every combination in volume control. Basically at this point, I have every checkbox enabled, every bar up to full. The help files for sound preferences, volume control, and audio recorder haven't really told me what they mean or how they relate to each other.

I don't know what other information to give. I guess I'll start with, I'm using a Gateway 500GR. The front mic & headphone jacks have never worked (under Ubuntu since Feisty), and I've never really tried to get them too. (If that is relevant). I'm trying to use the back mic jack (because the back speaker jack works).

I've put a screenshot on here, it says I have HDA Intel as the first option, among others.

If anyone can tell me what extra program I need to download, or point me to the definitive tutorial, I'd appreciate it. I'm not really in a rush for this, but I'd really like to be able to use Ekiga eventually.

---

### Post by ryanhaigh on 2008-04-27
Here is a good place to start:
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by ryanhaigh on 2008-04-28
Here is a good place to start:
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I always try recording with arecord from the commandline first using each device listed in the output of arecord -l.
> 
arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 2: ALC880 Analog [ALC880 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1


So I would try ```
arecord -D plughw:0,0 -d 20 -vv  dev0.wav
``` and ```
arecord -D plughw:0,1 -d 20 -vv dev1.wav
```. Using -vv should show you amplitude and you can tap the mic to see if it is registered, alternately you can open the wav files to see if anything was recorded.

---

### Post by end-user on 2008-04-28
Thank you. I ended up trying [this post]("http://ubuntuforums.org/showthread.php?t=616845&highlight=Realtek+ALC880"). Now I have my microphone working, as well as the front headphone jack.

I still don't know why there are 3 capture lines, and Digital - there are too many possible combos. But now I have a base line to work off of.

---

### Post by thujoneprophet on 2008-05-19
someone please help. i bought a used gateway nx860s laptop for the sole purpose of recording. it came with vista...yuck! so after trying out a few other open source operating systems settled on ubuntu because it had the recording apps i was looking for. i love using it but i can't get the stock 'sound recorder' program to even work. when i try to record ( after trying many configurations to get the sound working) the program freezes up, turns grey and makes me do a force quit. any ideas on what i need to do? i've been able to figure out how to get all the other sound issues to work but and i've scoured the forum for ideas. the pc does me no good for recording if i can't record.

---

### Post by ryanhaigh on 2008-05-19
Perhaps if all your other sound issues are working you may want to consider using an alternate application to do the recording. Im sure there are plenty of them, as I have indicated I prefer just to use the command line application arecord but there are many alternatives including audacity which is quite simple. The sound recorder in gnome has never worked very well for me although the issue is apparently much improved in Hardy thanks to pulseaudio (Im still on Gutsy so haven't checked for myself).

---

### Post by thujoneprophet on 2008-05-19
well, i have tried the audacity app and i still have the same problem. i figured if i could get the sound recorder to work, audacity would just slip right in. i'm new to linux but am really willing to dig to get out from under the microsoft shadow. my thought is that it's some piece of code that needs to be modified or something but i don't know anything about that.

---

### Post by ryanhaigh on 2008-05-19
Have you tried the troubleshooting guides that were posted earlier in this thread?

---

### Post by thujoneprophet on 2008-05-20
sadly, yes i have tried the troubleshooting guides listed in the post. i don't seem to be making any headway on my problem. i've tried many configurations in the sound options. one thing that i have noticed is that within the sound options preferences the sound capture won't do a test tone on any of the settings. that will lock up on me and i have to end the session from the system monitor. i have also tried a usb adapter with mic input and headphone jack and it shows the option to use that but doesn't do anything different.... i haven't given up on the whole thing i just feel like i'm losing some brain matter on the whole thing:(

---

### Post by ryanhaigh on 2008-05-20
Are you able to record from the commandline using arecord as I posted above?  Note that your card designation will likely be different.

---

