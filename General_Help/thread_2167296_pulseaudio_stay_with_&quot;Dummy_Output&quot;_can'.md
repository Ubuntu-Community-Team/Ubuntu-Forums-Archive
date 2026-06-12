---
title: "pulseaudio stay with &quot;Dummy Output&quot; can't choose audio device"
date: 2013-08-13
forum: General Help
---

### Post by kqalea on 2013-08-13
Hi there

My pulseaudio suddenly can't get aduio device and stick with "Dummy Output" (ubuntu 13.04)

i already try reinstall alsa-base pulseaudio and remove some setting
didn't works

i findout that i can't access the audio devices in usermode 
but i can access it with root

for example 

$ aplay -l
aplay: device_list:252: no soundcards found...

$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
Home directory not accessible: Permission denied
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
....
....
....

I must config someting wrong to cause that

Does any body face same issue before ?
[TABLE]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

---

### Post by kqalea on 2013-08-13
Hi all

After i chmod 777 /dev/snd -R
this issue then fixed

It's must someting wrong or missconfigration otherwise that i shouldn't manually config devices node
i will keep trace this looks what if i can find the root cause

---

### Post by kqalea on 2013-08-14
Hi all

I findout the root cause is me put the wrong config into /etc/udev/rules.d/ cause some error 
after i fix the config , no longer need config promession at /dev/snd

Regards

---

