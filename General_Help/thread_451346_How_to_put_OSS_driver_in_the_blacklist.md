---
title: "How to put OSS driver in the blacklist"
date: 2007-05-22
forum: General Help
---

### Post by sonnet on 2007-05-22
Hi I have an Esi Maya 44 audio card,and checking on the internet I found this on a mailing list:
""Re: [Alsa-user] ESI maya 44

Frank Barknecht
Thu, 02 Mar 2006 10:06:06 -0800

Hallo,

Zach Visagie hat gesagt: // Zach Visagie wrote:
> I need to get the ESI Maya 44 (not audiotrak, though their very
> similar)

They are the same devices. Really. It's just a different branding.

It should work plug and play if you blacklist the OSS driver (add

"audio" to /etc/hotplug/blacklist) and if you have the snd-usb-audio

driver from ALSA installed.
Ciao
-- 
Frank Barknecht"


So basically there's a guy that suggest to put the OSS driver in the blacklist and check eventually install the the "snd-usb-audio" driver from alsa.The fact is that what this guys write is referred to another  Distro.Does anyone know how to put in the blacklist the OSS driver?
Which line and in which file I should insert?
I checked in the folder /etc/modprobe.d and there are actually the file "blacklist" and "blacklist-oss".What line and in which file should I insert?
How can I check if the "snd-usb-audio" from alsa is installed?

---

### Post by sonnet on 2007-05-22
> **sonnet said:**
> Hi I have an Esi Maya 44 audio card,and checking on the internet I found this on a mailing list:
""Re: [Alsa-user] ESI maya 44

Frank Barknecht
Thu, 02 Mar 2006 10:06:06 -0800

Hallo,

Zach Visagie hat gesagt: // Zach Visagie wrote:
> I need to get the ESI Maya 44 (not audiotrak, though their very
> similar)

They are the same devices. Really. It's just a different branding.

It should work plug and play if you blacklist the OSS driver (add

"audio" to /etc/hotplug/blacklist) and if you have the snd-usb-audio

driver from ALSA installed.
Ciao
-- 
Frank Barknecht"


So basically there's a guy that suggest to put the OSS driver in the blacklist and check eventually install the the "snd-usb-audio" driver from alsa.The fact is that what this guys write is referred to another  Distro.Does anyone know how to put in the blacklist the OSS driver?
Which line and in which file I should insert?
I checked in the folder /etc/modprobe.d and there are actually the file "blacklist" and "blacklist-oss".What line and in which file should I insert?
How can I check if the "snd-usb-audio" from alsa is installed?

none can help?

---

