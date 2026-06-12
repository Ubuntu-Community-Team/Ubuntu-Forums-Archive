---
title: "wine problems (not running some exe's)"
date: 2007-12-27
forum: General Help
---

### Post by xaxas on 2007-12-27
... got WoW to work allmost perfect :D
( Just that if I alt-tab while i'm ingame or swiitch to another cube face it "minimizez" but it's not in a tab on any bar ... it's running perfectly (hearing sound & all) but i don't have any idea on how to get back in it so i have to kill process and re-run :( )

The mai problem is that i need to make 3 damned programs to work for my mum so far, no results ...

problem one:
```
xaxas@cybertron:~/CABINET/EvaluareSanatate$ cd /home/xaxas/CABINET/CJAS_MF
xaxas@cybertron:~/CABINET/CJAS_MF$ wine CJAS_MF.EXE
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.

```
the program is running but no way to access anything or see what it's doing :((
this is the same for 2 progs :((


problem two
```
xaxas@cybertron:~/CABINET/EvaluareSanatate$ wine EvaluareSanatate.exe
fixme:ole:OleLoadPictureEx (0xb31c84,26702,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x34f9b8), partially implemented.
fixme:ole:OLEPictureImpl_get_hPal unimplemented for type 3. Returning 0 palette.
fixme:ole:OLEPictureImpl_Render Not quite correct implementation of rendering icons...
fixme:msxml:domdoc_QueryInterface interface {7fd52380-4e07-101b-ae2d-08002b2ec713} not implemented
fixme:msxml:domdoc_QueryInterface interface {37d84f60-42cb-11ce-8135-00aa004bb851} not implemented
fixme:msxml:xmlnode_get_nodeTypedValue ignoring data type
fixme:msxml:DllCanUnloadNow 
fixme:msxml:DllCanUnloadNow 
fixme:msxml:DllCanUnloadNow 

```
the program tryes to start and gives an error: Invalid use of NULL
no idea what i should do :((

Pleeeaze, i would apreciate any help :((
i don't want 2 go back to windows :((

---

### Post by fazavon on 2007-12-27
1. What are the programs?

2. The reality is that wine is **not** a great fix. Some things work great in Wine and others leave you... well much like after the first time you say glitter. 

Anyway, you can look up known programs that work with Wine at [http://appdb.winehq.org/](http://appdb.winehq.org/)

Hope that helps.

//j

---

### Post by alpinesatan on 2007-12-27
Hey!

There also other windows emulators avalible, just google it and you will be suprised.

kind Regards

---

### Post by xaxas on 2007-12-27
those programs are known only to romanian doctors and are made by goat-people in C++ or other ancient languages so this is a first-time they're ever tried under linux :((

---

