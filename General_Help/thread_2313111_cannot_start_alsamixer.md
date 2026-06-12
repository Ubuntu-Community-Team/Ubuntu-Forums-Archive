---
title: "cannot start alsamixer"
date: 2016-02-09
forum: General Help
---

### Post by chilliepot on 2016-02-09
Well I installed Ubuntu on a Lenovo T43 and I am trying to get sound to work.

When I type in $ amixer or $ alsamixer, the response is, -   "Mixer attach default error: No such file or directory".

Even though amixer and alsamixer are clearly in the /usr/bin directory.
If I go into the /usr/bin directory and type the same thing I get the same response.

Is this normal? Or should it bring up the mixer controls?

---

### Post by QDR06VV9 on 2016-02-09
Yes it should bring up a mixer window..
Try to use: one at a time though.
```
alsamixer -c 1
alsamixer -c 2
alsamixer -c 3
```
And if none of those work post back the content of this in the terminal
```
/sbin/lsmod | grep snd

```
This should give us a good start in helping you out.

---

### Post by chilliepot on 2016-02-10
Thanks for that.

The first three give a response of "Invalid card index"

The next: 
snd_intel8x0           36864  2
snd_ac97_codec        106496  1 snd_intel8x0
ac97_bus               16384  1 snd_ac97_codec
snd_pcm                90112  2 snd_ac97_codec,snd_intel8x0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            28672  1 snd_seq_midi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    69632  12 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,thinkpad_acpi,snd_seq_device
soundcore              16384  1 snd



[COLOR=#000000][FONT=Arial][/FONT][/COLOR]

---

### Post by QDR06VV9 on 2016-02-10
Well it looks like we roll up our sleeve's and dig in here.
Will you post back the output of this from the terminal.
```
aplay -l
```
Is this a fresh install?
And also what version of Ubuntu are you using? IE: (14.04 or 15.10)
If you are unsure put this in the terminal:
```
lsb_release -a
```

---

