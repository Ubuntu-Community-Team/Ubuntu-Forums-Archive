---
title: "No sound after boot Pulseaudio problem"
date: 2021-06-19
forum: General Help
---

### Post by oden99 on 2021-06-19
Hi all.

I have a startup problem where i always have to send "pulseaudio -k" to get my soundcard setup working as it should.
This happens on every reboot or coldboot.

If I understand the command "pulseaudio -k" k stands for "KILL" turning pulseaudio off so it look like there is some kind of conflict when ubuntu 20.04 starts up everything.

First I would like to now and se what steps Ubuntu does at a startup to find this conflict, perhaps move pulseaudio start to a later time in the startup so avoid this conflict..

Yes I can add the pulseaudio command in the upstart manager and it works but it feels like the wrong way to do this sine pulse audio obviously are running but dont work ass planned after a startup..

What files are executed in a normal startup ?

---

### Post by bradleypariah on 2021-06-20
I had something like this problem once.  Not sure if this'll help.  I had two issues:
1. I had an 1/8" cable plugged into the wrong jack.  

I thought I was plugged into Front LR, but it turns out I was in Side LR.  I have a 7.1 card, but I'm only running 5.1 speakers, so all I had was Side, Rear, and Center/Sub plugged in. Pulse kept switching to the HDMI output, because (I think) it only checks Front LR for a load, and if it's not there, it moves on to the next working output. 
If I killed pulse, then force-switched the output with pavucontrol, sound would work, which only delayed me realizing my front two speakers were plugged into the wrong jack.
Once I realized that, I had tons of new self-inflicted issues.  Because I messed with so many software settings while troubleshooting, I found that reinstalling my desktop package brought the sound setting back to normal.  So, in my case 

2. I reinstalled kubuntu-desktop

Sorry if I'm way off base.  I'm not a Linux genius.  Just a stupid user.

---

