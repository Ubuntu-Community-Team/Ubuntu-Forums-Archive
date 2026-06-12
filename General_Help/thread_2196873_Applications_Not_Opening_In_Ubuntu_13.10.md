---
title: "Applications Not Opening In Ubuntu 13.10"
date: 2013-12-31
forum: General Help
---

### Post by shabalabadingdong on 2013-12-31
I have recently just upgraded from 13.04 to 13.10 and some apps like GIMP, Audacity, Synaptic, LibreOffice, and many more are not opening when I click the app icon pulses but doesn't open.  By the way my computer is a Dell XPS 420 and it's graphics card is too old and doesn't have a proprietary driver (ATI Radeon HD 3650) recently I thought I fixed it by typing in the terminal: sudo apt-get install flgrx, but it booted the computer in low graphics mode and when I clicked to boot in this mode for one session it didn't boot up at all.  So I went into recovery mode and root and typed in sudo apt-get remove flgrx and sudo reboot to reboot and it fixed the problem...but the apps not opening still occurs.


-Any help, tip, or fix is greatly appreciated!

---

### Post by deadflowr on 2014-01-01
What happens when you try typing one of the apps name in a terminal, to try to run it?
Example:  gimp. (Just type it like that, simply gimp, no uppercase or anything else)
Does it launch, or does it produce errors and stuff like that.
If it errors post the errors in this thread.

---

### Post by shabalabadingdong on 2014-01-01
It does nothing.

---

### Post by deadflowr on 2014-01-01
> **shabalabadingdong said:**
> It does nothing.
What happened?
Or rather, what did you try?

---

### Post by ajgreeny on 2014-01-01
Have you actually installed gimp? It doesn't come by default, or didn't in some versions; not sure about 13.10.

---

### Post by shabalabadingdong on 2014-01-01
Okay this is what I get when I type it in the terminal when I try to open Audacity.


ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:961:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4541
Expression 'ret' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1670
Expression 'AlsaOpen( &alsaApi->baseHostApiRep, params, streamDir, &self->pcm )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1830
Expression 'PaAlsaStreamComponent_Initialize( &self->capture, alsaApi, inParams, StreamDirection_In, NULL != callback )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2092
Expression 'PaAlsaStream_Initialize( stream, alsaHostApi, inputParameters, outputParameters, sampleRate, framesPerBuffer, callback, streamFlags, userData )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2764
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4541
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4541
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4541

By the way that image below where it shows audacity open I don't see at at all when I try to open it, and that is just pure weird.

---

