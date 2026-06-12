---
title: "Problem with Jack and 4 Channel USB Audio"
date: 2007-09-25
forum: General Help
---

### Post by BobboProfondo on 2007-09-25
Hello All

I'm having a bit of a problem with my Tascam US-428 USB audio interface. When I try to open Rosegarden, or patch Audacity or Ardour in Jack the Jack server stops. Every time. 

Long story (fairly) short: 
So far I've managed to set everything up to record on two channels through Jack and have had good results using Rosegarden and Audacity. 

I posted a question about how to get all 4 channels working, and got a very helpful response that mentioned the nr_packs=1 option for the snd_usb_usx2y module. 

I may be doing something daft here, but the steps I follow are...

```
sudo modprobe snd_usb_usx2y nrpacks=1 (and password)Plug in the US-428

usx2yloader

us428control &
```

Once I've run these, start Jack Control, and choose 'hw:1,2' as my interface (which says 'US-X2Y hwdep Audio' next to it.)

Start the Jack server, and the four inputs are there in the connections list. Yippee! 

Then, however, when I start Rosegarden, or try to connect Audacity or Meterbridge, Jack stops and when I was first trying this I got loads of messages about Broken Pipes. (Googling for broken pipes and jack seems to just bring up a long list of plumbers called Jack!)

On trying to replicate this again the following day (probably with different settings) I got the following, but the result is just the same, Jack stops. 

```
11:04:34.051 MIDI connection graph change.
11:04:37.688 Startup script...
11:04:37.692 artsshell -q terminate
11:04:38.001 Startup script terminated with exit status=256.
11:04:38.004 JACK is starting...
11:04:38.007 /usr/bin/jackd -v -R -dalsa -dhw:1,2 -r44100 -p256 -n8
11:04:38.028 JACK was started with PID=6599 (0x19c7).
11:04:40.129 Server configuration saved to "/home/bob/.jackdrc".
11:04:40.133 Statistics reset.
11:04:40.158 Client activated.
11:04:40.174 Audio connection change.
11:04:40.207 Audio connection graph change.
11:04:53.157 Audio connection graph change.
11:04:53.860 Audio connection graph change.
11:04:53.899 Audio connection change.
11:04:53.999 Audio connection graph change.
11:04:54.027 MIDI connection graph change.
11:04:56.259 MIDI connection change.
11:04:56.263 Shutdown notification.
11:04:56.266 Client deactivated.
11:04:56.274 JACK was stopped successfully.
11:04:56.275 Post-shutdown script...
11:04:56.276 killall jackd
11:04:56.297 MIDI connection graph change.
11:04:56.961 MIDI connection change.
11:04:56.972 Post-shutdown script terminated with exit status=256.
11:04:57.713 MIDI connection graph change.
```

Any light anyone can shed on this would be much appreciated. 

Cheers
Bob

---

