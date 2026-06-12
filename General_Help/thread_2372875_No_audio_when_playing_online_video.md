---
title: "No audio when playing online video"
date: 2017-09-29
forum: General Help
---

### Post by AbleTassie on 2017-09-29
This problem seems to be new; I did not have it before. There is a popup that suggests that PulseAudio needs to be installed:  "To play audio, you may need to install the required PulseAudio  software."

 I know Firejail can affect audio. I have Firejail installed, but it seems to be a problem whether FIrejail is running or not, including if I reboot without activating Firejail. 

Should I install PulseAudio? Is PulseAudio secure? I checked the Software Center and there seem to be PulseAudio GUI utilities, but no PulseAudio per se.

Thanks,

A.

---

### Post by mc4man on 2017-09-29
Because mind reading is a lost art you should probably add what release of Ubuntu you are using or if not Ubuntu also what flavor.
And if possible a link to any online vid that shows this behavior.

(if using Ubuntu the pulseaudio package is default installed..

---

### Post by AbleTassie on 2017-09-29
I am using Lubuntu 16.04.3 LTS, this happens with any video I try to watch online. Examples: 

[https://www.youtube.com/watch?v=0CDWc_UAdCY](https://www.youtube.com/watch?v=0CDWc_UAdCY)

[http://www.huffingtonpost.com/entry/russel-honore-katrina-commander-puerto-rico_us_59cdb801e4b06791bb0f9f25](http://www.huffingtonpost.com/entry/russel-honore-katrina-commander-puerto-rico_us_59cdb801e4b06791bb0f9f25)

[http://www.pbs.org/newshour/](http://www.pbs.org/newshour/)

---

### Post by AbleTassie on 2017-09-29
Since PulseAudio is apparently included in Ubuntu by default, it must be safe. So I used the Terminal Commands 
sudo apt-get update
sudo apt-get install pulseaudio

as suggested here [https://www.howtoinstall.co/en/ubuntu/xenial/pulseaudio](https://www.howtoinstall.co/en/ubuntu/xenial/pulseaudio) and that appears to have solved the problem, including 
when Firejail is running.

A.

---

