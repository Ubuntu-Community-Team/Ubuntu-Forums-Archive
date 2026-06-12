---
title: "Audio input (mic) comes through choppy"
date: 2021-02-25
forum: General Help
---

### Post by cyberminion on 2021-02-25
Hi folks,

I'm having an issue with a new install of Ubuntu, where the sound input (from a mic) is coming through choppy. It sounds as if my voice is cutting in and out 30+ times per second. I'm mostly understandable, but it also causes a teeth-gritting, almost fingernails-on-chalkboard kind of discomfort when listened to. I don't seem to have any additional drivers listed as available by Ubuntu. I have also tried Mint on this device, and somewhat expectedly had the same basic issue. I am using an Asrock Mobo, which might be the root problem, as I am now aware that Asrock and Linux sometimes don't play well together. I _do_ know that the hardware is functional, since it works fine in Windows. Here are the relevant system specs:

System:
  Kernel: 5.8.0-44-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Gnome 3.36.4 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: ASRock model: B450M Pro4 serial: <filter> 
  UEFI: American Megatrends v: P4.20 date: 07/07/2020 
[B]Audio:
  Device-1: AMD Navi 10 HDMI Audio driver: snd_hda_intel v: kernel 
  bus ID: 09:00.1 
  Device-2: AMD Family 17h HD Audio vendor: ASRock driver: snd_hda_intel 
  v: kernel bus ID: 0b:00.3 
  Sound Server: ALSA v: k5.8.0-44-generic [/B]

Of course, Asrock doesn't offer software support for Linux, but I'd read in another forum that Asrock used RealTek audio hardware, so I tried getting a clean copy of that from their site. (I have no idea if this would even work.) However, after downloading and unzipping the package, I'm...honestly not sure what to do with it. The "Ubuntu Software" application refuses to run it, and attempting to run it manually via CLI just throws errors. (The latter issue might be PEBCAK.)


Does anyone have suggestions as to what I can try? I've used Ubuntu before without major issues, but never really dug deep into it.


Thank you!

---

