---
title: "Problems with audio (I/O stuff)"
date: 2005-04-04
forum: General Help
---

### Post by timelord726 on 2005-04-04
When trying to run Audacity and Muse, I get two errors that seem to indicate the sound server is in use, however I know it isn't right then.  Here are the errors:

**Audacity**: There was an error initializing the audio i/o layer.  You will not be able to play or record audio.  Error: Host error.

**Muse:** MusE failed to find a Jack audio server.  Check that Jack was started.  If Jack was started check that it was started as the same user as MusE.

What's going on?

---

### Post by tenzin on 2005-04-05
same problem for me ...I just started to work with jack ...but muse (and synaddsubfx) doesnt work....on the other side jack works (but with a strange error on the startup*) with: hydrogen and ardour...



*I allways get this from the jack-message window (on startup) :

[SIZE=1][I]13:27:17.284 Statistics reset.
13:27:17.293 Could not open ALSA sequencer as a client. MIDI patchbay will be not available.
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: Datei oder Verzeichnis nicht gefunden
13:27:18.713 Startup script...
13:27:18.713 artsshell -q terminate
13:27:19.006 Startup script terminated with exit status=256.
13:27:19.006 JACK is starting...
13:27:19.007 /usr/bin/jackd -R -doss -r48000 -p1024 -n2 -w16
13:27:19.025 JACK was started with PID=8410 (0x20da).
cannot write to jackstart sync pipe 4 (Bad file descriptor)
jackd: wait for startup process exit failed
jackd 0.99.51
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
oss_driver: /dev/dsp : 0x10/2/48000 (4096)
oss_driver: indevbuf 4096 B, outdevbuf 4096 B
oss_driver: using barrier mode, (dual thread)
13:27:21.238 Server configuration saved to "/root/.jackdrc".
13:27:21.238 Statistics reset.
13:27:21.271 Client activated.
13:27:21.272 Audio connection change.
13:27:21.274 Audio connection graph change.
13:27:22.640 Audio connection graph change.[/I] [/SIZE]

it would be nice if I can use synaddsubfx and muse with jack....

---

### Post by timelord726 on 2005-04-05
My brother's computer is now doing exactly the same thing described in my initial post.  He just upgraded his from Warty to Hoary.  Also, he doesn't have any sound at all... except system sound, or so I assume, because I heard the startup sound at login.  He now tells me that he can't play sound though.

---

### Post by Spainface on 2005-07-31
Audacity works for me now, though I don't know what I did...  Except one thing:  I can record, and play it, but I can't record a second track while listening to the first.  The second track plays like it's in slow motion... really low and distorted.  

Any ideas why?

.e.

---

### Post by keithacole on 2005-08-01
i find that u have to 
"sudo killall esd"

for audacity to start up, and record... 

then u have to sudo esd to again..

its wierd, but i cant get it right, i just wanna record multi tracked audi.. thats it

---

