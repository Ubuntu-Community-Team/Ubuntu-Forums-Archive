---
title: "VLC Media Player sound breaking on high volume"
date: 2008-05-05
forum: General Help
---

### Post by spider3000 on 2008-05-05
Hello everybody.

Basically my laptop speakers are very quiet, so in VLC Media Player I put the default volume on 1024, i.e. 200%. However when there's a scene with a lot of sound, like for example a crowd cheering, the sound starts to break. Is there any way to fix this, perhaps a setting in the sound driver's options? I know this doesn't happen in Windows.


Also, is there a fix yet for using sound simultaneously on different applications?


Thanks.

---

### Post by joshsmith on 2008-05-05
your experiencing clipping, which you are not going to be able to get around. go and triple check all the relevant volume levels in gnome-volume-control to check they are really not very low

for sound stuff in hardy.
playing multiple things at once is the norm. its not like ubuntu was designed not to be able to do this. dont start to think that is usual state of peoples computers.
however, you may be sufering with some pulse bugs giving you a couple of weird incompatibilities, check my thread here:
[http://ubuntuforums.org/showthread.php?p=4724433](http://ubuntuforums.org/showthread.php?p=4724433)

---

### Post by caljohnsmith on 2008-05-05
> **spider3000 said:**
> Hello everybody.

Basically my laptop speakers are very quiet, so in VLC Media Player I put the default volume on 1024, i.e. 200%. However when there's a scene with a lot of sound, like for example a crowd cheering, the sound starts to break. Is there any way to fix this, perhaps a setting in the sound driver's options? I know this doesn't happen in Windows.


Check out this thread I started about audio distortion in Ubuntu, I think you will find it helpful:
[http://ubuntuforums.org/showthread.php?t=753418](http://ubuntuforums.org/showthread.php?t=753418)

What version of VLC are you using? I'm still using 0.8.6c from the repos, and for that version, setting volume > 50% means digital amplification, which means it could lead to distortion (max volume is 100%). If the volume control has changed in new versions, which it sounds like it has since you say yours goes to 200%, then I would bet that anything past 100% volume means digital amplification (or the potential for distortion). 

> **joshsmith said:**
> your experiencing clipping, which you are not going to be able to get around. 

I disagree--you do not have to experience distortion (clipping) if you set all volume levels appropriately so there is no digital amplification. Please see the above thread for more info on how I empirically tested to find the limits.

---

