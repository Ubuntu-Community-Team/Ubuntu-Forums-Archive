---
title: "Mysterious flickering sound device"
date: 2013-02-01
forum: General Help
---

### Post by rjbrooksjr on 2013-02-01
Hi everyone. Running on a computer that I had initially installed 12.04 on, and have since upgraded to 12.10. Since the upgrade (and not before) I've had a very strange sound problem. Everything works as expected, and I get sound where I expect it. However when listening to music, watching a video, or anything really, there's been this strange/quick feedback/garbage sound that lasts for only second or less. Its very painful with headphones on.

Anyway, I've been dealing with it, never able to figure it out, until yesterday I coincidentally noted that in the sound settings, under output, at the same time the feedback noise happens, a new entry flickers in the output devices only for the length of the noise then disappears. Its way too fast to actually read what it is.

Listed in devices I always have is two items for the HDMI ports, and one for the built in motherboard sound card which is what I'm using. I don't have another sound card in there.. and I have no idea what this mysterious flickering in entry could be. I've tried finding an unexpected entry in alsa mixer, and there's this:

dmesg | grep sound
[    1.419970] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input2
[    1.420044] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input3
[    1.420106] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[    1.420159] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    1.420214] input: HDA Intel PCH Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    1.420276] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    1.420331] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    1.420372] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    1.878579] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[    1.878637] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14


But I really have no idea what to do from here. Any thoughts would be appreciated.

---

### Post by cg40k on 2013-02-01
I have been having a similar problem but only when two or more sound applications are running.

---

### Post by kanikilu on 2013-02-01
I had the exact same problem as you on my Intel HD audio chipset. After foolhardily, and unsuccessfully, trying to compile the drivers myself, I started reading the wiki. From this page:

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

I tried the "position_fix" option described on this page:

[https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

I added "options snd-hda-intel position_fix=1" to my alsa-base.conf file and rebooted, and (fingers-crossed), the horrible distortion sound hasn't re-occurred. This was just yesterday, so we'll see if it holds [-o<

This also coincided with yesterday's kernel update for 12.10 (3.5.0-23), so I don't know what fixed it, but I would guess it was the alsa option since no other kernel updates helped in the past...

---

### Post by rjbrooksjr on 2013-02-01
I'll try that. Staring at it more just now, I was able to read the flickering device. It was "Headphone Output - Built-in Audio"

I have my headphones plugged in the front headphone port on my case..  Yesterday debugging  I also tried unplugging my headphones to see if that made it stop (meaning nothing plugged in because I don't have speakers here at work), but I still saw the flickering device. Something about that port I guess...

---

### Post by kanikilu on 2013-02-01
Mine was also on the front port of my case, using headphones. I have speakers here at work, but don't use them often, but if I remember correctly, I think it did it with those as well. I haven't tested them since setting that option, though...

---

### Post by rjbrooksjr on 2013-02-01
Niether position_fix=1 or position_fix=2 worked. Couldn't try the "Turning off PulseAudio timer scheduling" because it was already off.

Dang.. at this point it might just be worth buying a sound card and disabling this one in the bios.

---

