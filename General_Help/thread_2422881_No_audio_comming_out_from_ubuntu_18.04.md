---
title: "No audio comming out from ubuntu 18.04"
date: 2019-07-14
forum: General Help
---

### Post by stafer601 on 2019-07-14
So i have pulseaudio and this is it's output:
```



E: [pulseaudio] pid.c: Daemon already running.

E: [pulseaudio] main.c: pa_pid_file_create() failed


```
and here are the pavucontrol screeshots:



[LIST]
[*][Playback]("https://i.imgur.com/H5UDPN7.png")


[*][Output_Devices]("https://i.imgur.com/YovP2Zp.png")


[*][Configuration]("https://i.imgur.com/LMZaiIt.png")

[/LIST]
According to pavucontrol the audio should be coming out there's no audio. It's not a hardware issue cause an hour earlier i had windows 10 installed without any probelms. And a week before that i had manjaro, again whitout any audio issues. I've used 18.04 and 16.04 on this machine without any issues.

---

### Post by kesetyan on 2019-07-14
Hi stafer601,

I had a similar problem which I was able to resolve:
My Line-in was recognized in my Ubuntu 18.04 system but I could not get any sound.  Apparently this was because '**Loopback**' was not operating.  The solution for me was as follows:
To initiate Loopback for each individual session, I had to open the terminal and type "**pactl load-module module-loopback**" *(don't include speech marks)* and press the return key.
This worked for me but would be better if I did not need to do this every new session - the answer was to create a script file to load the module automatically each new session and this was carried out as follows:
Open the terminal and type "**sudo sh -c ' echo "load-module module-loopback" >> /etc/pulse/default.pa ' **" and press the return key *(do not include the opening and closing speech marks but do include the single and double speech marks within the text - also include the spaces within the text)*.

This worked for me so I hope it resolves your problem too.

---

### Post by kesetyan on 2019-07-22
Hi stafer601,

Has your sound problem been resolved yet.  My reply was a week ago and it would be interesting to know if the information I provided, which worked for me when I had a similar sounding problem, worked for you.  If it didn't work then the many experts that frequent this forum will be able to provide help, I'm sure, if you respond.

---

