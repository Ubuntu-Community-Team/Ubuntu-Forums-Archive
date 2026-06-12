---
title: "How can I switch between Jack and Pulseaudio ?"
date: 2013-02-03
forum: General Help
---

### Post by curiousapprentice on 2013-02-03
I need to use jack and pulse audio both working correctly. Some apps require pulse, (example - Radio Tray), & some requires jackd (example - Qsynth).

How can I use both jack and pulse by switching between them.  Switching is the only method by which I can get all apps running. Please help.

I have been searching for past three days for a good solution. Im on Ubuntu 12.04.

---

### Post by mwinthrop on 2013-02-04
Are you using Ubuntu Studio?  If not, that might be what you want to use.  Also, you might want to consider KXStudio and see if that meets your needs.  KXStudio consists of several repositories related to audio that works in Ubuntu Studio.  It is located here: [http://kxstudio.sourceforge.net](http://kxstudio.sourceforge.net)

It has several custom tools for working with audio and runs both Jack and Pulseaudio simultaneously in a seamless way.  You can turn Pulseaudio on and off easily using a tool called "Cadence."

---

### Post by zealibib slaughter on 2013-02-04
do you have pulseaudio jack sink and pulseaudio jack source in qjackctl connections?

---

### Post by curiousapprentice on 2013-02-05
I have QjackCTL and I also installed pulseaudio-module-jack. I switch between sound servers using command line (editing the /etc/pulse/default.pa)

I’m on Ubuntu 12.04 LTS x86 linux (not Ubuntu studio).

---

### Post by zealibib slaughter on 2013-02-05
in your pulse audio volume control when a pulse audio device is initialized and jack is running you get the option to play through jack as long as jack sink is up. 
see attached screenshot i am running qjackctl and connecting firefox flash to jack via jack sink
start jack via qjackctl start playback through an alsa (pulse) client open volume control and go to playback tab. find stream and select jack as playback device.

---

### Post by curiousapprentice on 2013-02-10
@ [zealibib slaughter]("http://ubuntuforums.org/member.php?u=985458"): I thank you for your detailed answer. See, I already know what  you trying to show me through the screen-shot. Im already using jack, using jack sink. But the problem is, how do I switch between them ? (not editing,stopping restarting everything manually). I want some tool which can switch between pulse and jack as per need.  one solution is installing "Cadence". But the rumor is, it can break my ubuntu system.

Can some 1 clarify if installing "Cadence" on normal ubuntu 12.04 desktop works or not ?

---

