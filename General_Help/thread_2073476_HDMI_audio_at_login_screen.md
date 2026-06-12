---
title: "HDMI audio at login screen"
date: 2012-10-19
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-10-19
i need to set the systems audio output to the bold one here
```
@quantal:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: VT1708S HP [VT1708S HP]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[B]card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/B]
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```i have no issue getting my hdmi audio working, but i want it to work at the lightdm login screen (root runs the commands i have set to play sound)
this command verifies my speakers are working on card 1 device 7
```
speaker-test -Dplughw:1,7 -c 2
```if it matters on my laptop i can play ogg files like this
[FONT=Courier New]ogg123 /path/to/something.ogg[/FONT]
but on this system i have to use this
[FONT=Courier New]ogg123 -d pulse /path/to/something.ogg[/FONT]
how can i made pulse default?
i set the already default sink in [FONT=Courier New]/etc/pulse/client.conf
alsa_output.pci-0000_01_00.1.hdmi-stereo-extra1[/FONT]

---

### Post by pqwoerituytrueiwoq on 2012-10-20
I figured out how to make it work on my guest account
guest has to login to a sudo enabled account via ssh and delete there own .pulse-cookie file with sudo
at which point thy can start pulseaudio and configure the sound to work via the gui
how is that for piratical :lol:

---

### Post by pqwoerituytrueiwoq on 2012-10-20
got a fix for the guest user
/usr/local/bin/guestAudioFix
```
#!/bin/bash
sleep 1
cd /tmp
if [ $(ls guest-* 2> /dev/null | wc -l) -gt 0 ];then
    guest=$(ls | grep '\-guest-')
    rm ./$guest/.pulse-cookie
    sudo -u $guest pulseaudio --start
fi
exit

```add this line to [FONT=Courier New]/etc/lightdm/lightdm.conf[/FONT]
```
session-setup-script=sh -c "/usr/local/bin/guestAudioFix &"
```don't forget to [FONT=Courier New]chmod +x /usr/local/bin/guestAudioFix[/FONT]

now the guest user cna edit there sound preferences

now to configure the sound to work (eg hdmi sound settings)
```
sudo mkdir /etc/skel/.pulse
sudo cp ~/.pulse/* /etc/skel/.pulse/
```now the guest user does not have to adjust the sound every time they login


[SIZE=4]But I still don[SIZE=4]'t[/SIZE] have sound at the login screen (except analog)[/SIZE]

---

