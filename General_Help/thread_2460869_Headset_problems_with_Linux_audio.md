---
title: "Headset problems with Linux audio"
date: 2021-04-20
forum: General Help
---

### Post by en3rg1zer on 2021-04-20
Hi!

I'm in a bit of a pickle regarding audio in my machine. I'll try explaining it as best as I can.

Around a year ago I started having problems with my audio set up. At the time I was running Windows 10 on an Asus ROG Strix B450-F motherboard, with a Ryzen 2600 CPU. I was also using the HyperX Cloud Stinger Headset (actually, I still am), with a single jack that gets split with an adapter into the motherboard. One day, my friends started complaining that they could hear my OS sounds through Discord. I say "one day" because up until then I had gotten no complains of the sort. Also, as far as I can tell, it was completely sudden. After searching the web with no success I finally managed to cope with the situation by playing with the sound settings and volumes. People could still hear my OS sounds, but I managed to get sufficiently low so that my friends could bear it.

Fast forward a couple of months, my motherboard suddenly died. I know, its weird. I had never had a board die on me like this, but I guess there is always a first. Anyway, I ended up buying a new motherboard (the one I am using right now), which is the MSI Mortar Max with Realtek ALC892/ALC897 Codec. I also installed a UEFI dual boot of Pop_OS! and Windows 10 (this machine was basically supposed to be a "gaming only" machine, but since I am stuck working from home, I thought I might as well install Linux so I can get some work done in the big screen). Also, there was a couple of weeks delay between changing the motherboard (with a fresh install of Windows) and installing Linux. During that period, the old complains seemed to have gotten away.

Now, after installing Linux, the complains returned. Although, I thought, this time I am running an OS where I can actually do some digging! Except, I didn't find much information about this online. Here is what I got so far:

    -> The problem is not with Discord. If I record my audio, I can also hear the applications in the background. Also, there is considerable static noise, especially compared to the volume of my voice.

    -> The problem does not happen only with my headset. If I plug in my girlfriend's headset I get the same result, although the static is not so bad and the OS sounds are lower.
    
    -> If I plug my headset to my laptop - a ThinkPad running Pop_OS! - I can still hear the OS sound in the background, but again, the static isn't so bad and the OS sounds are lower. It's worth mentioning that I have used Discord in my laptop with my headset and got no complains from other people.
    
    -> During my research I read somewhere that the Realtek ALC892/ALC897 Codec is particularly bad. Don't know how accurate this is.
    
    -> Finally, I played around with the settings in pavucontrol with no success. However, I managed to get the situation under control by enabling the echo-cancelation module of pulseaudio.
    
Another thing worth mentioning is that, in Linux, every once in a while (once a day, give or take) something happens and my output sound gets really dirty. The noise is so much that it is unbearable. I can fix this by restarting pulseaudio with "pulseaudio -k". I am also not sure about this, but it appears to be related to the volume. I tend to hear things very loudly and it seems to me that this happens more often if I crank up the volume.

Having said all this, here are my thoughts on the situation:

    -> Maybe it is normal for headset microphones to capture a little bit of the sound coming from the headphones. They are physically connected after all and, since I tend to hear things very loudly, maybe its unavoidable that the microphone captures a little bit of sound.
    
    -> If my above claim is true then maybe this small amount of feedback is usually fixed by some sort of echo-canceling treatment in the drivers.
    
    -> Maybe the low quality of the Realtek codec does not help the situation. Also, the headphones are far from top-quality.
    
Now, I would greatly appreciate any input you have on this subject. I am quite ignorant when it comes to audio processing. Still, my main question at the moment is if buying an external sound card could help with the issue. If so, do you guys have any recommendations of external sound cards to use with Linux?

For anyone still reading, thank so so much for your time! I know the post is quite long, but since I don't have a good grasp on what is going on, I don't really know what information to filter.

Thank you all so much for your time once again!

---

### Post by mastablasta on 2021-04-21
is headset connected via USB or jacks? single or multiple? is speaker sound disabled when you plug in the headset?

i have a 12 EUR Genius headset and i never had this issue. we have realtek, ryzen and such on my kids PC and have no issue. kids use HP Proliant *Gaming *headset with single jack. one has it split with adapter later on, the other one  has single plug on laptop anyway. we tried a couple of chinese headsets from local store and they were rubish. literary fell appart. i even exchanged one and then it's speaker fell off inside and you can hear it rattling. anyway most (if not all) headsets seem to be made in china and plenty are actually quite bad in quality. even one of the HP had to be replaced after 3 months. certain sounds (e.g. lower, base) simply stopped working.

some mics on gaming headsets are really sensitive. how loud is the sound set on headset? mine is usually set to about 20-30 % volume. even that can get a bit too loud, once the ears accommodate.

---

### Post by CelticWarrior on 2021-04-21
> [COLOR=#000000]we tried a couple of chinese headsets from local store and they were rubish.[/COLOR]

FYI, Your Genius headset is as much "chinese" as all the others. Literally all the others, from total rubbish to the best money can buy, all are made in China and now more often than not, also designed and engineered by Chinese companies.
Am I nitpicking? Not really. Given the current climate I have to **take all this veiled soft-racism seriously**, very much so. Please avoid such remarks in the future, thank you.

---

### Post by en3rg1zer on 2021-04-21
I'm sorry. I completely forgot to supply that information. The headset has a single jack that gets split afterwards with an adapter and connected to the motherboard. The problem does not seem to be related to the adapter, since the problem persists when connected to my laptop using only the single jack. I also have no speaker attached to the motherboard. Only the headset. Regarding the volume, I tend to listen to things pretty loudly. My headset nob is set to maximum and the system sound is usually around 60-70%.

---

### Post by annajane on 2021-04-22
> **mastablasta said:**
> is headset connected via USB or jacks? single or multiple? is speaker sound disabled when you plug in the headset?

i have a 12 EUR Genius headset and i never had this issue. we have realtek, ryzen and such on my kids PC and have no issue. kids use HP Proliant *Gaming *headset with single jack. one has it split with adapter later on, the other one  has single plug on laptop anyway. we tried a couple of chinese headsets from local store and they were rubish. literary fell appart. i even exchanged one and then it's speaker fell off inside and you can hear it rattling. anyway most (if not all) headsets seem to be made in china and plenty are actually quite bad in quality. even one of the HP had to be replaced after 3 months. certain sounds (e.g. lower, base) simply stopped working.

some mics on gaming headsets are really sensitive. how loud is the sound set on headset? mine is usually set to about 20-30 % volume. even that can get a bit too loud, once the ears accommodate.

[COLOR=#242729][FONT=Arial]I have a Dell Studio XPS 1647 and headphones do not work (though , internal speakers work like a charm) , I have dual boot Windows 7 and headphones work perfectly fine ...[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I also tried -adding in options snd-hda-intel model=eapd probe_mask=1 position_fix=1.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I've experienced this with Oneric Ocelot and the latest Precise Pangolin (LTS).[/FONT][/COLOR]

---

