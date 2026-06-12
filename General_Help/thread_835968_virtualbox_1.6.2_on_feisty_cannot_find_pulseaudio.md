---
title: "virtualbox 1.6.2 on feisty cannot find pulseaudio"
date: 2008-06-21
forum: General Help
---

### Post by jewishj on 2008-06-21
Hello,

I have been trying to get the sound in a winxp guest in virtualbox 1.6.2 and the sound in the ubuntu feisty host to work simulataneously.  Originally, vbox would produce the following error when trying to boot the guest using ALSA audio..

```

No audio devices could be opened. Selecting the NULL audio backend with the consequence that no sound is audible..

Error ID: HostAudioNotResponding
Severity: Warning

```

Using OSS for the audio source instead would allow the guests sound to work fine, but would prevent the host from using sound at the same time.  I installed pulseaudio and it is working fine in ubuntu, but now OSS produces the above error, and ALSA produces the following error..

```

Some audio devices (PCM_out) could not be opened. Guest applications generating audio output or depending on audio input may hang. Make sure your host audio device is working properly. Check the logfile for error messages of the audio subsystem..

Error ID: HostAudioNotResponding
Severity: Warning

```
 
I was hoping that using PulseAudio as a source would fix this sound issue, but it isn't even an option in the audio driver menu.  Anyone have an idea on how I can get virtualbox to see Pulse Audio as an audio driver?

Thanks so much in advance for any help

---

### Post by jewishj on 2008-06-22
Update... 

I tried installing libao-pulse and modifying libao.conf to use pulse as the default driver.  Now, when I try to use the ALSA driver with virtualbox.. it crashes.  When I use OSS it gives the same result described above.  Everything else still works fine with pulse.

---

