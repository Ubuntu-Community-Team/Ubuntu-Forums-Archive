---
title: "Webcam microphone is faster and high-pitched"
date: 2018-07-19
forum: General Help
---

### Post by thewolf3 on 2018-07-19
Hi,

So I am entirely new to Linux and have recently installed it. So far, everything is ok, except for the microphone of my webcam (Philips SPZ 3000).

Basically, if I record any audio through it (audacity, discord,...) it is faster (meaning 5s plays in 2s) and a lot higher pitched.

Things I have tried:
- I checked for updates and drivers and installed everything.
- Checked Philips' website and found only drivers for Windows.
- Tried playing with the dials in alsamixer, no luck.
- I installed pavucontrol but still couldn't figure out the solution while playing with the dials.
- I tried changing the sample rate in Audacity and it does change the sound although it is far from normal.
- I tried fiddling with the pulseaudio daemon.conf (option: default-sample-rate) and changing the rate there while killing and restarting pulseaudio, but still no luck.
- I looked around the internet and it seems that this was a known issue with Logitech webcams in 2010/11 era, so basically every post is old and most of them are fixed either by changing the sample rate in daemon or by a kernel patch.

I'm on Bionic Beaver 64bit.
The webcam: Philips SPZ-3000

Does someone more experienced have any ideas?

Thanks in advance?

---

### Post by thewolf3 on 2018-07-21
So, I have managed to solve the issue.
Here's what I did.
1. Make sure that you updated everything that you can and than try restarting you PC a couple of times.
2. After the first step, Ubuntu suddenly started recognizing my camera mic as an actual camera mic and not just "input" (judging by the label).
3. Play with your pulse audio setting - precisely the sampling rate. Here are a few tips.
    -If your voice is faster and high pitched the frequency is too high, reduce it, I found that 16000Hz works fine for my mic.
    -For checking use a basic mic recorder from the appstore (do not use Audacity as it has it's own sampling rate and usually doesn't use the default one, use something simple)
    -After you save the changes to the file, ALWAYS restart the service
        -sudo nano /etc/.pulse/daemon.conf (edit the file, save with ctrl+x and then enter)
        -sudo pulseaudio -k
        -sudo pulseaudio --start

Hope it helps someone.

Best regards

---

