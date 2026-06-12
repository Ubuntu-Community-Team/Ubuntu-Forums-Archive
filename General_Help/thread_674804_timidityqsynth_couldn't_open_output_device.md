---
title: "timidity/qsynth couldn't open output device"
date: 2008-01-22
forum: General Help
---

### Post by Holonet on 2008-01-22
Timidity is acting very strangely for me.  I installed it earlier, and I didn't have problems.  I was able to use the -ig switch and got the GUI and all.  I was figuring out how to use a soundfont file and I was having trouble with that at first...messing with qsynth and jack...but I think I have that part straightened out now.

Here is what I've done.  I have Jackcontrol for the jack server, I have qsynth open with GeneralCrisisMIDI loaded.  Then I try to use Timidity to play a MIDI file with that soundfont.

In the course of this, I have completely removed all timidity things via synaptic, even did apt-get clean a couple times, and reinstalled it.  For some reason, I can't get it to load the gui, or even play anything now.  I have traced the cause of this to qsynth.  With qsynth running, timidity constantly insists that it cannot open the output device, which I do not understand, to be frank.  Even if I type timidity --help, it says couldn't open the output device.  If I close qsynth, then it does not say that, however it does say that it can't read any configuration file...and I cannot find any configuration file anywhere...even though it's just been installed, just the same as when it once before worked.  Also, if I try timidity -ig, it says "Interface g is not compiled in."  I don't understand how this could be since I just reinstalled timidity and timidity-interfaces-extra.  I'd be most grateful if someone could tell me why timidity is behaving so inconsistently...or possibly just the facets of doing this that I clearly don't understand :).

---

