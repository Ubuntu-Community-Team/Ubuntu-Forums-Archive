---
title: "blank dvr window"
date: 2005-05-14
forum: General Help
---

### Post by thumper on 2005-05-14
I am trying to find a dvr solution for my system.
Installed xawtv and did 

```

tim@spike:~$ xawtv -hwscan
This is xawtv-3.94, running on Linux/i686 (2.6.10-5-686-smp)
looking for available devices
port 177-177
    type : Xvideo, image scaler
    name : NV17 Video Overlay

port 178-178
    type : Xvideo, image scaler
    name : NV17 Video Texture

port 179-210
    type : Xvideo, image scaler
    name : NV05 Video Blitter

port 211-211                            [ -xvport 211 ]
    type : Xvideo, video overlay
    name : NVIDIA Video Interface Port

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : BT878 video (Hauppauge (bt878))
    flags: overlay capture tuner

```

TV card seems to be working fine for tvtime, but I don't see any video in dvr. Running Kubuntu Hoary.

Ideas anyone?

---

