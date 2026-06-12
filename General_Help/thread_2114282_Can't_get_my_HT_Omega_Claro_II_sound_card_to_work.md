---
title: "Can't get my HT Omega Claro II sound card to work"
date: 2013-02-09
forum: General Help
---

### Post by Sugetsu on 2013-02-09
Hello, I am new to the forums. I am a major noob when it comes to linux so please bear with me. The following is a compilation of everything I have tried to do in order to get the sound card working: [http://www.htomega.com/claro2.html](http://www.htomega.com/claro2.html)

I just installed Ubuntu 64bit 12.04 precise and I can't get my sound card to be recognized by the system. After countless hours googling for solutions I have arrived at a dead end.

At one point I was even able to enable HDMI audio by following the command:
sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily
sudo apt-get update
sudo apt-get install alsa-hda-dkmsToo bad my monitor doesn't have speakers. This has been one frustrating experience.... No matter what I do I cant the following to change:

lshw:
*-multimedia:0 UNCLAIMED
                description: Multimedia audio controller
                product: CMI8788 [Oxygen HD Audio]
                vendor: C-Media Electronics Inc
                physical id: 6
                bus info: pci@0000:04:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 maxlatency=24 mingnt=2
                resources: ioport:e800(size=256)

An old post in this forums seems to indicate that someone was able to solve the issue by adding the device module to /etc/modules: [http://ubuntuforums.org/showpost.php?p=10328968&postcount=3](http://ubuntuforums.org/showpost.php?p=10328968&postcount=3) ... but of course I haven't the faintest idea on how to do such a thing...

Finally... I was able to upgrade my Alsa drivers from 1.0.24 to 1.0.25 by following the script instructions found here: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577) but still nothing... at least this was a significant step in my quest to solve this issue.

In an act of desperation, I turned to the following sound troubleshoot guide:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure). Based on this guide I was instructed to post the output of this diagnostics command: wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && chmod +x ./alsa-info.sh && ./alsa-info.sh. 

Here it is: [http://www.alsa-project.org/db/?f=2809917cb48d4422d536fd1d0946d37782f0ed81](http://www.alsa-project.org/db/?f=2809917cb48d4422d536fd1d0946d37782f0ed81)

Can someone here please help me? All I see in the Pulse audio volume control is the Dummy output. =(

Thank you in advance!!!

---

### Post by Sugetsu on 2013-02-09
Update

I decided to upgrade my kernel to the newest stable version following this guide: 
[http://ubuntuforums.org/showthread.php?t=1872537](http://ubuntuforums.org/showthread.php?t=1872537), the system now recognises HDMI audio but my sound card remains UNCLAIMED. Again, my monitor doesn't have speakers.

Could it be that I need to add my sound card's modules to /etc/modules like old post I posted suggested? I have no idea how to do such a thing!

Please help =(

---

### Post by Sugetsu on 2013-02-09
Bump...

---

### Post by lisati on 2013-02-09
This thread is a duplicate of [http://ubuntuforums.org/showthread.php?t=2114306](http://ubuntuforums.org/showthread.php?t=2114306)

One thread for a particular support request is sufficient.

Thread closed.

---

