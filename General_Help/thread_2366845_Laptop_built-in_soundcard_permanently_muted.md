---
title: "Laptop built-in soundcard permanently muted"
date: 2017-07-22
forum: General Help
---

### Post by dewdrop_world on 2017-07-22
Little problem that I've never seen before.

My laptop has a mute button (Fn-F1). The mute button has an orange light, and the orange light is stuck on. Also, I can't get any sound out of the built-in hardware (but USB audio interfaces are working perfectly).

If I press the Mute key, nothing happens -- the light stays on and I still get no sound.


[LIST]
[*]Built-in soundcard: Input is fine; no errors reported for output, but no sound. (Because input is fine, I think ALSA is connecting to the hardware correctly.) 
[*]USB soundcards: No problems. (I've tried two.) 
[/LIST]

Background info:

I'm using Ubuntu Studio. I've rejiggered the PulseAudio and JACK setup a little bit because the default configuration doesn't work the way I want. I've set PA autospawn=no and I use scripts in qjackctl to launch PA after the JACK server is up. This is because I want PA to route all audio through JACK, always, no exceptions (but the default configuration has JACK using one audio device and PA using a different one), and this is the only way I've found that absolutely reliably does this. Every other approach I've tried works sometimes, but sometimes fails.

When I'm trying the built-in soundcard, I check alsamixer and make sure all the faders are up.

Nothing is muted in pavucontrol -- but this is irrelevant because I can't hear either PA or JACK-native apps through the built-in soundcard.

Again, it appears that everything is working correctly in the software layers -- JACK startup messages show no errors connecting to the soundcard.

ThinkPad Edge E341.

$ uname -a
Linux dlm-E431 4.8.0-58-lowlatency #63~16.04.1-Ubuntu SMP PREEMPT Mon Jun 26 19:54:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

TIA,
James

---

### Post by Autodave on 2017-07-22
Let me start by saying that I have no idea about what you have done so far: I only started playing with Jack yesterday.

So having said that, let me give you an idea to try: and don't laugh: I have fixed MANY laptops by doing this.

  	 	 	 	   1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

---

### Post by dewdrop_world on 2017-07-22
I *will* laugh... and I will also try it later. I think I understand what you're suggesting -- makes sense actually, but I can't do it right this minute.

Thanks,
James

---

### Post by dewdrop_world on 2017-07-23
> **Autodave said:**
> 1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

No dice... I left the battery out (computer unplugged) for about 45 minutes. Same situation.

James

---

### Post by dewdrop_world on 2017-07-26
It's with some embarrassment that I have to report: In fact,  the faders were up in alsamixer, but the channels were also muted (M key). I didn't notice because I had never used "M" before.

That was pretty dumb.

So... never mind. It's working now. Marking solved.

James

---

