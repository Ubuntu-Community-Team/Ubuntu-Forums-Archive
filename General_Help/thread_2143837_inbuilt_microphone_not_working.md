---
title: "inbuilt microphone not working"
date: 2013-05-10
forum: General Help
---

### Post by NikitaLoik on 2013-05-10
Hi

I am looking for help with my inbuilt microphone.

I have recently swiched from Windows to Ubuntu 13 and was extremely happy, BUT I have a problem with my internal microphone - the sound works just alright.

I am running an old Medion MD 96350. 
Apparently my sound card is snd_hda_intel, ALC888.

I have tried out alsamixer settings, and pavucontrol setiings; both are to no avail.

I would be extremely happy if you could help me.
I would be grateful if you could give as detailed explanation as possible, since I am an absolute nube and this problem is a way to learn

Thank you very much in advance :-)

---

### Post by dino99 on 2013-05-10
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by NikitaLoik on 2013-05-11
Hi again, I followed the suggested instructions step by step, this is the result

[INDENT]1. cat /proc/asound/card0/codec* | grep Codec
[/INDENT]
[INDENT=2]Codec: Realtek ALC888
[/INDENT]
[INDENT=2]Codec: LSI ID 1040

[/INDENT]
[INDENT]2. /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz[/INDENT]
[INDENT=2]bash: /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz: Permission denied

[/INDENT]
[INDENT]3. usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
[/INDENT]
[INDENT=2]bash: usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz: No such file or directory
[/INDENT]
[INDENT]
4. Checked [HD Audio Models]("http://lxr.linux.no/#linux+v3.2.19/Documentation/sound/alsa/HD-Audio-Models.txt")[/INDENT]
[INDENT=2][COLOR=#008000]**ALC 888 corresponds to the model=medion**[/COLOR][COLOR=#a52a2a]
[/COLOR][/INDENT]
[INDENT=2][COLOR=#a52a2a][B]have no idea what LSI ID 1040 corresponds to :-(

[/B][/COLOR]
[/INDENT]
[INDENT]5. sudo nano/etc/modprobe.d/alsa-base.conf
[/INDENT]
[INDENT=2]the file looks empty
typing in 

options snd-hda-intel model=medion
sudo alsa force-reload

does not really help

[/INDENT]
I am lost again :confused:

---

### Post by NikitaLoik on 2013-05-14
Hey, dino99.

Could you possibly suggest any alternatives to try - I am absolutely lost.

Thank you.

---

