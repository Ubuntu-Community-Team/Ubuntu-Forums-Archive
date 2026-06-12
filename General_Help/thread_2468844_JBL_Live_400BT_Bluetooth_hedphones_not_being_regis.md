---
title: "JBL Live 400BT Bluetooth hedphones not being registered as a PulseAudio sink - 21.10"
date: 2021-11-11
forum: General Help
---

### Post by agvantibo on 2021-11-11
I'm using vanilla Ubuntu 21.10 upgraded from 21.04, and after the  upgrade my headphones (JBL Live 400BT) refused to become a PulseAudio  sink. They still connect via Bluetooth, still are determined to be an  external BT headset by the Settings app, but they are not available as  an output sink anywhere. I restarted the bluez and pulseaudio daemons,  rebooted the system, even reinstalled the packages - but to no avail.

One workaround is using PipeWire instead of PA, as described [here]("https://ubuntuhandbook.org/index.php/2021/05/enable-pipewire-audio-service-ubuntu-21-04/").  When I followed the tutorial to replace Pulse with Pipe completely, the  issue vanished. Also, options appeared to choose more BT audio codecs, which is great,  but the main downside is, under _REALLY_ heavy CPU load (~90%-100%) PipeWire  throws in some really weird artifacts that make online video calls via  Zoom an utterly nightmarish experience.

So I'm currently stuck  with either Pulse and no headphones, or Pipe and irregular artifacts.  Thankfully, the aforementioned artifacts have not been sighted after a  recent update, so Pipe might be a viable solution.

Does anyone  know any fixes for Pulseaudio that might help? 
Is replacing PulseAudio  like that a safe process? I've found this to be easily reversible with `ppa-purge` and a couple of `systemctl`s, but maybe that broke somehting?

---

