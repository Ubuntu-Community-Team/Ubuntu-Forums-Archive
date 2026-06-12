---
title: "Help me get sound on linux ( hoary)"
date: 2005-03-22
forum: General Help
---

### Post by ChaperonNoir on 2005-03-22
Hello.

I have no sound on my system !

I don't know why sound does not work. I remember, when i installed the first Ubuntu 64 version, sound was working without any configuration. I reinstalled hoary recently and i have no sound !

Can someone explain me how to get it to work ?

P.S : It's an onboard sound. MB: Chaintech VNF3-250

---

### Post by dusu on 2005-03-22
This might be totally stupid from me, but, did you try to run aumix, and see whether the various volumes are set to non-zero values ?

---

### Post by ChaperonNoir on 2005-03-22
I don't have the command aumix.

But yes, i tried unmuting everything with alsamixer, and with the GUI of alsamixer ( sound control in kde)

Let's say that i start playing a .mp3 file in XMMS, i have the mp3 plugin, i choose alsa as the output plugin. It plays the file... But i have no sound.

---

### Post by cutOff on 2005-03-22
[QUOTE=ChaperonNoir]Hello.

I have no sound on my system !

I don't know why sound does not work. I remember, when i installed the first Ubuntu 64 version, sound was working without any configuration. I reinstalled hoary recently and i have no sound !

Can someone explain me how to get it to work ?

P.S : It's an onboard sound. MB: Chaintech VNF3-250[/QUOTE]
Try to run alsaconf application included on alsa-utils package (if you are using Alsa, of course)


Regards-

---

### Post by ChaperonNoir on 2005-03-22
I tried getting to use alsaconf !

Bash : command not found

However, when i try to install alsa-utils, it says i already have it.

BIZZARE.

---

### Post by cutOff on 2005-03-22
[QUOTE=ChaperonNoir]I don't have the command aumix.

But yes, i tried unmuting everything with alsamixer, and with the GUI of alsamixer ( sound control in kde)

Let's say that i start playing a .mp3 file in XMMS, i have the mp3 plugin, i choose alsa as the output plugin. It plays the file... But i have no sound.[/QUOTE]
Have you installed multimedia codecs??
```
$ sudo apt-get install gstreamer0.8-plugins
$ sudo apt-get install w32codecs
``` 

Regards

---

### Post by ChaperonNoir on 2005-03-22
It's still.. not working  :? 

Card: NVidia CK8S          &#9474;&#9474; Chip: C-Media Electronics CMI9761

---

### Post by ChaperonNoir on 2005-03-22
I started ESD in my terminal.

Then i chose ESD sound in XMMS.

Im looked at this subject for this
[http://www.ubuntuforums.org/showthread.php?t=21079](http://www.ubuntuforums.org/showthread.php?t=21079)

Still no sound

client.c: created 24 "UNIX socket client"
protocol-esound.c: read() failed: EOF
client.c: freed 24 "UNIX socket client"
client.c: created 25 "UNIX socket client"
protocol-esound.c: read() failed: EOF
client.c: freed 25 "UNIX socket client"
client.c: created 26 "UNIX socket client"
protocol-esound.c: read() failed: EOF
client.c: freed 26 "UNIX socket client"

---

### Post by ChaperonNoir on 2005-03-22
I'm using an headset.

My voice was successfuly recorded using Audacity  [-o< 

But i still have no sound .

Someone ?

---

### Post by bored2k on 2005-03-22
[QUOTE=ChaperonNoir]I'm using an headset.

My voice was successfuly recorded using Audacity  [-o< 

But i still have no sound .

Someone ?[/QUOTE]
 This is one of the generic sound solvers [one of many], originally said by someone on this forum -kassetra- a while back to me -worked- :

> 1. Install alsa-oss
2. Install alsa-headers
3. Make sure you have libesd0 and gstreamer0.8-esd installed. (if not, install)
4. Make sure esound and esound-common are installed. (if not, install)
5. alsa-base
6. alsa-utils
7. gstreamer0.8-alsa
8. libpt-plugins-alsa
9. vlc-plugin-esd

Ok, next.
1. Right click on the little volume control in your top panel and the
choose Open volume control.
2a. *IF* it opens, you should see two tabs, one for OSS and the other
for Alsa. Make sure nothing is muted.

We're going to switch you to a sound daemon that allows multiple sounds.
1. In gstreamer-properties, change the Default Sink to output: ESD -
Enlightenment Sound Daemon
2. Change your Output plugin in XMMS to eSound output plugin. 
3. Enable your sound server startup.

---

### Post by oracledarren on 2005-03-22
You need to mute the IE958 Output chanel

---

### Post by ChaperonNoir on 2005-03-22
Thanks goodness it works.

And the sound is great.

Thank you all  :grin:

---

### Post by konfused on 2005-04-13
I just installed the ubuntu hoary, and i have no sound.... 
could someone please give a step by step guide of how you go about intsalling alsa and the various other things needed to get the sound to work?

---

### Post by konfused on 2005-04-13
problem solved

---

### Post by Mellow D on 2005-05-11
I too have a Chaintech VNF3-250, newest BIOS, etc.  But, I cannot get any sound output using OSS/ESD/ALSA/whatever.  Did anyone manage to resolve this problem?  I have already looked in the HOWTO's at the "About Sound in Hoary" and followed the guide there to no avail.  I have also installed the Linux sound drivers from [www.nvidia.com](www.nvidia.com) as the VNF3-250 uses an nForce3 chipset.  Help!

---

