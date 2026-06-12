---
title: "Firefox with multipe sound cards"
date: 2007-10-19
forum: General Help
---

### Post by motley on 2007-10-19
Hi,

My machine is running Ubuntu fiesty and I have 2 sound cards installed on it. I can hear sound from all applications  except firefox  when running flash video.

 I have installed flash 9 which uses alsa.

My asoundrc for user A looks like:

pcm.!default {
        type hw
        card 0
}
ctl.!default {
        type  hw
        card 0
}


My asoundrc for user B looks like:

pcm.!default {
        type hw
        card 1
}
ctl.!default {
        type  hw
        card 1
}


I can hear sound just for both users except firefox from the above .asoundrc configuration

If I delete .asoundrc than I can hear sound for one user but not for other.


Any pointers are highly appreciated. 

Thanks a ton

---

