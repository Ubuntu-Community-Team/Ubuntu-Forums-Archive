---
title: "Skype &amp; Bluetooth Headset"
date: 2008-04-27
forum: General Help
---

### Post by wieman01 on 2008-04-27
I might be beating a dead horse here, but I am once again out of luck.

Has anybody got Skype working with a Bluetooth headset? I would appreciate if somebody could outline what I need to do. I am using the Bluetooth server that comes with Ubuntu and my headset connects just fine. It's just that Skype does not pick up the sound device... Am I missing something?

Thanks.

---

### Post by wieman01 on 2008-04-28
Update... I also filed a bug report. This is it, perhaps someone can help:

"Pretty much summarizes my issue. My headset connects perfectly using Kubuntu's KBluetooth, then icon turns blue after entering the passkey, etc. However, when I do 'aplay' I get the following error message:
```
Playing raw data 'xxx.mp3' : Unsigned 8 bit, Rate 8000 Hz, Mono
ALSA lib pcm_params.c:2135:(snd_pcm_hw_refine_slave) Slave PCM not usable
aplay: set_params:879: Broken configuration for this PCM: no configurations available
```
My sound devices are:
```
 0 [I82801DBICH4 ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at irq 9
 1 [Headset ]: Bluetooth SCO - BT Headset
                      BT Headset 1
```
Skype does not recognize my device either. Any idea what is going on? I used to work in Feisty."

_**EDIT:**_
My launchpad bug report: [https://bugs.launchpad.net/ubuntu/+bug/223498]("https://bugs.launchpad.net/ubuntu/+bug/223498")

---

### Post by shivans on 2008-04-28
I'd be interested in the answer to this, I'm having troubles connecting my Motorola S9 up to Skype.

---

### Post by wieman01 on 2008-04-28
I'll keep you posted. I am out of luck for the moment, as this apparently relates to a kernel bug. So I keep looking for solutions.

---

### Post by psyke777 on 2008-05-08
[http://ubuntuforums.org/showthread.php?p=4910397](http://ubuntuforums.org/showthread.php?p=4910397)

---

### Post by wieman01 on 2008-05-09
Mmm... looks very promising. I might try it when I get back home in 2 weeks. Thank you. Look forward to it.

---

### Post by wieman01 on 2008-05-17
Solved my problem! Thank you very much. Worked great on Kubuntu.

---

