---
title: "Rosegarden is full of thorns"
date: 2005-04-04
forum: General Help
---

### Post by nicholaspaul on 2005-04-04
Oh dear oh dear.. what does this error mean? The Rosegarden splash doesnt disappear... Do I need to install other libraries or something? 

nicholas@ubuntutu:~ $ rosegarden4
Link points to "/tmp/ksocket-nicholas"
Link points to "/tmp/kde-nicholas"
kbuildsycoca running...
rosegarden: main: Showing startup logo
JACK compiled with System V SHM support
nicholas@ubuntutu:~ $ rosegarden (sequencer): SequencerMmapper : setting size of /tmp/kde-nicholas//rosegarden_sequencer_timing_block to 91012
rosegarden (sequencer): SequencerMmapper : mmap size : 91012 at 0xb6472000
rosegarden (sequencer): SequencerMmapper::init()
rosegarden (sequencer): Registering with DCOP server
Rosegarden 0.9.9 - AlsaDriver - alsa-lib version 1.0.5

JackDriver::initialiseAudio - JACK server not running
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevi...etc.
(this last line keeps repeating)

How do i run jack? I've tried installing everything that looks like alsa from synaptic.

---

### Post by ember on 2005-04-04
You can start JACK manually by jackd -hw:0 -r:44100 -d:alsa, if I remember correctly, yet I would advise you to use QJackCtl which is very comfortable.

---

### Post by nicholaspaul on 2005-04-04
This is what I tried (after stabbing various commands at it) -
_______________________________________________
nicholas@ubuntutu:~ $ jackd -d alsa
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
Couldn't open hw:0 for 32bit samples trying 24bit instead
Couldn't open hw:0 for 24bit samples trying 16bit instead
Couldn't open hw:0 for 32bit samples trying 24bit instead
Couldn't open hw:0 for 24bit samples trying 16bit instead
_______________________________________________
and there it just waits... and waits...

---

### Post by nicholaspaul on 2005-04-08
OK, I installed QJackCtl, and I'm very impressed! But I get an error, saying hw:0 is busy  and that I have to close that app first. i dont have anything else running (That I know of ).. what could it be? I tried other hw settings , but they seem to be unopenable. 
Is there someplace I can list my hw devices?

---

### Post by JasonField on 2005-04-08
I had a similar problem and found the following thread...

[http://www.mail-archive.com/alsa-devel@lists.sourceforge.net/msg08883.html](http://www.mail-archive.com/alsa-devel@lists.sourceforge.net/msg08883.html)

The long and short of it is that after running

sudo modprobe snd-seq

I could then run

rosegarden4

and it all starts up fine. I also think that you need to use sudo when you run qjackctl to get it all to run proeperly (although I'm not 100% on that :) )

HTH,

J

---

### Post by nicholaspaul on 2005-04-08
Do you get audio too? My audio is still 'grey out' (and under System Config, it says Audio No)

---

### Post by bobmitch on 2005-04-08
Could it be that jack is already running?

Do a **ps -ef | grep -i "jack" | grep -v "grep"**.  If anything is returned, jack is already running. (I think the process is called 'jackd' but using jack in the grep will catch it...

---

### Post by nicholaspaul on 2005-04-08
Is it running? I dunnol! I get this :

[SIZE=1]root      9871     1  0 Apr06 ?        00:02:56 /usr/bin/jackd -d alsa -d hw -r 44100 -p 2048 -n 2[/SIZE]

If that means its running with a sample rate of 44.1 id like to change that :D
Can i stop it and restart with QJackCtl ?

---

