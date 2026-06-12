---
title: "problems getting midi to work"
date: 2007-05-14
forum: General Help
---

### Post by darkenemy on 2007-05-14
ok, so i am trying to use a program called guitar pro-run by midi

i have installed:
Bitscope
Jack controol
Jack Eq
Jack Rack
patchage
rosegarden
timidity ++ midi sequencer

all in attempt to get it.
at one point right after i installed timidity, it worked, (however had an EXTREME amount of lag) only to stop right after i restarted.

i need to find a way to get a midi port for this program? 

i have no idea what to do and am getting really lost...
any help would be much appreciated.

---

### Post by christhemonkey on 2007-05-14
Are you running guitar pro in wine?

If so then run winecfg, then under the audio tab, select JACK for sound driver (deselect everything else)

Then start jack from jackcontrol (qjackctl) then start guitar pro with wine, finally go to connections > midi in qjackctl and connect the port for wine to the one for your midi device.

Magic.


Latency issues are normal for running audio apps under wine.

---

### Post by darkenemy on 2007-05-14
i am running it in wine... but when i run winecfg there is no "jack" under audio.  there is alsa, but not jack...

does this mean i didnt set up jack correctly?

furthermore, can this ever be run in linux without lagging? why or why not?

---

### Post by darkenemy on 2007-05-14
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack


this is actually what i get when i try to click the sound tab of winecfg (what appears in teh terminal)

---

### Post by christhemonkey on 2007-05-15
Ah, sorry, i forgot to say that when you use jack with wine, you need to install libjack0.100.0-dev

```
sudo apt-get install libjack0.100.0-dev 
```

The reason is because it is running in a compatibility layer for windows on linux. So native latency wont be possible, you may be able to get acceptable latency, who knows, try it!

---

