---
title: "Audacity Error Message"
date: 2005-05-24
forum: General Help
---

### Post by ceti on 2005-05-24
Audacity always opens with this error message:

[i]There was an error initializing the audio I/O layer.
You will not be able to play or record audio.

Error: Host error

[/i]The Audio IO section in the configuration file **.audacity **reads:
[AudioIO]
PlaybackDevice=/dev/dsp
RecordingDevice=/dev/dsp
.....

I have /dev/dsp  in my Ubuntu tree, so what's wrong?

Thanks

---

### Post by JonahRowley on 2005-05-24
What are the permissions like on **/dev/dsp**?  Are you in the **audio** group?  Does Audacity have ALSA support?  If so, try using that instead of OSS.

---

### Post by ceti on 2005-05-25
thanx.
solved.

---

### Post by eight_car on 2006-02-08
I get the same error!

1) Where is the .audacity file located?

2) I have the proper permissions

3) It won't pull up ANY output interfaces on the GUI

How do I fix this?

Thanks

---

### Post by vladdythephotogeek on 2006-07-07
> **eight_car said:**
> I get the same error!

1) Where is the .audacity file located?

2) I have the proper permissions

3) It won't pull up ANY output interfaces on the GUI

How do I fix this?

Thanks

Same problem. Any help would be greatly appriciated.

---

### Post by matjaz_pirnovar on 2006-07-08
Same problem here. What I want is to record the sound and that's exactly what I can't now!

"There was an error initializing the audio I/O layer.
You will not be able to play or record audio."

Help appreciated.

M

---

### Post by sonicbalalaika on 2006-12-06
First, sorry about my bad english.

For solving that problem there are 2 ways:

1) system/preferences/Sound  uncheck "mixing esd" and "play system sounds" 
2) Before running audacity type "sudo killall esd".

---

