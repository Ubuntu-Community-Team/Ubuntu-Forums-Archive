---
title: "No sound"
date: 2007-10-02
forum: General Help
---

### Post by Madmoose on 2007-10-02
Hello, 

I recently had to cannibalize my computer to save info on my wifes computer. Turns out the mobo and the CPU are both going bad. Anyway, I made working computer out of both our computers. She used to have creative sound blaster live MP3+, but I ended up using my newer sound blaster audigy. All I really did was take my hard drive out, and putting hers in. I thought everything went well in the swtich, but when I got home today my wife asked me why she has no sound. Naturally, I said..."Ummmm :confused: don't know..." 

The first thing I checked was to see if Ubuntu saw the card, and yes it does in the hardware information. Then I looked into sound, and looked to see if the card was selected, and yep it sure was. Then I thought; "Hmmm. Maybe the alsamixer is turned way down." So, I opened up a terminal. Typed in alsamixer, and got:

```
alsamixer: function snd_ctl_open failed for default: No such device
```

Now, I've had issues with this card in the past becouse my hard drive was an Ubuntu only box. That's why I checked everything in order I did, and those fixed my issue. Yet, this is a new thing. I've looked around the posts, but I've yet to see anything about this. 

Any help would be great. 

Ash

---

### Post by overlord.gaurav on 2007-10-02
Maybe your sound card isn't installed properly.
You can try [this guide]("https://help.ubuntu.com/community/SoundTroubleshooting") for installing the sound card drivers.

---

### Post by Madmoose on 2007-10-05
> **overlord.gaurav said:**
> Maybe your sound card isn't installed properly.
You can try [this guide]("https://help.ubuntu.com/community/SoundTroubleshooting") for installing the sound card drivers.

Hey there, 

Thanks for the link, but it didn't work. Did everything down the list. In fact, as of last night the sound on this laptop just stopped working... poof no sound. I've followed that link as well, and everything seems to be in orfer. 

Anyone have any idea why both my computers don't have sound? Was there an update I missed?

Thanks, 

Ash

---

### Post by Quilan on 2007-10-05
Hi Madmoose

If your Audigy is listed and, Alsa is installed ok, can you try this:

Assuming you have Gnome, right click on the Volume Applet and click on Open Volume Control. Click on the Switches tab and make sure Audigy Analog/Digital Output Jack is UNTICKED.

Then System -> Prefs -> Sound and go for a test.

I too have an Audigy and mess around installs and stuff.. sometimes the Distro (and in my experience: Edgy/Fiesty/Gutsy) need a little 'untick' to give the, otherwise OOTB install, a kick start.

HTH

Quil

---

### Post by peabody on 2007-10-05
I had issues in the past with an older Audigy card such that if the digital out was enabled, the analog outputs didn't work.  However, the fact that you can't even get alsamixer to run is potentially a very bad thing.

I run lspci to make sure the card is even being seen (maybe it just went bad)?.  If it shows up in the list, it's time to start playing with modprobe.

---

