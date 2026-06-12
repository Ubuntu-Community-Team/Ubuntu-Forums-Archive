---
title: "Timidity CPU usage problem"
date: 2005-05-08
forum: General Help
---

### Post by fishfork on 2005-05-08
I'm trying to configure a soft synth for MIDI playback. I've installed Timidity and the soundfont Unison.SF2. Now my machine's fairly old (AMD K6-II, 400 Mhz). At first the CPU usage was really high, but I changed some options in timidity.cfg, which I've added to the wiki [here](http://www.ubuntulinux.org/wiki/MidiSoftwareSynthesisHowTo) if you're interested. So now the CPU usage is around/less than 25% when I play a midi file like this:

timidity somesong.mid

So next I ran it as a midi server:

timidity -iA

Then I try to play a midi file with pmidi or kmid. It all works fine, until, at a seemingly random moment, the sound will stop and timidity will start hogging 100% of the CPU. If I wait for a few seconds, sometimes I get the odd random note, and occasionally the music will start again and it will go back to normal. Generally it starts doing it again, though. When I press ctrl-C to quit pmidi, I get a splurge of notes at once, and then the CPU usage goes back to normal.

Any ideas at all?

---

### Post by fishfork on 2005-05-11
Update: I tried running Timidity from the /etc/init.d script as I put in the wiki, and the problem's gone away. Still not sure what was causing it though. At least the sound works in rosegarden now :)

---

### Post by alainhenry on 2005-05-22
Thanks for updating the wiki page [https://www.ubuntulinux.org/wiki/MidiSoftwareSynthesisHowTo](https://www.ubuntulinux.org/wiki/MidiSoftwareSynthesisHowTo)
on software synthesis.  Having the midi server start at boot is great, thanks for adding that.  Still, I have not yet managed to have timidity working as a midiserver yet. 
=== NOW YES, but read on

I have two questions:  

1) I installed flac and freepats.  
The command "timidity -iA" gets the following error message:
   /dev/dsp: Device or resource busy
   couldn't open output device
=== CORRECTION: this is the message I get when launching this as root, but it works fine from my user login.  
===


2) Trying to use the command described in the wiki:
timidity -iA -B2,8 -Os1l -s 44100
gets the message: 
   can't open pcm device 'default'.
   Couldn't open ALSA pcm device ('s')

Any suggestion welcome
=== CORRECTION: it works with the simple command "timidity -iA" from my login, but I'm still curious about why the above commands do not work


Alain

---

### Post by alainhenry on 2005-05-22
I also tried setting up timidity to launch from /etc/default/init.d.  I included the seq-snd-... modules in /etc/modules and uncommented the line TIM_ALSASEQ=true in /etc/default/timidity
It all seem to work, but there is no sound.  
I checked alsamixer, but there is no obvious modification to do.

Any idea? It shoudl work ,because launching timidity -iA from the command line works fine.  


Alain

---

### Post by fishfork on 2005-05-22
[QUOTE=alainhenry]
The command "timidity -iA" gets the following error message:
   /dev/dsp: Device or resource busy
   couldn't open output device
=== CORRECTION: this is the message I get when launching this as root, but it works fine from my user login.  
===
[/QUOTE]

That seems to be a strange error. Isn't /dev/dsp an OSS device, not the ALSA one?
I don't see why it's working as an ordinary user, but not as root either. Try 'sudo lsof /dev/dsp' to see what's using the device. You could try 'killall esd' to stop esd if it's running too.

---

