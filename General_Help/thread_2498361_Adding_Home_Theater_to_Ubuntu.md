---
title: "Adding Home Theater to Ubuntu"
date: 2024-06-10
forum: General Help
---

### Post by pilotone on 2024-06-10
[COLOR=#000000][FONT=Verdana]Hi, [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I currently have a smart tv (not connected to internet), a win 8 computer and a Morantz receiver.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I want to desperately scrap the win 8 for Bodhi.  The tv is using an HDMI connection to the receiver and the receiver to the PC. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Does anyone have any experience connecting a receiver to Ubuntu? [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Can the usual Pulseaudo, blueman and bluez work passing through the PC to the Morantz?[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I'm trying to get all my ducks in a row before I start the conversion.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Thanks[/FONT][/COLOR]

---

### Post by TheFu on 2024-06-10
I use an Ubuntu Server to run Jellyfin, then use RaspberryPi v2/v3/v4 devices running OSMC at the receiver location to drive audio and our projectors.  Because of my receiver (Onkyo and Kenwood), I split off the audio from the HDMI output to a TosLink for the audio receivers.  

I don't have any 4K resolution output, which I understand will cause issues with HDCP from any stock Linux system, so a commercial player - like the Vero V [https://osmc.tv/vero/](https://osmc.tv/vero/)  - with proprietary HDMI code is needed to output 4K thanks to the HDMI/HDCP standards "committee" aka cartel never approving any F/LOSS software for that purpose.  If course, if you don't haven't any HDCP content, then 4K output shouldn't be a problem.

Additionally, the audio signals can be passed through from the source files to the receiver, so it will need to decode any specialized audio codecs like Atmos or DD+.  My receivers don't have any of that, so I just force 5.1 PCM through the TosLink.

I would never use bluetooth for anything on purpose.  Last time my computer was hacked, it was because I forgot to disable Bluetooth and remove the drivers. I don't need that to happen, yet again.

---

### Post by pilotone on 2024-06-11
Thanks for the reply. I'll look into what you are doing.  
I don't bluetooth either. I tried it once and couldn't jack the volume up high enough for any real sound.

---

### Post by TheFu on 2024-06-11
If you don't need/want bluetooth, you don't need blueman  or  bluez.  Seems that will remove 2/3rd of the problems.

---

### Post by pilotone on 2024-06-11
Wow I didn't realize that.  Thanks no bluez or blueman for me.

---

