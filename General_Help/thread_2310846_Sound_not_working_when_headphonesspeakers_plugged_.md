---
title: "Sound not working when headphones/speakers plugged in"
date: 2016-01-22
forum: General Help
---

### Post by sonar2 on 2016-01-22
Hello dear people,
having a noobish problem - when i plug something into the audio jack the sound dissapears. I am running ubuntu 14.04 LTS on a Asus Intel® Pentium(R) CPU N3530 @ 2.16GHz × 4. I have a dual OS.
I saw some other topics, so i know this link is needed -  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

hope u can help me out

When I bring alsamixer in the terminal and plug in the headphones, the speaker volume goes automaticlly to 0, if I unplug it goes back to normal. While plugged, even if i change manually the volume, nothing changes.

---

### Post by grahammechanical on 2016-01-22
I think that you will need to go into sound settings and switch the audio output from internal audio to headphones. I do not know if this applies to 14.04 but in 15.10 onwards headphone output will appear in sound settings once we plug a set of headphones into the headphone socket. Then we can select headphones as the audio output.

Unless, you are plugging the headphones into the line-out socket.

Regards.

---

### Post by sonar2 on 2016-01-22
> **grahammechanical said:**
> I think that you will need to go into sound settings and switch the audio output from internal audio to headphones. I do not know if this applies to 14.04 but in 15.10 onwards headphone output will appear in sound settings once we plug a set of headphones into the headphone socket. Then we can select headphones as the audio output.

Unless, you are plugging the headphones into the line-out socket.

Regards.

Nah, it changes automaticly to headphones as output, the system knows there is something plugged in, the volume is shown to be up just no freaking sound coming out.

---

### Post by Yellow Pasque on 2016-01-22
You gave a link to the script instead of a link to your actual info. Try it again.

---

### Post by sonar2 on 2016-01-23
> **Temüjin said:**
> You gave a link to the script instead of a link to your actual info. Try it again.

Hmmm... is this it then? : [http://www.alsa-project.org/db/?f=635ebd362ed7b9b67c5806ba7aaa2091121b358f](http://www.alsa-project.org/db/?f=635ebd362ed7b9b67c5806ba7aaa2091121b358f)

Aah, please you guys, help me out, got nobody i can ask and got nothing i can do on my own, dont want to give up on ubuntu cause of this little inconvenience

---

### Post by Yellow Pasque on 2016-01-23
Yes, that's the correct link. Did you add this line before or after the problem started?
```
snd_hda_intel: model=asus
```
If it did not help, then get rid of it. I don't even think 'asus' is a valid model keyword for ALC269/270 codec.

Some things I'd suggest:
1. Try disabling auto-mute (use spacebar to toggle in alsamixer). Sound will still come out of the speakers when you plug in headphones, but it will be interesting to see if it fixes no sound condition.
2. If possible, try a LiveUSB of a more current version of Ubuntu to see if the problem got fixed. There's no sense troubleshooting a problem that's already been fixed. You can use a 16.04 daily build ( [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) ) or a 15.10 image if you don't want to use a daily build. Remember, you're not installing it; you're just looking to see if the issue still occurs in the Live environment.

> Aah, please you guys, help me out, got nobody i can ask and got nothing i can do on my own, dont want to give up on ubuntu cause of this little inconvenience 

It was less than 10 hours since your last post. Please don't bump your thread more than once a day (forum policy).

---

### Post by sonar2 on 2016-01-24
> **Temüjin said:**
> Yes, that's the correct link. Did you add this line before or after the problem started?
```
snd_hda_intel: model=asus
```
If it did not help, then get rid of it. I don't even think 'asus' is a valid model keyword for ALC269/270 codec.

Some things I'd suggest:
1. Try disabling auto-mute (use spacebar to toggle in alsamixer). Sound will still come out of the speakers when you plug in headphones, but it will be interesting to see if it fixes no sound condition.
2. If possible, try a LiveUSB of a more current version of Ubuntu to see if the problem got fixed. There's no sense troubleshooting a problem that's already been fixed. You can use a 16.04 daily build ( [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) ) or a 15.10 image if you don't want to use a daily build. Remember, you're not installing it; you're just looking to see if the issue still occurs in the Live environment.



It was less than 10 hours since your last post. Please don't bump your thread more than once a day (forum policy).

Yes, sorry about that, wont happen again. 
So I disabled the auto-mute in alsamixer and nothing change and the sound from the internal speakers disappeared.
I dont know if i mentioned before, but this is something that just happened one day, without me changing/touching nothing on the system. It has always worked with no problems before.
When I use windows and i plug something in, a window from the sound manager appears asking me to accept the hardware and it gives me the possibily to change some details of the sound and stuff, so i need to click ok before the plugged hardware be accepted and used. One day this thing didnt pop up, i switched to Ubuntu and the sound wasnt coming from the plugged stuff anymore. Is there any possibility that it is just some random glitch that got transfered from one OS to the other? Sorry if this is a complete idiotic question, it is just the feeling i get.
I will try the LiveUsb thing, it basicly means to start my computer with the OS from the key, right? and check if the headphones work.

Thanks

---

### Post by Vladlenin5000 on 2016-01-24
> **sonar2 said:**
> When I use windows and i plug something in, a window from the sound manager appears asking me to accept the hardware and it gives me the possibily to change some details of the sound and stuff, so i need to click ok before the plugged hardware be accepted and used. One day this thing didnt pop up, i switched to Ubuntu and the sound wasnt coming from the plugged stuff anymore. Is there any possibility that it is just some random glitch that got transfered from one OS to the other? Sorry if this is a complete idiotic question, it is just the feeling i get.


No, the question isn't idiotic, there are no idiotic questions... But there are flawed logic and yours above is one example among so may I've found here and elsewhere.
No, glitches aren't and can't be transfered from one OS to another.
In your case, sound logic (pun intended) tells us it's an **hardware failure**. You're wasting your time troubleshooting software. Contact your tech support if still in warranty or any other service if not. Keep in mind repairing such problems in a notebook is often very expensive. Alternatively you can use a cheap USB sound card if you really need the headphones port.

> I will try the LiveUsb thing, it basicly means to start my computer with  the OS from the key, right? and check if the headphones work.

Yes, and please do that just in case but I bet it'll be the same.

---

### Post by sonar2 on 2016-01-24
[QUOTE=Vladlenin5000;13428151]No, the question isn't idiotic, there are no idiotic questions... But there are flawed logic and yours above is one example among so may I've found here and elsewhere.
No, glitches aren't and can't be transfered from one OS to another.
In your case, sound logic (pun intended) tells us it's an **hardware failure**. You're wasting your time troubleshooting software. Contact your tech support if still in warranty or any other service if not. Keep in mind repairing such problems in a notebook is often very expensive. Alternatively you can use a cheap USB sound card if you really need the headphones port.



Yes, and please do that just in case but I bet it'll be the same.[/QUOT

Everything works fine in Windows, so how can it be a hardware problem?

---

### Post by Vladlenin5000 on 2016-01-24
So now it works again in Windows?

Quoting again > One day this thing didnt pop up (...)

---

### Post by Yellow Pasque on 2016-01-24
> **sonar2 said:**
> I dont know if i mentioned before, but this is something that just happened one day, without me changing/touching nothing on the system. It has always worked with no problems before.
No, I don't think you mentioned that. In that case, one quick/easy thing you can try is deleting pulseaudio's user configuration so that it regenerates fresh config files:
```
rm -rf ~/.config/pulse*
pulseaudio -k
```
One other possibility would be try to an older kernel that you still have installed on the system. Maybe you installed a kernel upgrade the last time you had it working and didn't notice it not working until you booted into the new kernel (i.e. there was a bug/regression introduced by a kernel update).

> When I use windows and i plug something in, a window from the sound manager appears asking me to accept the hardware and it gives me the possibily to change some details of the sound and stuff, so i need to click ok before the plugged hardware be accepted and used. One day this thing didnt pop up, i switched to Ubuntu and the sound wasnt coming from the plugged stuff anymore.

I think you're talking about the Realtek sound manager. That doesn't have any affect on other OS's.

> Is there any possibility that it is just some random glitch that got transfered from one OS to the other?

I've seen some sound issues occur when booting directly from Windows into Linux because Windows would leave the codec in an odd state and the BIOS didn't completely reset it. Of course, the system would be fine if doing a cold boot into Linux though.

> I will try the LiveUsb thing, it basically means to start my computer with the OS from the key, right? and check if the headphones work.
Yes

---

