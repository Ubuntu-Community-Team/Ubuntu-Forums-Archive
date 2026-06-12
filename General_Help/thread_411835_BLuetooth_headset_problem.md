---
title: "BLuetooth headset problem"
date: 2007-04-17
forum: General Help
---

### Post by Kuroyume on 2007-04-17
I managed to get my BT headset paired with my computer, but when i try to play sound to it (using XMMS, just to test) all i get is a slight hiss... the progress bar doesn't move at all, and there is no sound...

output:

```
btsco -v 00:16:44:00:D8:AC
btsco v0.42
Device is 2:0
Voice setting: 0x0060
RFCOMM channel 2 connected
Using interface hci0
speaker volume: 12 mic volume: 15
i/o needed: connecting sco...
connected SCO channel
Done setting sco fd
speaker volume: 11 mic volume: 15

```

relevant part of dmesg:

```
[11813.000000] snd-bt-sco revision 1.16 $
[11813.000000] snd-bt-sco: snd-bt-scod thread starting
[11898.832000] snd-bt-sco: playback_open
[11898.832000] snd-bt-sco: prepare ok bps: 16000 size: 8000 count: 800
[11898.852000] snd-bt-sco: playback_trigger 1
[11898.852000] snd-bt-sco: setting playback to bspcm
[11898.860000] Bluetooth: SCO (Voice Link) ver 0.6
[11898.860000] Bluetooth: SCO socket layer initialized
[11933.084000] snd-bt-sco: playback_trigger 0
[11933.084000] snd-bt-sco: setting playback to NULL
[11933.088000] snd-bt-sco: Disposing of previous socket count 3
[11933.088000] snd-bt-sco: file_count is 1 (expected 3)
[12003.508000] ubuntu/media/gspcav1/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
[12003.512000] ohci_hcd 0000:00:0b.0: leak ed f7fac200 (#81) state 2
[12041.636000] snd-bt-sco: playback_open
[12041.636000] snd-bt-sco: prepare ok bps: 16000 size: 8000 count: 800
[12041.656000] snd-bt-sco: playback_trigger 1
[12041.656000] snd-bt-sco: setting playback to bspcm
[12118.400000] snd-bt-sco: playback_trigger 0
[12118.400000] snd-bt-sco: setting playback to NULL
[12118.404000] snd-bt-sco: Disposing of previous socket count 3
[12118.404000] snd-bt-sco: file_count is 1 (expected 3)

```

any ideas? this is the very last of my hardware issues... after this i could proudly say that ALL of my hardware and peripherals work...

thanks in advance...

---

### Post by bwhite82 on 2007-04-17
Have you checked out the wiki?

[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=bluetooth&titlesearch=Titles]("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=bluetooth&titlesearch=Titles")

---

### Post by Kuroyume on 2007-04-17
yup... i got it paired using what says there, but it doesn't say anythng about ny problem or anything like it... i also searched the forums, and can't seem to find anything either...

---

