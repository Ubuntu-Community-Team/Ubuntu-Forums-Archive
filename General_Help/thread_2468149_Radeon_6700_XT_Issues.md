---
title: "Radeon 6700 XT Issues"
date: 2021-10-19
forum: General Help
---

### Post by wildpjah on 2021-10-19
Hello,
I recently installed a new GPU a 6700 XT and have been having issues. I never had issues at all with my old GTX 1060 GB after making sure I had the right driver. I got AMD because I was supposed to not have to deal with that. I am running a fresh install of Ubuntu now just to make sure nothing I did broke anything.

Firstly, there are flashes of black screen pretty consistently in a couple different spots on the screen. [https://imgur.com/Z7VzsC7](https://imgur.com/Z7VzsC7) They don't show up using screen capture so I took a video. This gets absolutely infuriating after a while. I have not been able to find any info on this, but I have a Windows partition where I have no issues so I know my card isn't just dead.

Secondly,
I have what seems to be a common enough issue but I have not been able to find a solution that works well for me. When running most games, they crash X and I have to restart it from another tty or just reboot the computer because even that doesn't work sometimes. This crash is extremely consistent and usually happens within minutes of loading a game, sometimes within seconds. The main game I have been trying this with is Total War Warhammer II if it makes a difference, but like I said it happens with plenty of other games like KSP and Middle Earth Shadow of War. The main error seems to be ```
[drm:amdgpu_job_timedout [amdgpu]] *ERROR* ring gfx_0.0.0 timeout, signaled seq=571939, emitted seq=571941
```
I've found some other forums saying that a different kernel version might work but always versions that are too old to be compatible with my 6700xt. The other things I found were to do with mesa and I tried them before the fresh install but I could've just done it wrong.

I don't usually use forums so I'm not sure the best way to post the rest of the journalctl or what else might be helpful but I'm available if you could let me know. 

Any help with either issue would be appreciated. I really enjoy linux and would hate for this to be the reason I can't use it anymore.

EDIT: I've managed to actually replicate the crashing on windows now. The flashing black squares are still a unique issue though.

---

### Post by Autodave on 2021-10-19
Did you remove all the nVidia drivers?  Did you attemp to install any drivers for the new card?  If so, what one(s) and where did you get it?

---

### Post by wildpjah on 2021-10-19
Yes when I first did it I attempted to remove everything nvidia related and I tried using amdgpu pro as well as switching between the different vulkan drivers. I had no success, so just in case I messed up something on accident before, I have installed a clean new boot where I haven't done any tinkering just to make sure I'm doing things right. That's where I am now.

---

