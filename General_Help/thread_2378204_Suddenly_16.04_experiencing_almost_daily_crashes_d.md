---
title: "Suddenly 16.04 experiencing almost daily crashes due to [?] GPU 'panic'"
date: 2017-11-21
forum: General Help
---

### Post by crazybear on 2017-11-21
I'm using Ubuntu Gnome 16.04. I have a top-of-the-line AMD GPU - which, at best, has problems with 16.04. 

I often have to boot up two or even three times to get my 3 screens/heads all working - although my GPU can easily handle six monitors [it is 16.04 that can not handle them with AMD]. That was annoying enough, but usually once I got all three working [when one or two were not, they were either too blurred to see what was on the screen, or the monitor would be black] things used to continue as normal. 

Not anymore. Now I get lots of freqent freeze-ups [I see the windows, but nothing can be changed and all is frozen - must do a hard shut-down] or a crash [interestingly a screen appears with only a time - the time at which the computer crashed]. I finally figured out to go to the /var/log/syslog and find that time and just before. I am NOT an expert at reading these [i can post, but they tend to be VERY large]. 

What I see, with my inexpert eye, is the GPU having trouble and all processor activity going to attempt to normalize it. None of the statements I see repeated [often several hundreds of times] when put into a search engine get me answers for solutions. Anyone who thinks they can help me, it would be MOST appreciated. Why it used to work fairly well and now not, I have no idea. It is fully updated, has lots of memory and a powerful CPU, great MB, great GPU with tons of memory and I'm using only half of the number of monitors the GPU can handle. Please help. I have not kept EVERY syslog report, but I have several and can collect more as the computer crashes nearly every day or every other day now...I see patterns, but do NOT understand what the words are really indicating. I hope someone here does...I'm sure someone to many here do....

A sample of what I call GPU panic is below, and I'll try to upload an entire session, but they are huge files.

```
ffff8ad393309000, new_rbo = ffff8ad392d03000
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.534765]
[drm:radeon_crtc_page_flip_target [radeon]] flip-ioctl() cur_rbo =
ffff8ad393309000, new_rbo = ffff8ad392d03000
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.550953]
[drm:drm_mode_addfb2 [drm]] [FB:60]
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.550971]
[drm:radeon_crtc_page_flip_target [radeon]] flip-ioctl() cur_rbo =
ffff8ad392d03000, new_rbo = ffff8ad392d07800
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.551008]
[drm:radeon_crtc_page_flip_target [radeon]] flip-ioctl() cur_rbo =
ffff8ad392d03000, new_rbo = ffff8ad392d07800
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.551039]
[drm:radeon_crtc_page_flip_target [radeon]] flip-ioctl() cur_rbo =
ffff8ad392d03000, new_rbo = ffff8ad392d07800
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.567621]
[drm:drm_mode_addfb2 [drm]] [FB:97]
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.567636]
[drm:radeon_crtc_page_flip_target [radeon]] flip-ioctl() cur_rbo =
ffff8ad392d07800, new_rbo = ffff8ad393309000
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.567672]
[drm:radeon_crtc_page_flip_target [radeon]] flip-ioctl() cur_rbo =
ffff8ad392d07800, new_rbo = ffff8ad393309000
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.567704]
[drm:radeon_crtc_page_flip_target [radeon]] flip-ioctl() cur_rbo =
ffff8ad392d07800, new_rbo = ffff8ad393309000
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.584275]
[drm:drm_mode_addfb2 [drm]] [FB:60]
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.584290]
[drm:radeon_crtc_page_flip_target [radeon]] flip-ioctl() cur_rbo =
ffff8ad393309000, new_rbo = ffff8ad392d03000
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.584326]
[drm:radeon_crtc_page_flip_target [radeon]] flip-ioctl() cur_rbo =
ffff8ad393309000, new_rbo = ffff8ad392d03000
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.584357]
[drm:radeon_crtc_page_flip_target [radeon]] flip-ioctl() cur_rbo =
ffff8ad393309000, new_rbo = ffff8ad392d03000
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.601100]
[drm:drm_mode_addfb2 [drm]] [FB:97]
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.601115]
[drm:radeon_crtc_page_flip_target [radeon]] flip-ioctl() cur_rbo =
ffff8ad392d03000, new_rbo = ffff8ad392d07800
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.601152]
[drm:radeon_crtc_page_flip_target [radeon]] flip-ioctl() cur_rbo =
ffff8ad392d03000, new_rbo = ffff8ad392d07800
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.601183]
[drm:radeon_crtc_page_flip_target [radeon]] flip-ioctl() cur_rbo =
ffff8ad392d03000, new_rbo = ffff8ad392d07800
Nov 4 10:57:59 peterandcrazybear-GA-X58A-UD7 kernel: [21047.617742]
[drm:drm_mode_addfb2 [drm]] [FB:60]
```

[and this goes on with NO OTHER entries [!] for perhaps 100 pages!

or:

```
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.914384] [drm:drm_crtc_helper_set_mode [drm_kms_helper]] [CRTC:36:crtc-0]
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.914410] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 32 to mode 3, devices 00000008, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.914426] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 32 to mode 3, devices 00000080, active_devices 00000080
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.917535] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 33 to mode 3, devices 00000200, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.917551] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 33 to mode 3, devices 00000400, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.917565] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 21 to mode 3, devices 00000001, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.940595] [drm:radeon_compute_pll_avivo [radeon]] 154000 - 153900, pll dividers - fb: 171.0 ref: 5, post 6
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.940666] [drm:radeon_crtc_handle_flip [radeon]] radeon_crtc->flip_status = 0 != RADEON_FLIP_SUBMITTED(2)
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.940703] [drm:drm_crtc_helper_set_mode [drm_kms_helper]] [ENCODER:55:TMDS-55] set [MODE:97:]
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.940718] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 30 to mode 3, devices 00000800, active_devices 00000800
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.949948] [drm:radeon_crtc_load_lut [radeon]] 0
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.950007] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 30 to mode 0, devices 00000800, active_devices 00000800
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.951189] [drm:drm_crtc_helper_set_config [drm_kms_helper]] Setting connector DPMS state to on
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.951192] [drm:drm_crtc_helper_set_config [drm_kms_helper]]     [CONNECTOR:56VI-I-1] set DPMS on
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.951207] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 32 to mode 3, devices 00000008, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.951222] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 33 to mode 3, devices 00000200, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.951236] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 33 to mode 3, devices 00000400, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.951250] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 21 to mode 3, devices 00000001, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972119] [drm:drm_mode_setcrtc [drm]] [CRTC:38:crtc-1]
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972127] [drm:drm_mode_setcrtc [drm]] [CONNECTOR:59:DVI-D-1]
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972130] [drm:drm_crtc_helper_set_config [drm_kms_helper]] 
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972133] [drm:drm_crtc_helper_set_config [drm_kms_helper]] [CRTC:38:crtc-1] [FB:71] #connectors=1 (x y) (1920 0)
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972136] [drm:drm_crtc_helper_set_config [drm_kms_helper]] crtc has no fb, full mode set
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972139] [drm:drm_crtc_helper_set_config [drm_kms_helper]] [CONNECTOR:50P-2] to [NOCRTC]
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972142] [drm:drm_crtc_helper_set_config [drm_kms_helper]] [CONNECTOR:56VI-I-1] to [CRTC:36:crtc-0]
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972144] [drm:drm_crtc_helper_set_config [drm_kms_helper]] crtc changed, full mode switch
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972147] [drm:drm_crtc_helper_set_config [drm_kms_helper]] [CONNECTOR:59VI-D-1] to [CRTC:38:crtc-1]
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972149] [drm:drm_crtc_helper_set_config [drm_kms_helper]] attempting to set mode from userspace
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972157] [drm:drm_mode_debug_printmodeline [drm]] Modeline 97:"" 0 154000 1920 1968 2000 2080 1200 1203 1209 1235 0x0 0x9
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972169] [drm:radeon_encoder_set_active_device [radeon]] setting active device to 00000040 from 00000040 00000040 for encoder 2
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972174] [drm:drm_crtc_helper_set_mode [drm_kms_helper]] [CRTC:38:crtc-1]
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972196] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 32 to mode 3, devices 00000008, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972211] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 32 to mode 3, devices 00000080, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972226] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 33 to mode 3, devices 00000200, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972240] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 33 to mode 3, devices 00000400, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972254] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 21 to mode 3, devices 00000001, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972325] [drm:radeon_compute_pll_avivo [radeon]] 154000 - 153900, pll dividers - fb: 171.0 ref: 5, post 6
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972431] [drm:radeon_crtc_handle_flip [radeon]] radeon_crtc->flip_status = 0 != RADEON_FLIP_SUBMITTED(2)
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972435] [drm:drm_crtc_helper_set_mode [drm_kms_helper]] [ENCODER:58:TMDS-58] set [MODE:97:]
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.972449] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 30 to mode 3, devices 00000040, active_devices 00000040
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.981951] [drm:radeon_crtc_load_lut [radeon]] 1
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.998654] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 30 to mode 0, devices 00000040, active_devices 00000040
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.999847] [drm:drm_crtc_helper_set_config [drm_kms_helper]] Setting connector DPMS state to on
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.999850] [drm:drm_crtc_helper_set_config [drm_kms_helper]]     [CONNECTOR:59VI-D-1] set DPMS on
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.999865] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 32 to mode 3, devices 00000008, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.999879] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 33 to mode 3, devices 00000200, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.999894] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 33 to mode 3, devices 00000400, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5802.999908] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 21 to mode 3, devices 00000001, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.023996] [drm:drm_mode_setcrtc [drm]] [CRTC:40:crtc-2]
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.024012] [drm:drm_mode_setcrtc [drm]] [CONNECTOR:50:DP-2]
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.024015] [drm:drm_crtc_helper_set_config [drm_kms_helper]] 
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.024018] [drm:drm_crtc_helper_set_config [drm_kms_helper]] [CRTC:40:crtc-2] [FB:71] #connectors=1 (x y) (3840 0)
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.024021] [drm:drm_crtc_helper_set_config [drm_kms_helper]] crtc has no fb, full mode set
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.024024] [drm:drm_crtc_helper_set_config [drm_kms_helper]] crtc changed, full mode switch
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.024027] [drm:drm_crtc_helper_set_config [drm_kms_helper]] [CONNECTOR:50P-2] to [CRTC:40:crtc-2]
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.024030] [drm:drm_crtc_helper_set_config [drm_kms_helper]] [CONNECTOR:56VI-I-1] to [CRTC:36:crtc-0]
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.024032] [drm:drm_crtc_helper_set_config [drm_kms_helper]] [CONNECTOR:59VI-D-1] to [CRTC:38:crtc-1]
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.024035] [drm:drm_crtc_helper_set_config [drm_kms_helper]] attempting to set mode from userspace
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.024042] [drm:drm_mode_debug_printmodeline [drm]] Modeline 97:"" 0 154000 1920 1968 2000 2080 1200 1203 1209 1235 0x0 0x9
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.024054] [drm:radeon_encoder_set_active_device [radeon]] setting active device to 00000080 from 00000080 00000080 for encoder 2
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.024060] [drm:drm_crtc_helper_set_mode [drm_kms_helper]] [CRTC:40:crtc-2]
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.024083] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 32 to mode 3, devices 00000008, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.024097] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 33 to mode 3, devices 00000200, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.024112] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 33 to mode 3, devices 00000400, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.024126] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 21 to mode 3, devices 00000001, active_devices 00000000
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.024198] [drm:radeon_compute_pll_avivo [radeon]] 100000 - 99900, pll dividers - fb: 37.0 ref: 1, post 10
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.034013] [drm:radeon_crtc_handle_flip [radeon]] radeon_crtc->flip_status = 0 != RADEON_FLIP_SUBMITTED(2)
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.034023] [drm:drm_crtc_helper_set_mode [drm_kms_helper]] [ENCODER:49:TMDS-49] set [MODE:97:]
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.034055] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 32 to mode 3, devices 00000080, active_devices 00000080
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.036882] [drm:radeon_crtc_load_lut [radeon]] 2
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.036967] [drm:radeon_atom_encoder_dpms [radeon]] encoder dpms 32 to mode 0, devices 00000080, active_devices 00000080
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.047063] [drm:radeon_dp_link_train [radeon]] clock recovery at voltage 0 pre-emphasis 0
Nov  6 07:38:58 peterandcrazybear-GA-X58A-UD7 kernel: [ 5803.049173] [drm:radeon_dp_link_train [radeon]] channel eq at voltage 0 pre-emphasis 0
```

going on for several hundred pages with no other computer functions reported as were reported BEFORE this panic started.

Sorry, I tried many times, but seem not to be able to upload the syslog files I have. I get error messages for size or type.

---

### Post by dragonfly41 on 2017-11-21
This idea (unproven) comes from a google search .. using multiple search term (operators) taken from your logs ..

```
"new_rbo" NEAR "freeze"
``` .. finds ..

[https://askubuntu.com/questions/821987/syslog-filling-up-with-radeon-crtc-page-flip-only-on-ubuntu-16-04-unity-deskto](https://askubuntu.com/questions/821987/syslog-filling-up-with-radeon-crtc-page-flip-only-on-ubuntu-16-04-unity-deskto)

From this I extract this clue ...

> The issue doesn't occur with Gnome Metacity or Compiz. 

I would try installing gnome-session-flashback (I have this installed myself in Ubuntu 16.04) and reboot to select Gnome Metacity.

Here is an older writeup for 14.04

[http://www.webupd8.org/2014/04/how-to-install-and-tweak-gnome.html](http://www.webupd8.org/2014/04/how-to-install-and-tweak-gnome.html)

---

### Post by crazybear on 2017-11-21
> **dragonfly41 said:**
> This idea (unproven) comes from a google search .. using multiple search term (operators) taken from your logs ..

```
"new_rbo" NEAR "freeze"
``` .. finds ..

[https://askubuntu.com/questions/821987/syslog-filling-up-with-radeon-crtc-page-flip-only-on-ubuntu-16-04-unity-deskto](https://askubuntu.com/questions/821987/syslog-filling-up-with-radeon-crtc-page-flip-only-on-ubuntu-16-04-unity-deskto)

From this I extract this clue ...

 

I would try installing gnome-session-flashback (I have this installed myself in Ubuntu 16.04) and reboot to select Gnome Metacity.

Here is an older writeup for 14.04

[http://www.webupd8.org/2014/04/how-to-install-and-tweak-gnome.html](http://www.webupd8.org/2014/04/how-to-install-and-tweak-gnome.html)

Well, thanks - that would be an interesting suggestion but I DO use Metacity! This also doesn't explain why these crashes didn't happen months ago and are more frequent now, as I have always used Metacity. I have Unity as a log in choice too - I NEVER use it - I HATE it and LOATH the idea Ubuntu ever conceived of it and promote  it still - but that is me. Should I / can I uninstall Unity without damaging all else? Is it running in the background and causing some problem?

---

### Post by dragonfly41 on 2017-11-21
> [COLOR=#000000]Should I / can I uninstall Unity without damaging all else? Is it running in the background and causing some problem?[/COLOR]

I'm sorry, I just don't know if Unity can be uninstalled.
Nor can I suggest why this has suddenly appeared.
I agree that syslogs are difficult to comprehend, that is why I use text mining to look for patterns.
There is the option of trying Compiz, just to see if that works.

---

### Post by crazybear on 2017-11-21
> **dragonfly41 said:**
> I'm sorry, I just don't know if Unity can be uninstalled.
Nor can I suggest why this has suddenly appeared.
I agree that syslogs are difficult to comprehend, that is why I use text mining to look for patterns.
There is the option of trying Compiz, just to see if that works.


Compiz works so poorly on my computer I don't use it enough to know if it crashes or not - it is not usable for me to work on the computer. Don't know why, but many features are missing or do not work. So, now what? I have no reason to believe any of my hardware is deteriorating, so it must be that some kernel or other updates are now effecting what NEVER was a good match between AMD GPU and 16.04!

---

### Post by dragonfly41 on 2017-11-21
Further searching using different search pattern suggests increasing frame buffer size in UEFI bios.

[https://bugs.debian.org/cgi-bin/bugreport.cgi?att=1;bug=703370;filename=130319193059.BMP;msg=31](https://bugs.debian.org/cgi-bin/bugreport.cgi?att=1;bug=703370;filename=130319193059.BMP;msg=31)

source:  [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=703370](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=703370)

My _guess_ is that this symptom has appeared after a recent upgrade .. has UEFI BIOS been upgraded?

---

### Post by crazybear on 2017-11-21
> **dragonfly41 said:**
> Further searching using different search pattern suggests increasing frame buffer size in UEFI bios.

[https://bugs.debian.org/cgi-bin/bugreport.cgi?att=1;bug=703370;filename=130319193059.BMP;msg=31](https://bugs.debian.org/cgi-bin/bugreport.cgi?att=1;bug=703370;filename=130319193059.BMP;msg=31)

source:  [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=703370](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=703370)

My _guess_ is that this symptom has appeared after a recent upgrade .. has UEFI BIOS been upgraded?

No. My MB is too old to even offer new BIOS upgrades. AS to UEFI BIOS, I'm not sure I know what that is/entails. I did update the stack long ago [without doing so 16.04 wouldn't work with my AMD at all] - but longer ago than I remember this problem starting. I do not know exactly when this began - I think a few months ago; then it was once per few weeks. Now it is about every other day, sometimes every day and DAMN annoying! I've lost no data yet...but it is only time before I do. I have to fix this, but first I must diagnose it. I was just thinking of going to six monitors, but will not even think of it until three are working. Is Ubuntu ever going to be compatible with AMD again?

Aside...12.04 worked flawlessly; 14.04 had more problems, but was still OK; 16.04 for me has been a disaster and is getting worse. I have long been a fan of Ubuntu/Linux - but that is fading...fast.

---

### Post by dragonfly41 on 2017-11-21
There are many questions here I can't answer.

However, this is the gameplan I would follow based on my own recent efforts to better understand and analyse logs.

First I would install TextSTAT which is a tool for analysing unstructured text (such as text in log files).
I have posted ideas for using TextSTAT and I suggest that you search the forum for TextSTAT.

When you understand how to use TextSTAT, create a corpus containing all relevant log files (including earlier archived log files going back to before this started.   

Or you might use a service such as loggly.
[https://www.loggly.com/ultimate-guide/analyzing-linux-logs/](https://www.loggly.com/ultimate-guide/analyzing-linux-logs/)

Now analyse word forms to look for recurring patterns such as &#8220;new_rbo&#8221; and &#8220;radeon_crtc_page_flip_target&#8221;

The concordance window will point to text fragments (say 40 characters on either side of &#8220;new_rbo&#8221; or other chosen word form.

You are using this tool to find clues, better than just staring at log files.

Include /var/log/Xorg.0.log in your corpus.

Now try to find date when this started.

Finding a start date now look to see if you can correlate this date with Ubuntu upgrades or kernel upgrades.   There must be a register somewhere.

...

Re: your questions on AMD & Ubuntu I would follow other discussions about AMD + Ubuntu.
There is one nearby thread.

[https://ubuntuforums.org/showthread.php?t=2378181](https://ubuntuforums.org/showthread.php?t=2378181)

---

### Post by crazybear on 2017-11-21
> **dragonfly41 said:**
> There are many questions here I can't answer.

However, this is the gameplan I would follow based on my own recent efforts to better understand and analyse logs.

First I would install TextSTAT which is a tool for analysing unstructured text (such as text in log files).
I have posted ideas for using TextSTAT and I suggest that you search the forum for TextSTAT.

When you understand how to use TextSTAT, create a corpus containing all relevant log files (including earlier archived log files going back to before this started.   

Or you might use a service such as loggly.
[https://www.loggly.com/ultimate-guide/analyzing-linux-logs/](https://www.loggly.com/ultimate-guide/analyzing-linux-logs/)

Now analyse word forms to look for recurring patterns such as “new_rbo” and “radeon_crtc_page_flip_target”

The concordance window will point to text fragments (say 40 characters on either side of “new_rbo” or other chosen word form.

You are using this tool to find clues, better than just staring at log files.

Include /var/log/Xorg.0.log in your corpus.

Now try to find date when this started.

Finding a start date now look to see if you can correlate this date with Ubuntu upgrades or kernel upgrades.   There must be a register somewhere.

...

Re: your questions on AMD & Ubuntu I would follow other discussions about AMD + Ubuntu.
There is one nearby thread.

[https://ubuntuforums.org/showthread.php?t=2378181](https://ubuntuforums.org/showthread.php?t=2378181)

PFFT~! That sounds 'great' but difficult, time consuming and probably beyond my technical abilities. Even if it shows a kernel update that caused the problem, I'd likely have to drop down six ago or so...and what other problem would that cause? As for AMD-Ubuntu threads and online posts, I must have read them all...just read the one you pointed to and it is the same old same old. Lucky for me I do not do gaming. I use multiple monitors for a HUGE desktop for research I do - but I like my computer to perform well and it is NOT - never did in the graphics department even BEFORE this issue which causes freezes or crashes [I assume they are caused by the same thing, though haven't yet proven that]. I'm not even sure where older syslogs are kept or if one has to tell the computer to keep them. I see only the current and one former one - but then I'm no expert. As for xorg.log files I know ziltch. Nothing with Ubuntu is easy...some like that...I do not. I need to be doing research, not playing around with the OS all the time. I'd go back to 14.04, but mine is not working and no one yet has been able to help me get that working again...but that is another story for another thread. thanks. I see I have a lot of learning and work to do....where is 18.04? and will it be better with AMD? I hope so....16.04 is horrible with one of the two better GPU makers - NOT a plus on anyone's side.....

---

### Post by QIII on 2017-11-21
Hello!

Did you do a fresh installation of 16.04 or did you upgrade in place?  What driver were you using before updating?  Did you remove it before you updated?  What specific model is your top of the line GPU?

The amount of help we can provide without stabbing wildly in the dark is directly proportional to the amount of diagnostic information we have.

When hardware that works for a while suddenly and inexplicably stops working, suspicion falls on the hardware.  However, it is best to rule out software/driver/OS issues.

---

### Post by crazybear on 2017-11-21
> **QIII said:**
> Hello!

Did you do a fresh installation of 16.04 or did you upgrade in place?  What driver were you using before updating?  Did you remove it before you updated?  What specific model is your top of the line GPU?

The amount of help we can provide without stabbing wildly in the dark is directly proportional to the amount of diagnostic information we have.

When hardware that works for a while suddenly and inexplicably stops working, suspicion falls on the hardware.  However, it is best to rule out software/driver/OS issues.

I did an upgrade from 14.04. In 14.04 of course I used fglx and the latest one. It worked fine. Any problems I had with 14.04 did NOT involve the GPU at all. I believe I removed it before updating, yes. the GPU is an AMD Radeon HD 7970 Extreme Edition. It is not overheating or acting up in Windows [in which it acts perfectly. Windows stinks, but has the ability to have the latest AMD driver - I think it is NOT the hardware. 16.04 is notorious for AMD problems. I upgraded to this 16.04 several YEARS ago, but the crashes only started a few MONTHS ago and have become more frequent, yet I have been in Windows recently and all was fine. In 16.04 it always had the problem of one or two monitors not starting correctly, but if one reboots, when they all start correctly they remain so. My GPU is NOT listed as compatible with the proprietary add-on to the 'great' [ha!] Ubuntu AMD driver.

---

### Post by QIII on 2017-11-21
16.04 is not notorious for AMD problems.  It is "notorious" only in that it does not include the non-supported fglrx driver and uses by default the open source Radeon driver or the open source AMDGPU driver, whichever is appropriate for the hardware.  This is not unique to Ubuntu.

There is no "Ubuntu AMD driver", so the issue does not lie with Ubuntu.

Your HD 7970 is not compatible withe the AMDGPU driver.

More in a bit.  I have a meeting to go to.

---

### Post by crazybear on 2017-11-21
> **QIII said:**
> 16.04 is not notorious for AMD problems.  It is "notorious" only in that it does not include the non-supported fglrx driver and uses by default the open source Radeon driver or the open source AMDGPU driver, whichever is appropriate for the hardware.  This is not unique to Ubuntu.

There is no "Ubuntu AMD driver", so the issue does not lie with Ubuntu.

Your HD 7970 is not compatible withe the AMDGPU driver.

More in a bit.  I have a meeting to go to.

Yes, I know it is not compatible with the AMDGPU. Sorry, but I will stay with my 'take' on 16.04 being *_well known_* for problems with AMD GPU's - spin it anyway you like - it isn't going to change _**my**_ viewpoint, nor the huge number of threads and problems listed on the internet, as well as this forum, on this matter. As forum admin you can defend the honor of Ubuntu. I saw the difference between the open source AMD driver and fglx driver in 14.04. The open source Radeon driver never was more than fair - but as I don't do gaming or too many other GPU-intensive things I was moderately satisfied in 16.04 [minus the problem with multiple monitors issues] until the crashes began. Maybe those who can use AMDGPU are happier. I can't know what that is like. I did some research today and supposedly 18.04 will work well with AMD GPU's, but that is six months away!!!!

---

### Post by QIII on 2017-11-21
Your experience, whatever the cause, is frustrating.  I understand that.  But part of understanding how to proceed is understanding what the issue is.  And that is not Ubuntu.  I'm in no way beholden to Ubuntu nor am I beholden to Canonical.  I'm not employed by Canonical.  I'm not an Ubuntu evangelist.  If I don't think Ubuntu is the best option for someone, I have no problem recommending other OSes -- including Windows.  I own my own company and provide my time on the Ubuntu Forums voluntarily.

The reason it is important to understand the actual issue is this:  fglrx is no longer supported by AMD for more recent versions of X.  Your card is not supported by AMDGPU because that driver will only work with GCN (Graphics Core Next) hardware.  When installed, Ubuntu will choose between the AMDGPU driver or the Radeon driver depending on which hardware is present and what it supports.  Those are the two options that are available for AMD products.  There is nothing Canonical can do about that.  AMDGPU is developed by AMD, not by anyone at Canonical.  But because of the relationship between Canonical and AMD, the AMDGPU driver was first made available and tested on Ubuntu.

The number of problems and posts you see on the web or here at the Forums is skewed.  People don't complain when things go right, but when things go wrong.  Since we don't see the complaints about things going right, we have no way to gauge the incidence of problems as a function of number of users.  It may be high.  It may be low.  We can't determine that.  16.04 will already work with AMD cards.  When installed, a unit unsupported by AMDGPU will cause a default installation of the Radeon driver, which does, in fact, work well for the majority of users.  This is not an issue unique to Ubuntu.

I use an R9 380X, an AMDGPU supported card, and have absolutely no problems with 16.04.  I also have installed the AMDGPU-PRO overlay and the Vulkan SDK.  With the switch to Wayland, however, there are issues yet to be worked out with regard to AMDGPU.  AMD is working on that, but I am sticking with X for the moment.  That IS a problem for the user, but it is not caused by Ubuntu.  Your card is not supported by AMDGPU, so we must look elsewhere to address your particular problem.

Given that understanding of the issue, a rational and methodical approach to resolution is in order.  Let's start here (partly based on the fact that you updated rather than installing afresh):  

We first need to determine what driver module is loaded into the kernel.  You can do this by 

```
lsmod
```

Generally I would ask you to grep for something specific, but in this case a complete list would be best.  Please post the complete results.

---

### Post by dragonfly41 on 2017-11-21
I don't want to take this discussion off its course since QIII has much more experience in this Ubuntu / AMD discussion and is an AMD user.

This discussion explained the problem to me at least ..
[http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)

However in my recent purchase of Windows 10 on Dell I learned about Windows Subsystem for Linux (WSL) which is Ubuntu 14.04 running in Windows.

My thought is, in the interim, and depending on the nature of your research could you run whatever research you are engaged in on WSL (Ubuntu 14.04 sans desktop) and leave Windows+AMD to present results to your monitors?   It would help if you could expand on the nature of your research.

Another similar line of thought as an interim measure is to run Ubuntu on Windows VirtualBox.

This doesn't explain why there was a change in your circumstances.   You might think this is a cop out.
But it might give you something to work on while getting to grips with the core issue of Ubuntu 16.04 + AMD compatibility.

---

### Post by QIII on 2017-11-21
Looking back through my research for [this blog article]("https://theleftcoastgeek.net/index.php/hardware/12-possible-amdgpu-pro-supported-gpus-by-the-end"), I see that the HD 7970 is a GCN 1.0 GPU.  Since AMD started supporting GCN 1.1 and later first, they had to work backwards to cover GCN 1.0 GPUs.  It looks like that work may be done (at least for some cards) by the time 18.04 arrives with its version of the kernel.

In six months, this discussion may be moot.  But let's see if we can't get you through until then in some fashion.

---

### Post by crazybear on 2017-11-22
> **dragonfly41 said:**
> I don't want to take this discussion off its course since QIII has much more experience in this Ubuntu / AMD discussion and is an AMD user.

This discussion explained the problem to me at least ..
[http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)

However in my recent purchase of Windows 10 on Dell I learned about Windows Subsystem for Linux (WSL) which is Ubuntu 14.04 running in Windows.

My thought is, in the interim, and depending on the nature of your research could you run whatever research you are engaged in on WSL (Ubuntu 14.04 sans desktop) and leave Windows+AMD to present results to your monitors?   It would help if you could expand on the nature of your research.

Another similar line of thought as an interim measure is to run Ubuntu on Windows VirtualBox.

This doesn't explain why there was a change in your circumstances.   You might think this is a cop out.
But it might give you something to work on while getting to grips with the core issue of Ubuntu 16.04 + AMD compatibility.

I do not use Windows! When I do on rare occasions I turn off internet. Windows has an agreement with the intelligence communities and backdoors. It is spyware! What I legally do I have reasons to avoid all spyware. I also have every OS on SEPARATE disks and always will be such...so I can not and will not run Ubuntu withing Windows...sorry. Thanks, but my work is very special and I can not / will not detail it here in the least.

> **QIII said:**
> Your experience, whatever the cause, is frustrating.  I understand that.  But part of understanding how to proceed is understanding what the issue is.  And that is not Ubuntu.  I'm in no way beholden to Ubuntu nor am I beholden to Canonical.  I'm not employed by Canonical.  I'm not an Ubuntu evangelist.  If I don't think Ubuntu is the best option for someone, I have no problem recommending other OSes -- including Windows.  I own my own company and provide my time on the Ubuntu Forums voluntarily.

The reason it is important to understand the actual issue is this:  fglrx is no longer supported by AMD for more recent versions of X.  Your card is not supported by AMDGPU because that driver will only work with GCN (Graphics Core Next) hardware.  When installed, Ubuntu will choose between the AMDGPU driver or the Radeon driver depending on which hardware is present and what it supports.  Those are the two options that are available for AMD products.  There is nothing Canonical can do about that.  AMDGPU is developed by AMD, not by anyone at Canonical.  But because of the relationship between Canonical and AMD, the AMDGPU driver was first made available and tested on Ubuntu.

The number of problems and posts you see on the web or here at the Forums is skewed.  People don't complain when things go right, but when things go wrong.  Since we don't see the complaints about things going right, we have no way to gauge the incidence of problems as a function of number of users.  It may be high.  It may be low.  We can't determine that.  16.04 will already work with AMD cards.  When installed, a unit unsupported by AMDGPU will cause a default installation of the Radeon driver, which does, in fact, work well for the majority of users.  This is not an issue unique to Ubuntu.

I use an R9 380X, an AMDGPU supported card, and have absolutely no problems with 16.04.  I also have installed the AMDGPU-PRO overlay and the Vulkan SDK.  With the switch to Wayland, however, there are issues yet to be worked out with regard to AMDGPU.  AMD is working on that, but I am sticking with X for the moment.  That IS a problem for the user, but it is not caused by Ubuntu.  Your card is not supported by AMDGPU, so we must look elsewhere to address your particular problem.

Given that understanding of the issue, a rational and methodical approach to resolution is in order.  Let's start here (partly based on the fact that you updated rather than installing afresh):  

We first need to determine what driver module is loaded into the kernel.  You can do this by 

```
lsmod
```

Generally I would ask you to grep for something specific, but in this case a complete list would be best.  Please post the complete results.

```

$ lsmod
Module                  Size  Used by
nls_iso8859_1          16384  1
xt_multiport           16384  1
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
ipt_MASQUERADE         16384  3
vboxnetflt             28672  0
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
vboxdrv               458752  3 vboxnetadp,vboxnetflt,vboxpci
nf_nat_ipv4            16384  1 iptable_nat
appletalk              36864  0
ipx                    28672  0
p8023                  16384  1 ipx
psnap                  16384  2 appletalk,ipx
p8022                  16384  1 ipx
bridge                139264  0
stp                    16384  1 bridge
llc                    16384  4 p8022,psnap,bridge,stp
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
snd_hrtimer            16384  1
snd_usb_audio         184320  2
uvcvideo               90112  0
usblp                  20480  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
snd_usbmidi_lib        32768  1 snd_usb_audio
joydev                 20480  0
videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
snd_hda_codec_realtek    90112  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     49152  1
ip6t_REJECT            16384  1
snd_hda_intel          36864  9
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
gpio_ich               16384  0
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  2 snd_hda_codec,snd_usb_audio
snd_pcm               102400  5 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hda_core,snd_hda_codec_hdmi
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  2 snd_seq_midi,snd_usbmidi_lib
intel_powerclamp       16384  0
kvm_intel             200704  0
snd_seq                65536  3 snd_seq_midi_event,snd_seq_midi
kvm                   593920  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
pcbc                   16384  0
snd_timer              32768  3 snd_seq,snd_hrtimer,snd_pcm
aesni_intel           167936  0
snd                    77824  36 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_usb_audio,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_usbmidi_lib,snd_seq_device,snd_hda_codec_realtek,snd_pcm
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
lpc_ich                24576  0
i7core_edac            24576  0
edac_core              53248  1 i7core_edac
soundcore              16384  1 snd
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate           20480  0
input_leds             16384  0
serio_raw              16384  0
shpchp                 36864  0
mac_hid                16384  0
xt_hl                  16384  22
ip6t_rt                16384  3
binfmt_misc            20480  1
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  3
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv6,nf_log_ipv4
xt_LOG                 16384  10
xt_limit               16384  13
xt_tcpudp              16384  24
xt_addrtype            16384  4
nf_conntrack_ipv4      16384  13
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  17
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 28672  3 nf_nat_ftp,nf_nat_masquerade_ipv4,nf_nat_ipv4
it87                   57344  0
hwmon_vid              16384  1 it87
coretemp               16384  0
libcrc32c              16384  1 nf_nat
parport_pc             32768  0
ppdev                  20480  0
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack          131072  11 nf_conntrack_ipv6,nf_conntrack_ftp,nf_conntrack_ipv4,ipt_MASQUERADE,nf_conntrack_broadcast,nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat_masquerade_ipv4,xt_conntrack,nf_nat_ipv4,nf_nat
iptable_filter         16384  1
ip_tables              24576  3 iptable_mangle,iptable_filter,iptable_nat
x_tables               36864  18 xt_LOG,xt_multiport,ipt_REJECT,iptable_mangle,ip_tables,ebtables,iptable_filter,xt_tcpudp,ipt_MASQUERADE,xt_limit,ip6t_REJECT,xt_CHECKSUM,ip6table_filter,xt_addrtype,ip6t_rt,xt_conntrack,ip6_tables,xt_hl
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
dm_mirror              24576  0
dm_region_hash         20480  1 dm_mirror
dm_log                 20480  2 dm_mirror,dm_region_hash
amdgpu               1560576  0
uas                    24576  0
usb_storage            69632  2 uas
hid_generic            16384  0
usbhid                 53248  0
hid                   118784  2 hid_generic,usbhid
amdkfd                139264  1
amd_iommu_v2           20480  1 amdkfd
mxm_wmi                16384  0
radeon               1507328  9
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                    98304  2 amdgpu,radeon
drm_kms_helper        151552  2 amdgpu,radeon
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
pata_acpi              16384  0
fb_sys_fops            16384  1 drm_kms_helper
r8169                  81920  0
mii                    16384  1 r8169
drm                   352256  9 amdgpu,radeon,ttm,drm_kms_helper
pata_jmicron           16384  1
ahci                   36864  7
libahci                32768  1 ahci
fjes                   77824  0
wmi                    16384  1 mxm_wmi
```

---

### Post by QIII on 2017-11-22
Did you attempt at any time to install AMDGPU?

I see the following modules:

```
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                    98304  2 amdgpu,radeon
drm_kms_helper        151552  2 amdgpu,radeon
drm                   352256  9 amdgpu,radeon,ttm,drm_kms_helper
```

I would expect to see either

```

i2c_algo_bit           16384  2 amdgpu
ttm                    98304  2 amdgpu
drm_kms_helper        151552  2 amdgpu
drm                   352256  9 amdgpu, ttm,drm_kms_helper

```

or

```

i2c_algo_bit           16384  2 radeon
ttm                    98304  2 radeon
drm_kms_helper        151552  2 radeon
drm                   352256  9 radeon,ttm,drm_kms_helper

```

What we may have here are conflicting drivers, either by accidental installation or by some very unexpected oddity in your updates -- maybe when you updated the graphics stack with an HWE.

---

### Post by crazybear on 2017-11-22
> **QIII said:**
> Did you attempt at any time to install AMDGPU?

I see the following modules:

```
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                    98304  2 amdgpu,radeon
drm_kms_helper        151552  2 amdgpu,radeon
drm                   352256  9 amdgpu,radeon,ttm,drm_kms_helper
```

I would expect to see either

```

i2c_algo_bit           16384  2 amdgpu
ttm                    98304  2 amdgpu
drm_kms_helper        151552  2 amdgpu
drm                   352256  9 amdgpu, ttm,drm_kms_helper

```

or

```

i2c_algo_bit           16384  2 radeon
ttm                    98304  2 radeon
drm_kms_helper        151552  2 radeon
drm                   352256  9 radeon,ttm,drm_kms_helper

```

What we may have here are conflicting drivers, either by accidental installation or by some very unexpected oddity in your updates -- maybe when you updated the graphics stack with an HWE.

I don't remember trying to install AMDGPU as I had read my GPU was not supported. Yes, I did update the stack with HWE and it was a long, complex, problematic process.

---

### Post by QIII on 2017-11-22
OK.  Somehow AMDGPU got into the mix.  What we'll try first is blacklisting AMDGPU to keep it from loading and see how that works out.  Unfortunately it is well past midnight here and I have a long work day ahead tomorrow trying to get three days work done before the holiday.  If someone else doesn't happen along before I get back to this, I'll catch up to you as soon as I can.

---

### Post by crazybear on 2017-11-22
> **QIII said:**
> OK.  Somehow AMDGPU got into the mix.  What we'll try first is blacklisting AMDGPU to keep it from loading and see how that works out.  Unfortunately it is well past midnight here and I have a long work day ahead tomorrow trying to get three days work done before the holiday.  If someone else doesn't happen along before I get back to this, I'll catch up to you as soon as I can.

Can't it just be uninstalled with 
amdgpu-pro-uninstall
....or is there some danger all drivers could be uninstalled or other things in the OS be upset?
Looking at the instructions for installing amdgpu-pro, I don't see how it got installed, as it takes several commands.

---

### Post by QIII on 2017-11-22
AMDGPU-Pro may not have been installed, but it looks like AMDGPU has.

The problem with uninstalling it right now is that we don't know its state -- is it a mess, was it installed by the HWE, was it installed by accident.

Blacklisting it will let us know if the Radeon driver by itself will work for now.  Remember:  methodical.

Still at work, but I'll get back to you on how to blacklist a module unless someone else jumps in first.

---

### Post by crazybear on 2017-11-23
> **QIII said:**
> AMDGPU-Pro may not have been installed, but it looks like AMDGPU has.

The problem with uninstalling it right now is that we don't know its state -- is it a mess, was it installed by the HWE, was it installed by accident.

Blacklisting it will let us know if the Radeon driver by itself will work for now.  Remember:  methodical.

Still at work, but I'll get back to you on how to blacklist a module unless someone else jumps in first.

Please do.....

> $ lsmod | grep amdgpu
amdgpu               1560576  0
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                    98304  2 amdgpu,radeon
drm_kms_helper        151552  2 amdgpu,radeon
drm                   352256  10 amdgpu,radeon,ttm,drm_kms_helper


It looks from researching that I need to do:
1] open /etc/modprobe.d/blacklist.conf and added the following line: blacklist amdgpu

2] sudo update-initramfs -u

But I just noticed that I can not open a terminal 'here' [at any location/folder]...hmmm....I certainly could before.
Anyway, I'll wait to hear if this is the correct course of action before trying. Now, I'm trying to get back the ability to 'open a terminal here'.

I also see this article, I've not noticed before: [https://varunpriolkar.com/2016/12/how-to-use-amdgpu-driver-for-southern-islands-and-sea-islands-card-on-ubuntu-linux/](https://varunpriolkar.com/2016/12/how-to-use-amdgpu-driver-for-southern-islands-and-sea-islands-card-on-ubuntu-linux/) [I have a 'Tahiti' card which fits this rubric, I believe].

---

### Post by QIII on 2017-11-23
That's exactly what you need to do.  Understand, however, that changing system files is intrinsically dangerous and you want to be able to get things back to their original conditions should something go terribly wrong.  You should make a backup that can be used to set things back.  Instructions often neglect the very important task of creating a backup of a file before any changes are made. I would also have a bootable copy of the live image in case things go sideways and you can't reboot.  With that you can restore your backup.  

Just open the terminal.  I assume what's meant by "here" is the directory where the file resides.   To keep this easy, let's not worry about changing directories.

To make a backup copy of the original, issue 

```
sudo cp /etc/modprobe.d/blacklist.conf /etc/modprobe.d/blacklist.conf.bak
```

The exact name is not important in and of itself.  It just needs to be something you will remember.  If you are told the original file file doesn't exist ("cannot stat xxxxx") , don't worry.

When you have that backup, then

```
sudo nano /etc/modprobe.d/blacklist.conf
```

Nano is a terminal-based text editor.  Add the line you quoted.  Make sure to press enter after that line to be sure there is a termination on that line.  Ctrl+X to save, answer "Y" and then press enter when prompted for the file name.

Then issue 

```
sudo update-initramfs -u
``` 

to update initramfs, which contains its own copy of loaded modules.

Reboot.

Let us know how that goes.  If things have blown up, use the live image to get back here.

For the moment, disregard the Padoka PPA.  PPAs are not official.  They are Personal Package Archives -- there is no guarantee that the maintainers follow any sort of rigorous standard.  I have no reason to doubt that it is a good PPA (people use it all the time).  But given the fact that you are already in a bad spot, trying to solve this particular difficulty with a PPA is probably not wise.

---

### Post by crazybear on 2017-11-23
I found this strange [to me] entry on the blacklist:
> 
# EDAC driver for amd76x clashes with the agp driver preventing the apert$
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


what is that?!

I'll reboot now and see what happens. Perhaps it will take a while to know the result.

Too early to tell what will be...but when I rebooted I had the same old problem of one [or sometimes two] monitors [of three] being blurry. So I had to re-re-boot and now it seems stable. Only very rarely does a stable monitor of the three [in the past] become unstable. I don't know if this is connected or a separate issue, but I'd like to solve it too...as I was hoping to go to the six monitors which my GPU can support....but dare not yet. As I understand, the changes I just made are ONLY on the last kernel - yes?

> **crazybear said:**
> I found this strange [to me] entry on the blacklist:

[COLOR=#000000]*EDAC driver for amd76x*[/COLOR]
what is that?!

I'll reboot now and see what happens. Perhaps it will take a while to know the result.

I see this is related to CPUs, not GPUs...and don't understand. It was put there automatically at some point.
I have an Intel i7 990X [which can handle anything]

---

### Post by QIII on 2017-11-23
Yes.  Only the currently running kernel.  You can boot to older kernels and go through the same process.

OK.  We have you at least to a point where we can say you are relatively stable and stock.  Not where you want to be with regard to using all of your monitors, of course, but at least not is some crazy state.  Still, let's please run 

```
lsmod | grep amdgpu
```

to make sure there are no results.

Again, however, it's long past time for me to get to bed.  We'll have to reconvene later.

---

### Post by crazybear on 2017-11-23
> **QIII said:**
> Yes.  Only the currently running kernel.  You can boot to older kernels and go through the same process.

OK.  We have you at least to a point where we can say you are relatively stable and stock.  Not where you want to be with regard to using all of your monitors, of course, but at least not is some crazy state.  Still, let's please run 

```
lsmod | grep amdgpu
```

to make sure there are no results.

Again, however, it's long past time for me to get to bed.  We'll have to reconvene later.

```

$ lsmod | grep amdgpu
amdgpu               1560576  0
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                    98304  2 amdgpu,radeon
drm_kms_helper        151552  2 amdgpu,radeon
drm                   352256  10 amdgpu,radeon,ttm,drm_kms_helper

```

hmmm...curious...no change.

I'll try again, but I think nothing will change....

I just ran the commands again [to try to blacklist amdgpu] and rebooted...and amdgpu is still there....ideas?

```

$ lsmod | grep amdgpu
amdgpu               1560576  0
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                    98304  2 amdgpu,radeon
drm_kms_helper        151552  2 amdgpu,radeon
drm                   352256  9 amdgpu,radeon,ttm,drm_kms_helper

```

What does the number in the third column mean? It is the only thing that changed on one line - from 10 to 9.

Is turkey dinner delaying any help?

Would really appreciate help finishing this matter. I tried several times to blacklist the module. It apparently did not work for reasons unknown.

I haven't done anything else...but have tried to research this on my own. There is a file named: xserver-xorg-video-amdgpu-hwe-16.04.list at /var/lib/dpkg/info that lists the following [don't know if this is relevant or not]:

```

/.
/usr
/usr/share
/usr/share/man
/usr/share/man/man4
/usr/share/man/man4/amdgpu.4.gz
/usr/share/X11
/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-amdgpu.conf
/usr/share/doc
/usr/share/doc/xserver-xorg-video-amdgpu-hwe-16.04
/usr/share/doc/xserver-xorg-video-amdgpu-hwe-16.04/changelog.Debian.gz
/usr/share/doc/xserver-xorg-video-amdgpu-hwe-16.04/copyright
/usr/share/bug
/usr/share/bug/xserver-xorg-video-amdgpu-hwe-16.04
/usr/lib
/usr/lib/xorg
/usr/lib/xorg/modules
/usr/lib/xorg/modules/drivers
/usr/lib/xorg/modules/drivers/amdgpu_drv.so
/usr/share/bug/xserver-xorg-video-amdgpu-hwe-16.04/script

```

I'm NO expert, but this makes me inclined to think that it was installed with the new hwe....or in some way connected to it.

---

### Post by QIII on 2017-11-26
Blacklisting the module should keep it from loading ... unless another module requires it.  

It does appear as though the HWE update may have installed amdgpu pro, having found what could now be a supported card.

In case AMDGPU-PRO was somehow installed (which might force the amdgpu module load), let's see what happens if you attempt to uninstall it.

Open the terminal and issue

```
amdgpu-pro-uninstall
```

I believe the script should be available in your path, but we can look for it elsewhere if it is not.

---

### Post by crazybear on 2017-11-26
Using [COLOR=#0000cd]lsmod | grep amdgpu-pro[/COLOR] there was nothing found.

uninstall also did nothing

OK, I think I know the problem if in fact the two drivers can not or should not be both installed, but to me there seems to be no good solution....

Here are some screenshots of what is installed, but if I check to remove only the amdgpu part of hwe, synaptic says it will remove the entire hwe-16.04 package, which I originally put in after researching in order to help with problematic monitors with my GPU. If I remove amdgpu-hwe-16.04, I have to remove the entire hwe-16.04 and I'll be back to the unsatisfactory situation I was in. Unless the computer can run with the amdgpu-hwe-16.04 and have the generic radeon drivers removed. I dare not try that without first doing some research or knowing the consequences......

---

### Post by QIII on 2017-11-27
OK.  Before removing the entire HWE, the next "rule out" attempt might be to remove amdgpu from the blacklist and blacklist radeon instead.  Again, have a live dvd or usb image handy.  You still have a copy of the original config file?

---

### Post by crazybear on 2017-11-27
Before I start doing drastic things, remember that my GPU is NOT listed as approved for amdgpu! The radeon generic driver 'is' by generic default.

I just found this statement [not yet the way to implement it] "Newer cards (GCN 1.2+) can also use AMDGPU. You can force AMDGPU to be used by using a custom xorg.conf." here [https://www.linkedin.com/pulse/using-newer-amdgpu-driver-ubuntu-1604lts-dennis-mungai](https://www.linkedin.com/pulse/using-newer-amdgpu-driver-ubuntu-1604lts-dennis-mungai)

which 'custom xorg.conf' ? 
and [? here] [https://wiki.archlinux.org/index.php/AMDGPU#Enable_early_KMS](https://wiki.archlinux.org/index.php/AMDGPU#Enable_early_KMS)

Also: [COLOR=#000000][FONT=&quot]drm                   352256  9 amdgpu,radeon,ttm,drm_kms_helper[/FONT][/COLOR]
[COLOR=#000000]What does the number in the third column mean? It is the only thing that changed on one line - from 10 to 9.

I'll get around to testing this, but I fear the worst and lots of time and trouble getting things back to working and being able to work. My questions also have not be answered that I felt were needed to have answered before I started on this task.....[/COLOR]

I'd appreciate help understanding exactly what is meant below and if it would work/apply for my card. Above I gave the name of my card and it has also the name Tahiti [I guess for the model of GPU engine].

> [h=3]Enable Southern Islands (SI) and Sea Islands (CIK) support[/h]The [linux]("https://www.archlinux.org/packages/?name=linux") package enables AMDGPU support for cards of the Southern Islands (SI) and Sea Islands (CIK). When building or compiling a [kernel]("https://wiki.archlinux.org/index.php/Kernel"), CONFIG_DRM_AMDGPU_SI=Y and/or CONFIG_DRM_AMDGPU_CIK=Y should be be set in the config.
Even when AMDGPU support for SI/CIK has been enabled by the kernel, the [radeon]("https://wiki.archlinux.org/index.php/Radeon") driver may be used instead of the AMDGPU driver.
The following workarounds are available:

[LIST]
[*] Set amdgpu as first to load in the [Mkinitcpio#MODULES]("https://wiki.archlinux.org/index.php/Mkinitcpio#MODULES") array, e.g. MODULES="amdgpu radeon".
[*] [Blacklist]("https://wiki.archlinux.org/index.php/Blacklist") the radeon module.
[/LIST]
Also, since kernel 4.13, adding the amdgpu.si_support=1 radeon.si_support=0 or amdgpu.cik_support=1 radeon.cik_support=0 [kernel parameter]("https://wiki.archlinux.org/index.php/Kernel_parameter") is [required]("http://www.phoronix.com/scan.php?page=article&item=linux-413-gcn101&num=1"). Otherwise, AMDGPU will not start and you will end up with either radeon being used instead or the display being frozen during the boot. 


This and more details are from here: [https://wiki.archlinux.org/index.php/AMDGPU#Enable_early_KMS](https://wiki.archlinux.org/index.php/AMDGPU#Enable_early_KMS)

With much trepidation [because my questions were not answered] I blacklisted radeon and removed amdgpu from being blacklisted...however, my trepidation was for naught...the same thing happened. Both drivers are loaded in either case.

I'm curious about the above mentioned way to make amdgpu work for my tahiti radeon GPU.......

And I have NO idea why neither can be blacklisted.

---

### Post by dragonfly41 on 2017-11-29
Anything of relevance in here ... ?

[https://varunpriolkar.com/2016/12/how-to-use-amdgpu-driver-for-southern-islands-and-sea-islands-card-on-ubuntu-linux/](https://varunpriolkar.com/2016/12/how-to-use-amdgpu-driver-for-southern-islands-and-sea-islands-card-on-ubuntu-linux/)

---

### Post by mörgæs on 2017-11-29
With 16.04 giving so much trouble have you considered a live boot of 17.10 for comparison?

---

### Post by crazybear on 2017-11-30
> **mörgæs said:**
> With 16.04 giving so much trouble have you considered a live boot of 17.10 for comparison?

First, I ONLY use LTS versions of Ubuntu.
Second, I don't see the point. I'm waiting for 18.04, but that is six months away and would like to end the problems in 16.04.

> **dragonfly41 said:**
> Anything of relevance in here ... ?

[https://varunpriolkar.com/2016/12/how-to-use-amdgpu-driver-for-southern-islands-and-sea-islands-card-on-ubuntu-linux/](https://varunpriolkar.com/2016/12/how-to-use-amdgpu-driver-for-southern-islands-and-sea-islands-card-on-ubuntu-linux/)

Hmmm. Interesting, but for me a bit frightening. There is a lot of complexity and layers of things to do that would have to be undone if I had no working video. It is a little near the edge of my ability and comfort zone without help.

That said, I have added the ppa, but have not compiled the kernel in the manner they state...I guess I can't remain half pregnant...but I'm worried. For  you more experienced persons this would be a cake walk...for me, I need to be able to USE the computer and not just play with getting it working if something goes wrong.

I believe that if something goes horribly wrong I can just drop down to the next older kernel and boot until I get the current kernel fixed, no? I have NO idea about the options to choose on the menu for 'Graphics support' shown as a graphic on that page.

Please remember both drivers are loading. I see in this page a new way to blacklist a graphics driver:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splashmodprobe.blacklist=radeon"
 but before that [? after that ?] there are a LOT of steps that to me look drastic, and I'd not know how to undo them if I needed to.


Gulp! I'd need help step-by-step on this......I'm already in this too deep for my comfort.

---

### Post by dragonfly41 on 2017-11-30
It seems that the author of that article has created builds you might try ...

[https://cloud.priolkar.com/index.php/s/Ir7jwN2B5MEsGiL](https://cloud.priolkar.com/index.php/s/Ir7jwN2B5MEsGiL)



[Later edit]

I see that this article was referred to earlier in post #24.

---

### Post by crazybear on 2017-11-30
[QUOTE=dragonfly41;13716538]It seems that the author of that article has created builds you might try ...

[https://cloud.priolkar.com/index.php/s/Ir7jwN2B5MEsGiL](https://cloud.priolkar.com/index.php/s/Ir7jwN2B5MEsGiL)


Yes, that makes it easier, I think. Would anything else have to be done other than installing those .deb files?
Also, those are for 4.9 kernel and I now have 4.10.0-27. I think that makes that useless and the kernel would have to be built.
Once a new working kernel was especially built would that be incorporated into any newer versions as they were installed - or would one have to go through the entire process everytime one had a new kernel. Naive questions, I know...but I'm no expert on Ubuntu.
Also, no one seems to take in the ENTIRETY of my situation and worries. I still have both drivers loading. Will his 'other method' of blacklisting radeon driver work and when should it be done in the order of things. How would I undo all this  if it all fails?
I'm not a pro on dealing with these kinds of things and from past experience know I can be without a working computer for days or more while waiting for help to fix a messed up system. Will I always be able to load earlier kernels and work while I repair the latest one, if needed?

---

### Post by dragonfly41 on 2017-11-30
Really I have no personal experience in your environment.  I'm just offering ideas.
But If I were in your position I would create a LiveUSB 16.04 in a persistent flash drive (Try Ubuntu mode) for the express purpose of running experiments such as above.
In the LiveUSB I would install  Grub Customizer package to play with adding

[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splashmodprobe.blacklist=radeon"

Then in LiveUSB go through the steps in the article. Go through a new build as detailed.

This should be safe enough to try out.

I don't know if you would gain anything by leapfrogging into trying the Ubuntu 18.04 daily build.
This might unearth another can of worms but since others in this forum are using it I'm about to create a partition to try it.[/COLOR]

---

### Post by crazybear on 2017-11-30
OK, need HELP! OS won't boot at all. I'm in the OS with a liveCD - but I really don't know what to do [or what to undo]. I'm a bit in a panic as I need to work and that seems hours or days away now. How do I find the list of backups I made to the .conf file way back when? Is there a way to list the instructions given in terminal, so I can TRY to undo them all? I'm kind of lost and above my head in waters I don't know now.

---

### Post by QIII on 2017-11-30
Before you followed what I would consider to be a risky route, I was going to suggest simply replacing your original blacklist file, taking a step back and rethinking our approach.  I'm still not sure how both modules came to be installed in such a was as to have them both being loaded - that conflict likely causing your issues.  Now, unfortunately, your machine may be in a state so jumbled that it might be nigh impossible to sort out.

First question:  can you enter the "Advanced Options"/"Recovery Mode" mode through GRUB?

For instructions, see [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by crazybear on 2017-11-30
I really need HELP! I've never attempted to correct something using a live CD without detailed instructions. When I do something in terminal it is looking at the CD [I think] not the OS I got into. I can't find how to display the files in the OS - only in the CD...so I can't do much of anything and if I could have only a very vague idea of what I need to do. I could also do more damage than good. This is my work disk and need to work - I've been at this two hours and have made no progress and am sure this could take days for me without help. I'm lost.....

very strangely when I ran lsmod | grep amdgpu it gave nothing - making me think it was looking in the CD not the OS.
But when I ran lsmod | grep radeon is gave something that was a total surprise

```

root@ubuntu-gnome:/# lsmod | grep radeon
radeon               1515520  11
i2c_algo_bit           16384  1 radeon
ttm                   102400  1 radeon
drm_kms_helper        167936  1 radeon
drm                   368640  10 radeon,ttm,drm_kms_helper

```

but the OS won't load. It freezes at the log in screen. Even the mouse and keyboard won't work now.

For lsmod I got:

```


root@ubuntu-gnome:/# lsmod
Module                  Size  Used by
gpio_ich               16384  0
coretemp               16384  0
kvm_intel             192512  0
kvm                   598016  1 kvm_intel
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     45056  1
snd_hda_intel          36864  10
snd_hda_codec         135168  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_usb_audio         184320  2
snd_usbmidi_lib        32768  1 snd_usb_audio
uvcvideo               90112  0
snd_hda_core           86016  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  2 snd_hda_codec,snd_usb_audio
irqbypass              16384  1 kvm
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_pcm               110592  5 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hda_core,snd_hda_codec_hdmi
videobuf2_v4l2         24576  1 uvcvideo
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
snd_seq_midi           16384  0
ghash_clmulni_intel    16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
aesni_intel           167936  0
videodev              180224  3 uvcvideo,videobuf2_core,videobuf2_v4l2
snd_rawmidi            32768  2 snd_seq_midi,snd_usbmidi_lib
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
usblp                  20480  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
media                  40960  2 uvcvideo,videodev
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
snd_timer              32768  2 snd_seq,snd_pcm
glue_helper            16384  1 aesni_intel
snd                    86016  37 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_usb_audio,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_usbmidi_lib,snd_seq_device,snd_hda_codec_realtek,snd_pcm
joydev                 20480  0
input_leds             16384  0
ablk_helper            16384  1 aesni_intel
soundcore              16384  1 snd
serio_raw              16384  0
cryptd                 24576  3 ablk_helper,ghash_clmulni_intel,aesni_intel
lpc_ich                24576  0
i7core_edac            24576  0
intel_cstate           16384  0
shpchp                 36864  0
edac_core              53248  1 i7core_edac
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
aufs                  241664  5641
nls_utf8               16384  1
isofs                  40960  1
nls_iso8859_1          16384  1
dm_mirror              24576  0
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_mirror,dm_region_hash
uas                    24576  0
usb_storage            73728  3 uas
hid_generic            16384  0
usbhid                 53248  0
hid                   122880  2 hid_generic,usbhid
amdkfd                139264  1
amd_iommu_v2           20480  1 amdkfd
mxm_wmi                16384  0
radeon               1515520  11
i2c_algo_bit           16384  1 radeon
ttm                   102400  1 radeon
drm_kms_helper        167936  1 radeon
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
r8169                  81920  0
pata_acpi              16384  0
fb_sys_fops            16384  1 drm_kms_helper
mii                    16384  1 r8169
drm                   368640  10 radeon,ttm,drm_kms_helper
ahci                   36864  2
pata_jmicron           16384  1
libahci                32768  1 ahci
wmi                    16384  1 mxm_wmi
fjes                   28672  0


```

---

### Post by QIII on 2017-11-30
Let's see if we can get into recovery mode.  Go to the link I gave you.  Print it out.  Close the live session.  Remove the optical media.  Reboot.  Attempt to enter recovery mode.

Shut down.  Put the optical drive back in.  Boot to a live session and let us know if recovery mode works.

You can likely do what you need to do from a live session, but that may be more confusing for you.

---

### Post by crazybear on 2017-11-30
What surprised and upset me was, when the first kernel did not load, i had thought I could just drop down to the previous kernel and open it - that it was unchanged. But, every kernel displayed froze up in the exact same way. There are even older ones that don't display on the grub screen, but not sure how to make them display - some were hidden using grub-configuration or configure grub, forget now the name of the program.

Do I want to put back my old .config file or what do I want to do? Still lost....

I know how to get in to recovery mode...but in recovery mode if I go to 'drop to a terminal' [or whatever it is called], I still need to know what to do and I won't be able to see anything here. So before I do that, what kinds of things do I want to be doing?

Also, note that for some strange reason now only radeon is loading. If anything, I'd have thought that both would still be loading or if one amdgpu....but no,

Do I want to blacklist amdgpu now until I try to remove all new amdgpu 'things'? And what advantage is recovery mode. Here at least I can open internet and potentially find my files listed, but 'home' is home on the CD not home on the HD.

---

### Post by QIII on 2017-11-30
We will want to restore the blacklist configuration to its original state.  Had other things not been changed, that would have left us back where we started, no worse for the wear and we could have followed a different diagnostic path.  At this point, I have no idea what the state of your machine may be.  But let's start by restoring that file.  If you can get to the recovery mode it would be easier.

Hang tight for a bit.  Busy at work.  Work on a step-by-step for you.

---

### Post by dragonfly41 on 2017-11-30
I've just returned after a break.
Why has it got to this state?
My suggestion was to leave your work disk _untouched_ and just use a LiveUSB to experiment as a stand alone OS.
If the changes work _inside LiveUSB_ (or LiveCD) .. and **not** your work disk ..  the theory goes that you can later build on this experience on your work disk (which should be backed up incidentally).

Personally I don't see this as a risky route since your work disk is not being used.

But you seem to have read this as using LiveUSB (or LiveCD) to dive into your working disk to make changes.

Can you boot up LiveUSB and Try Ubuntu or not?

[P.S.] To avoid crossed lines I'll leave it to QIII to talk you through autopilot recovery mode.

[P.P.S] When you write "[COLOR=#000000]but the OS won't load" please clarify which OS you refer to .. (a) your work OS or (b) your LiveUSB OS.[/COLOR]

---

### Post by QIII on 2017-11-30
Warning!  Be very careful here.  You will be root while you do this and you can mess up your system every which way from Sunday.  You don't need to use sudo here because you are already root.

When you get to the recovery console, issue the following (Please cut and paste):

```
mount -o remount,rw /
```

This will take you to read/write mode so that you can make changes.

To restore your original blacklist file, issue

```
cp /etc/modprobe.d/blacklist.conf.whatever_you_named_the_backup /etc/modprobe.d/blacklist.conf
```

Then 

```
update-initramfs -u
```

Reboot.

This will preserve the backup copy of blacklist.conf, but also copy it over the top of the /etc/modprobe.d/blacklist.conf you modified before.  This, from the standpoint of what I asked you to do, will get you back to the original state.  This is why, when modifying system files, you should ALWAYS make a backup first.  We'll have to see first if that gets you booted and then see what we need to do to walk back whatever else you may have done if that is on your hard drive.

---

### Post by crazybear on 2017-11-30
> **QIII said:**
> We will want to restore the blacklist configuration to its original state.  Had other things not been changed, that would have left us back where we started, no worse for the wear and we could have followed a different diagnostic path.  At this point, I have no idea what the state of your machine may be.  But let's start by restoring that file.  If you can get to the recovery mode it would be easier.

Hang tight for a bit.  Busy at work.  Work on a step-by-step for you.

I had already done that before you suggested it. Neither driver is blacklisted now. As far as timing, I'm in Europe and I think you are PST - you are 9 hours earlier, so I'll be going to sleep when you are having lunch.....but if you leave a list of things to try I'll do them in the morning. 

Yes, I can get in recovery mode, but I HATE the tty1 terminal there and can't I do all the same here?
When in recovery mode I first went to networking, then to repair broken packages. It wanted to download three new xorg files. I didn't do it nor did I write down exactly what they were. I believe they are the new xorg files suggested in one of those urls on making my tahiti GPU work with amdgpu.

> **dragonfly41 said:**
> I've just returned after a break.
Why has it got to this state?
My suggestion was to leave your work disk _untouched_ and just use a LiveUSB to experiment as a stand alone OS.
If the changes work _inside LiveUSB_ (or LiveCD) .. and **not** your work disk ..  the theory goes that you can later build on this experience on your work disk (which should be backed up incidentally).

Personally I don't see this as a risky route since your work disk is not being used.

But you seem to have read this as using LiveUSB (or LiveCD) to dive into your working disk to make changes.

Can you boot up LiveUSB and Try Ubuntu or not?

[P.S.] To avoid crossed lines I'll leave it to QIII to talk you through autopilot recovery mode.

[P.P.S] When you write "[COLOR=#000000]but the OS won't load" please clarify which OS you refer to .. (a) your work OS or (b) your LiveUSB OS.[/COLOR]

I didn't go that route because I 1] don't know how to / never have before made a LiveUSB 2] and don't have a spare one of that size handy. While more trouble, perhaps, I ONLY went to live CD after the computer stopped loading at the boot screen. There were at least four persons making suggestions - some of them I was aware of were antithetical to other suggestions. In the end, I had to decide and I decided wrong...such is the world of those who are not experts in Ubuntu.

My Ubuntu 16.04.2 won't load. It freezes up on the login screen and at that point even the mouse and keyboard stop working. All I can do is a hard shut-down. It was then I went to a liveCD to try to undo some damage...but realized I didn't really know much what to do and couldn't make a list of terminal commands I had done to see what needed un-doing.

---

### Post by dragonfly41 on 2017-11-30
Tip: To see history of all terminal commands run ..
```
history
```
I'm in Windows right now.

---

### Post by crazybear on 2017-11-30
> **QIII said:**
> Warning!  Be very careful here.  You will be root while you do this and you can mess up your system every which way from Sunday.  You don't need to use sudo here because you are already root.

When you get to the recovery console, issue the following (Please cut and paste):

```
mount -o remount,rw /
```

This will take you to read/write mode so that you can make changes.

To restore your original blacklist file, issue

```
cp /etc/modprobe.d/blacklist.conf.whatever_you_named_the_backup /etc/modprobe.d/blacklist.conf
```

Then 

```
update-initramfs -u
```

Reboot.

This will preserve the backup copy of blacklist.conf, but also copy it over the top of the /etc/modprobe.d/blacklist.conf you modified before.  This, from the standpoint of what I asked you to do, will get you back to the original state.  This is why, when modifying system files, you should ALWAYS make a backup first.  We'll have to see first if that gets you booted and then see what we need to do to walk back whatever else you may have done if that is on your hard drive.

I can't cut and paste in recovery mode. I can see nothing from this forum or anything but the tty1 screen.
I actually would have to see a list of my files to remember what I renamed the file. I remember adding three letters before bak - but don't remember what they were. I thought there might already be a .bak file I'd overwrite - in hindsight I should have written it down. Learning the HARD way. how do I see the list of those files to remember what I changed it to?
I manually changed the blacklist, but now you say there are two, so I'm a bit confused. 
Can't I do all the above from here with the live CD? Any advantage to doing it in recovery mode..I'd have to print this out above and copy it carefully by eye and one eye is NOT good [awaiting an eye operation as a matter of fact]....but if need be I can do so constantly changing two pair of glasses....another reason I'd rather stay on liveCD - and I can post here and see posts here. At some point tomorrow I'll have to try another disk with another OS [an old 12.04] just to be able to do my work and answer emails etc. if this is not working, but I'll follow this forum and when I have some hours free come back to what looks like a few days work.

---

### Post by QIII on 2017-11-30
I realize you won't be able to see the forum from the terminal.  I suppose in this case you will have to either print the instructions out or have another machine handy to type manually, but be careful.

To paste in the terminal, you must use CTRL+SHIFT+V.

Whether you do this from the Live session or not, you will still have to do it in the terminal.

To find out what you named the backup file, go back in to the recovery mode, mount rw as before, issue

```
cd /etc/modprobe.d
```

and then

```
dir
```

This will list the files in that directory.

I have a specific notebook and always keep notes of what I do so that I can backtrack -- or jot down something learned.

(By the way, as a greybeard I wear trifocals, so i know how that goes.)

---

### Post by crazybear on 2017-11-30
OK,  I'm in 12.04 [an ooold disk like this ooold guy] and put the 16.04 in the computer and found what I renamed the file.
I'll do as suggested, but I have to tell you that at somepoint a day ago I remember seeing the computer installing new software connected to amdgpu - I'm almost sure. I did NOT specifically tell it to, but I had put in the ppa [now removed again] suggested for my Tahiti GPU with amdgpu [which seemed already to be installed]. Strangely, now, it seems not to be loading - I can only guess it is so messed up, though there, it doesn't load. Also, I hadn't mentioned it before, but will now....when I had amdgpu blacklisted [or radeon blacklisted] despite still loading I never had a crash.....so I think in some strange way, I'm now reverting back to a more unstable situation. Yes, now I remember that 'history' is the command for the terminal history, but that is commands I typed in...I think we need to know what programs were added or updated. How do I do that?

---

### Post by dragonfly41 on 2017-11-30
> [COLOR=#000000]"I think we need to know what programs were added or updated. How do I do that?"[/COLOR][COLOR=#000000]

This is what I do ..
[/COLOR]Install Synaptic
```
sudo apt-get install synaptic
```

Launch Synaptic Package Manager

System Tools > Administration > Synaptic Package Manager

File > History

Navigate to date to see packages installed.

However that will only be useful in your previous 16.04 kernel, not in Ubuntu 12.04 which is a fresh start.

[Later edit]

There are more tips here .. using command line

[https://askubuntu.com/questions/680410/how-to-view-history-of-apt-get-install](https://askubuntu.com/questions/680410/how-to-view-history-of-apt-get-install)

From your Live session navigate to your 16.04 file system ..

```
[COLOR=#111111][FONT=Consolas]grep " install " /var/log/dpkg.log
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]history | grep "apt-get install"
```[/FONT][/COLOR]

---

### Post by crazybear on 2017-11-30
> **dragonfly41 said:**
> [COLOR=#000000]

This is what I do ..
[/COLOR]Install Synaptic
```
sudo apt-get install synaptic
```

Launch Synaptic Package Manager

System Tools > Administration > Synaptic Package Manager

File > History

Navigate to date to see packages installed.

However that will only be useful in your previous 16.04 kernel, not in Ubuntu 12.04 which is a fresh start.

[Later edit]

There are more tips here .. using command line

[https://askubuntu.com/questions/680410/how-to-view-history-of-apt-get-install](https://askubuntu.com/questions/680410/how-to-view-history-of-apt-get-install)

From your Live session navigate to your 16.04 file system ..

```
[COLOR=#111111][FONT=Consolas]grep " install " /var/log/dpkg.log
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]history | grep "apt-get install"[/FONT][/COLOR]
```

synaptic was installed, but I can't get into the program or OS directly. I'll try the later edit method you mention.

One additional thing. I'm not as stupid as I seem...though fairly Ubuntu-naive, I admit. I do have a 16.04 clone. I'm on it now. It was cloned two months ago. So, I have all the the old files and programs I had two months ago - along with all the crashing here. I usually do clones more often, but things have been hectic. If anyone can see a use of the clone - either a way to move all things from the other current as of this morning disk [which I think has the same uuid] to here minus the chaotic new things - or use this one to get the other back to status quo, let me know. I know how to move some things, but not all. I last ran aptik on the one that is now crashed several weeks ago. Perhaps for now it is best to leave this one as is. I have just updated the software and will move some files I know how to move here - no program files. However, the other clone is two months more complex and up to date [in good ways other than the mistakes of the last days]. This one would be a lot of work to get up to date - but is here if needed and the other one fails completely.

This is frustrating in the extreme and taking me HOURS. I can NOT type anything in recovery mode terminal. Period.
with live CD many times I'm in 16.04 and then suddenly I'm not and it is looking into the CD. I don't know why.
I was working on my clone 16.04 this morning and it crashed [no surprise there] after abut two hours...and that is what I'm told to return to?
My system was much more stable after blacklisting amdgpu - for whatever strange reason. If I could change the UUID of this newer 16.04 and move the program information onto the clone, that would be the easier route. I have spent hours endlessly getting back into 16.04 [non-clone].
and here I go one more time to try to get history and packages installed recently.......
very frustrating. I'm about ready to live with crashes for six months.

> **crazybear said:**
> I can't cut and paste in recovery mode. I can see nothing from this forum or anything but the tty1 screen.
I actually would have to see a list of my files to remember what I renamed the file. I remember adding three letters before bak - but don't remember what they were. I thought there might already be a .bak file I'd overwrite - in hindsight I should have written it down. Learning the HARD way. how do I see the list of those files to remember what I changed it to?
I manually changed the blacklist, but now you say there are two, so I'm a bit confused. 
Can't I do all the above from here with the live CD? Any advantage to doing it in recovery mode..I'd have to print this out above and copy it carefully by eye and one eye is NOT good [awaiting an eye operation as a matter of fact]....but if need be I can do so constantly changing two pair of glasses....another reason I'd rather stay on liveCD - and I can post here and see posts here. At some point tomorrow I'll have to try another disk with another OS [an old 12.04] just to be able to do my work and answer emails etc. if this is not working, but I'll follow this forum and when I have some hours free come back to what looks like a few days work.

done

This is twilight zone stuff ...I NEVER installed or even thought of installing fglrx!!!!!! If I did it was years ago when I first installed 16.04 before I knew fglrx didn't work with it.. Below is NOT the full install log [I believe] and I don't understand why.

```

# grep " install " /var/log/dpkg.log
2017-11-01 16:56:21 install skype:i386 <none> 4.3.0.37-1
2017-11-01 17:12:35 install skypeforlinux:amd64 <none> 5.3.0.1
2017-11-03 06:18:30 install skypeforlinux:amd64 <none> 8.9.0.1
2017-11-05 18:08:59 install aptik:amd64 <none> 17.10-0~201711011237~ubuntu16.04.1
2017-11-21 06:53:20 install linux-image-4.10.0-40-generic:amd64 <none> 4.10.0-40.44~16.04.1
2017-11-21 06:53:22 install linux-image-extra-4.10.0-40-generic:amd64 <none> 4.10.0-40.44~16.04.1
2017-11-21 06:53:27 install linux-headers-4.10.0-40:all <none> 4.10.0-40.44~16.04.1
2017-11-21 06:53:30 install linux-headers-4.10.0-40-generic:amd64 <none> 4.10.0-40.44~16.04.1
2017-11-23 06:55:34 install rxvt-unicode:amd64 <none> 9.21-1build1
2017-11-23 06:56:28 install rxvt-unicode-256color:amd64 <none> 9.21-1build1
2017-11-23 06:57:39 install rxvt-unicode-lite:amd64 <none> 9.21-1build1
2017-11-23 06:59:14 install rxvt-unicode-256color:amd64 9.21-1build1 9.21-1build1
2017-11-25 06:34:28 install libqwt6abi1:amd64 <none> 6.1.2-5
2017-11-25 06:34:29 install libsphinxbase3:amd64 <none> 0.8+5prealpha-2ubuntu1
2017-11-25 06:34:29 install libpocketsphinx3:amd64 <none> 0.8.0+real5prealpha-1ubuntu2
2017-11-25 06:34:29 install libqaccessibilityclient0:amd64 <none> 0+git20140203-0ubuntu2
2017-11-25 06:34:29 install simon-data:all <none> 0.4.1-0ubuntu9
2017-11-25 06:34:32 install simon:amd64 <none> 0.4.1-0ubuntu9
2017-11-25 06:37:43 install jovie:amd64 <none> 4:15.12.3-0ubuntu1
2017-11-25 06:37:43 install kmouth:amd64 <none> 4:15.12.3-0ubuntu1
2017-11-30 08:03:29 install xserver-xorg-core:amd64 <none> 2:1.18.4-0ubuntu0.7
2017-11-30 08:03:33 install xserver-xorg-video-amdgpu:amd64 <none> 1.1.2-0ubuntu0.16.04.1
2017-11-30 09:39:17 install libdrm-common:all <none> 2.4.85-5~x~padoka0
2017-11-30 09:39:19 install libllvm5.0:i386 <none> 1:5.0-1~gd~x
2017-11-30 09:39:23 install libllvm5.0:amd64 <none> 1:5.0-1~gd~x
2017-11-30 09:39:27 install libomxil-bellagio-bin:amd64 <none> 0.9.3-3ubuntu1
2017-11-30 09:39:27 install libomxil-bellagio0:amd64 <none> 0.9.3-3ubuntu1
root@ubuntu-gnome:/# history | grep "apt-get install"
   54  sudo apt-get install dselect
   66  apt-get install aptik
   76  apt-get install dist-upgrade
  122  apt-get install openimageio-tools
  131  apt-get install dist-upgrade
  151  sudo apt-get install fglrx-updates
  152  sudo apt-get install fglrx-updates-core
  155  sudo apt-get install fglrx-updates
  156  sudo apt-get install fglrx-updates-core
  157  sudo apt-get install fglrx-amdcccle-updates
  161  sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
  184  sudo apt-get install "fglrx.*"
  191  sudo apt-get install "fglrx.*"
  221  sudo apt-get install -f
  223  sudo apt-get install dist-upgrade
  235  history | grep "apt-get install"


```

to me this also looks incomplete as to things I did install - very! and certainly seems not to include things the update intstaller installed.

I made a very big mistake in only following a suggestion rather than doing my own thinking. I should have just run 'history' and shown the last week. My mistake...but it takes 30 min. to get back into that and I'm on another disk now...I'll do that later. Asking only for the history of apt-gt install I think will miss a lot of what happened....it also can NOT be all of the times I used apt-get install...it is far far too few listed and most from long, long ago [years ago].

---

### Post by dragonfly41 on 2017-12-01
Groundhog day.

Unfortunately the default output of history command does not show the date/time stamp of each line.

For your historical reference to future terminal commands (not past commands) you can follow advice here to set date/time stamps on history.

[https://stackoverflow.com/questions/38526588/linux-command-history-with-date-and-time](https://stackoverflow.com/questions/38526588/linux-command-history-with-date-and-time)

[FONT=arial]```
[COLOR=#242729]echo 'export HISTTIMEFORMAT="%d/%m/%y %T "' >> ~/.bash_profile
[/COLOR]source ~/.bash_profile
```[/FONT]

---

### Post by crazybear on 2017-12-01
Oh, yes, forgot.....replaced the old .conf files.....it doesn't boot up. Freezes at the same place as before [log in screen]. It is obviously very messed up.

Next steps? lsmod? other? end of full history? Suggestions?

Thanks.

N.B. Anyone using 18.04 yet? And if so, is it at all stable? Work with AMD? Would I receive updates or would I endlessly have to update it manually - I've never tried a pre-release daily build. I'm pretty sure I'm better off waiting six months on 18.04. I should have just left things as they were a few days into this...it was more stable and possibly stable...then I went and messed it up with all the various suggestions and possibilities. Pffft!

I don't know how to move all the good and new things on the now dead OS over to the working old clone. I could use grsync, but what switches to use / not use and what folders to move and not move? Alternatively, can someone help me try to get the old OS up and running again. This old clone won't really make it. I need a lot of the information in the other. They have the same UUID. I could change the UUID on the newer disk, but then I'd have to do more to have it operate [I believe I know how to do all that with a live CD]. 

However, I do NOT now how to diagnose and then repair that drive. I'd like to have this all done by monday so I can work. Ideas? Suggestions?
While this may give me - one way or the other - a working and updated drive again, i still have not solved the original problem....but first to get back my OS fully working and updated. I make a LOT of changes in 2.5 months!

---

### Post by dragonfly41 on 2017-12-01
You are up to your neck in an alligator pit.
I hesitate to offer advice which might aggravate your position.

As I understand you now have 16.04 clone working from two months ago and a 16.04  OS which does not work after recent changes/suggestions.

One approach would be to compare old (reference point) with new (not working) to focus on the changes which need to be unwound.

There is a package named meld in Ubuntu software centre. This allows you to look at differences between old and new.

You can compare folders or files.  This assumes that both old and new can be mounted.

The following suggestion is at your own discretion.

So start by installing meld in your 16.04 two month clone which presumably you can boot up.

```
sudo apt-get install meld
```

Read here to get a handle on using meld.

[https://www.howtoforge.com/tutorial/beginners-guide-to-visual-merge-tool-meld-on-linux/](https://www.howtoforge.com/tutorial/beginners-guide-to-visual-merge-tool-meld-on-linux/)


We will dive straight into comparing the /etc/modprobe.d/  folders in 

the old 16.04
the non working 16.04

Launch Meld window.

Under New comparison are
File comparison
Directory comparison
Version control view

Click on Directory Comparison

Drop down menus are seen 

(None) .. under File comparison

(None) .. under Directory comparison

(None) .. under Version control view


Click on the first (None) and from the menu select Other .. at bottom of menu.

In the Window “Select First Folder” click on “+ Other Locations” and navigate to (for example) the /etc/modprobe.d/  folder in the old 16.04.
For the active OS look inside “Computer”.


Now in Meld window go to the next (None) and go through the same motions to select /etc/modprobe.d folder in the crashing 16.04


You should now see “modprobe.d” selected in both dropdowns (just make sure that they are from old and later OS).

Do not click on 2-way comparison.

Now click on Compare button ...

You will see a comparison of files in old and later modprobe.d folders.

Click on any file to view comparisons line by line.

From this workflow you might be able to unwind changes.

I have just run through this workflow myself comparing a recent 16.04 configuration with an older 16.04 configuration in an external drive.

> [COLOR=#000000]They have the same UUID[/COLOR]

This suggests to me that you are **not** mounting these two drives together but you are physically swapping them in and out.  If that is the case then the Meld ideas above will not work for you.   Do you have a USB drive container into which you can place the non working drive?   My second OS is connected via USB port.

Some further tips found when exploring "rollback" of installed packages

[https://askubuntu.com/questions/56095/how-i-do-a-system-restore](https://askubuntu.com/questions/56095/how-i-do-a-system-restore)

In particular this reminded me to install etckeeper which is version control of files in /etc

The etckeeper git is installed in /etc/.git so you need to turn on view hidden files in /etc.

This might give you more control over your future changes.

[https://help.ubuntu.com/lts/serverguide/etckeeper.html](https://help.ubuntu.com/lts/serverguide/etckeeper.html)

---

### Post by crazybear on 2017-12-02
All good suggestions. Thanks. Some small progress. Now, on the 'new disk' it is only the newest kernel that won't boot. It also will not load recovery mode on that kernel. I dropped down one kernel and it loaded - and seemed to almost normally - there was a brief flash of color not usually there before the normal desktop appeared. Is there a way to delete that newest and broken kernel and then the system should update and install it again - one would hope properly. Is it likely that whatever changes I made only apply to that kernel? I will explore further and see how things look in the older kernel and how stable that is....do some diagnostic look arounds and report back in a while.

So, best I can figure out all looks OK and so far [only two hours] as stable as before having dropped down one kernel. The newest kernel is totally messed up and I'd like to remove it, then have the system install it...BUT in synaptic if I ask it to mark for removal linux-image-4.10.0.40-generic [the newest and messed up], it also says to be removed: the hwe-16.04 and I don't want to remove that and don't think that was giving me my problems. In fact I had update the hwe to solve problems I had had before.

What to do? Anyway, perhaps from here I can repair the newest kernel?

I tried re-installing the bad kernel...but it reinstalled it such that it reacts the same as before [not working]. I don't understand why that is.
Also, the only thing that seems to be wrong in the one-down one-older kernel [which wasn't true when it was the highest kernel] is I have a three monitor system and the positions of the three, as well as what is placed on which is scrambled in a very odd way. Trying to fix that now..but still have no way to fix the bad newest kernel.

Well, at least I can do my normal work now, but things are still NOT good, at all. The most recent kernel is kaput and I dare not remove it and re-installing left it the same.

---

### Post by dragonfly41 on 2017-12-02
Following tips picked up from links I posted in post #77
I decided to try out TimeKeeper to keep snapshots which can be rolled back.

[http://www.teejeetech.in/p/timeshift.html](http://www.teejeetech.in/p/timeshift.html)

sudo apt-add-repository -y ppa:teejee2008/ppa
sudo apt-get update
sudo apt-get install timeshift

Also, since installing etckeeper, for each "apt run" I can now see changes committed to /etc/.git

This is a useful discipline.

In searching around I also found some commands which will scan through the entire file system and print out files changed during last 2 months or so.
This approach might help your diagnosis.

---

### Post by crazybear on 2017-12-02
> **dragonfly41 said:**
> Following tips picked up from links I posted in post #77
I decided to try out TimeKeeper to keep snapshots which can be rolled back.

[http://www.teejeetech.in/p/timeshift.html](http://www.teejeetech.in/p/timeshift.html)

sudo apt-add-repository -y ppa:teejee2008/ppa
sudo apt-get update
sudo apt-get install timeshift

Also, since installing etckeeper, for each "apt run" I can now see changes committed to /etc/.git

This is a useful discipline.

In searching around I also found some commands which will scan through the entire file system and print out files changed during last 2 months or so.
This approach might help your diagnosis.

These are really great for the future, but what about fixing my OS now?
I don't understand why the system wants to uninstall the new hwe if I try to delete the latest kernel. It does NOT want to uninstall hwe if I wanted to uninstall any older kernel. So, if I were to wait not many days or weeks for a yet newer kernel, would it incorporate the 'bad' things in the the current most recent kernel or not [I have no idea how that works]. I also can't understand the moving of the monitors. I physically moved the monitors to make them correct again, but if I go to another OS [and I have others] the monitors will be wrong - but software would not let me move the monitors and I don't know what configuration file handles them or the syntax. The monitor issue is secondary now.

The primary question is can I 1] fix or 2] delete the latest kernel [which doesn't load and is a mess] or not? If I move this working kernel up to the top of the grub list so that it loads automatically, what will happen when a new kernel is released and automatically installed? 

Thanks for the suggestions to keep tabs on things in the future, however.

---

### Post by dragonfly41 on 2017-12-02
> BUT in synaptic if I ask it to mark for removal linux-image-4.10.0.40-generic [the newest and messed up], it also says to be removed: the hwe-16.04 and I don't want to remove that

I'm *guessing* here, with no experience in hwe, but if I were gambling I would just uninstall/purge then with a fresh kernel reinstall hwe as I read here.

[https://askubuntu.com/questions/887123/can-i-switch-to-hwe-kernel-after-installation](https://askubuntu.com/questions/887123/can-i-switch-to-hwe-kernel-after-installation)

---

### Post by crazybear on 2017-12-02
> **dragonfly41 said:**
> I'm *guessing* here, with no experience in hwe, but if I were gambling I would just uninstall/purge then with a fresh kernel reinstall hwe as I read here.

[https://askubuntu.com/questions/887123/can-i-switch-to-hwe-kernel-after-installation](https://askubuntu.com/questions/887123/can-i-switch-to-hwe-kernel-after-installation)

But why is it 'associated' only with the newest kernel. Removing older kernels synaptic will not remove hwe. I don't understand the 'logic' the software is using. I like to understand before I do something; it seems to avoid mis-steps. I guess I can remove all and then reinstall, but don't like removing so much at one time and making such a big change. It listed about eight things it was going to remove.

OK, now I begin to understand. [https://askubuntu.com/questions/944842/kernel-4-10-in-ubuntu-16-04-3-update](https://askubuntu.com/questions/944842/kernel-4-10-in-ubuntu-16-04-3-update) shows that the hwe-16.04 is connected to the 4.10 kernel - and that makes sense. But I now have several 4.10 kernels and only removing the latest one will remove the hwe-16.04. But, aren't all my 4.10 kernels built to use that hwe-16.04? So, will they be rebuilt to work without it automatically?

After removal of the [? only] broken kernel, I'm then faced again with the original decisions and problems: reinstall hwe-16.04 and how to make it compatable with a Tahiti GPU as mentioned here [https://wiki.archlinux.org/index.php/AMDGPU#Enable_early_KMS](https://wiki.archlinux.org/index.php/AMDGPU#Enable_early_KMS) and other places...or suffer endless crashes and blurry monitors for another six months.

If hwe-16.04 is removed, will the normal stack that comes with 16.04 be put in - or will I have to put it in before I have a system that won't boot?
I still don't understand why only the latest 4.10 kernel's removal removes hwe-16.04. It was put in with a much earlier version of 4.10, so shouldn't they all be built on that? I'm very hesitant to do anything for fear it will make things worse.

On the program that can compare two disks, as I can't have them both in the computer at the same time, I don't see how I can apply it. Anyhow, in what folders would I look for changes if I could. There must be almost 100 GB of changes in the two disks [most not in the OS obviously].

---

### Post by dragonfly41 on 2017-12-03
I will attempt to answer both paragraphs.

**[para 1]**
I decided to try the joys of installing kernel 4.10.0-40-generic plus hwe trappings.
I am on Dell Inspiron 3268 with earlier releases of kernel working - 4.4.0-101-generic
and some fallback kernels.

After installing 4.10.0 with hwe, at boot I selected Ubuntu Advanced Settings and chose 4.10.0.
At login there were obvious problems seen in desktop.  So I decided to shutdown and go back to the stable 4.4.0 kernel.

I opened Synaptic Package Manager to view the newly installed packages by searching "hwe".

i read here ..

[http://ubuntuhandbook.org/index.php/2017/02/install-remove-enablement-stacks-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2017/02/install-remove-enablement-stacks-ubuntu-16-04/)

that uninstalling hwe stack also uninstalls ubuntu-desktop and xorg.

So after uninstalling hwe you need to _immediately_ reinstall ubuntu-desktop. 
That is, do not shutdown until you have reinstalled ubuntu-desktop.

I decided to use Synaptic Package Manager and removed the hwe stack via Synaptic and not the command line.
I noted a list of these hwe packages if needed for reference.

After removing hwe stack I tried to reboot into 4.10 kernel (with hwe removed) but I did not see the login dialogue, only Ubuntu screen with logo.
I ran Ctrl+F1 to get into terminal and ran the command "startx".
This got me to the desktop but menubars were missing and clearly my Dell 3268 was not working with 4.10 kernel (sans hwe).

I had to launch command terminal and ran the command "shutdown" which shuts down after 2 minutes.

Back into 4.4.0 kernel and now back to normal.
Hopefully this experiment will give you more information on how to remove hwe stack.

I could not get it to work on my Dell 3268.

**[para2]**
I did comment in earlier post that meld will not work when you are swapping out drives.  They _both_ need to be mounted. Look back at what was written.
You can only compare your problem drive with your working drive if you purchase a drive container to allow drive1 (internal) to be compared with drive2 (external container via USB port).   While on a buying spree purchase a SanDisk flashdrive so that you can run experiments in future on a LiveUSB.

Perhaps if you run this command and post results we can look at your configuration.

```
lsblk -o +label,PARTLABEL
```

In my case I have sda (the internal drive), and sdb (the external drive)
Partitions are numbered sda1, sda2 ... sdb1, sdb2 .. etc.


[P.S.]
Tip when you get around to using Meld.
Compare directory by directory, or sub-directory by sub-directory
and turn off "view matching files" since then you can focus on differences.


[Correction]
After removing HWE, at first I could not boot into 4.10 desktop as explained above.  For some reason I lost the cursor.
But I seem to have overcome this teething problem and I now have 4.10 kernel (without HWE) running on Dell 3268.

---

### Post by crazybear on 2017-12-04
I haven't seen anything in the many searched I've done about desktop also be removed if one removes hwe-16.04 and synaptic did NOT list that as about to be also removed....so I'm a little skeptical.

I have a very large, high capacity desktop this is on.

Before I tried anything on the bad newer disk, I wanted to try to get the updated materal to the working old clone. I finally thought I have figured out a way. Using grsync I move the entire Home and /etc [separately] to a data drive I emptied and reformated. It all came to about 300GB and I'm using 2TB drives. I asked [I thought] grsync to overwrite the home on the good old clone [to update everything]. Did this ONLY with Home, NOT /etc - as that could cause problems and had that there if I wanted to move specific things later.

However, although I can NOT find out what is going on, my drive which when full with all the new data should be no more than half full [1TB], it was showing getting up to 96% full, and I stopped the operation. I have installed and used various file size programs that show relative use of the disk. Sadly none show empty space. I can't figure out if the report on 95% full by system monitor is NOT correct - or somehow now there are two folders of everything [if the later, I have searched and searched and found NONE]. I don't  know what is going on and know that a disk shouldn't be pushed beyond about 80% full. I'm at a loss. I don't have a spare 3 or larger disk to use. This is turning into a nightmare. If that all had or will go well, then I'd feel a bit more relaxed to try the drastic changes in the other disk.

I don't see how I'm going to get around to using meld unless I change the UUID.

With all the problems you had removing hwe-16.04, I'd like to avoid that...if only I can get the new home to write over the home on this drive. It should work, but seems not to be - or at least is not reported to be. Also, a few folders on desktop are locked and never were on either drive...but that is minor at this moment. I'm exhausted and in a PANIC as I can not work on what I must work on for five days now...only messing around with this mess.

---

### Post by dragonfly41 on 2017-12-04
@crazybear

You might be skeptical but I know what I experienced.  I had to reinstall ubuntu-desktop after purging hwe but if you do forget you can still do that by logging into terminal after booting.

Here is my record of HWE packages I had installed .. and then removed ..

linux-generic-hwe-16.04
linux-header-generic-hwe-16.04
linux-image-generic-hwe-16.04
xserver-xorg-core-hwe
xserver-xorg-hwe-16.04
xserver-xorg-input-all-hwe-16.04
xserver-xorg-input-evdev-hwe-16.04
xserver-xorg-input-synaptics-hwe-16.04
xserver-xorg-input-wacom-hwe-16.04
xserver-xorg-legacy-hwe-16.04
xserver-xorg-video-all-hwe-16.04
xserver-xorg-video-amdgpu-hwe-16.04
xserver-xorg-video-ati-hwe-16.04
xserver-xorg-video-fbdev-hwe-16.04
xserver-xorg-video-intel-hwe-16.04
xserver-xorg-video-nouveau-hwe-16.04
xserver-xorg-video-qxl-hwe-16.04
xserver-xorg-video-radeon-hwe-16.04
xserver-xorg-video-vesa-hwe-16.04
xserver-xorg-video-vmware-hwe-16.04


Now when I search &#8220;hwe&#8221; I see no matches in Synaptic Package Manager. And my desktop is working.

I found the reason for losing my cursor because I had at one time dual monitors and my cursor disappeared off screen to the right.

Now I just have 4.10.0 kernel working without incident.

...

When using grsync it is prudent to try a &#8220;dry run&#8221; first,
There are two buttons in grsync top bar.
The one to the far right which executes the run and the other &#8220;i&#8221; which executes a dry run.

Remember that you will have hidden files to copy.

In your position I would have tried copying some sub-folders first rather than the entire /home folder.

Read up how to use an exclusion file with grsync.

[COLOR=#0000ff][P.S.] In grsync File > Preferences enable logging.[/COLOR]

...

I agree that without the physical setup suggested (both drives connected) there is no benefit in using Meld.

...

You seem to be in a perilous position with no backup if your &#8220;clone&#8221; should go belly up.

...

Post output of ..

lsblk -o +label,PARTLABEL

---

### Post by crazybear on 2017-12-04
Can anyone help me figure out what is filling my HDD or making it look like it is. I've tried many programs and nothing seems a problem. I've looked in folders and there are no visible double copies of files [nor doubled folders]...so how could 1TB of information produce 2TB on the drive>!>!. I thought I was almost done and now I have another disk that really is not usable....but it is still running and perhaps can be solved. Then I will try some more dangerous things on the other drive and whichever one is the better, clone it. Now, most I need to figure out why the disk is full, when it should be only half full!

---

### Post by dragonfly41 on 2017-12-04
System Tools > Disk Usage Analyser will show visually where disk is used.
Hover mouse over pie charts in right window.

---

### Post by dragonfly41 on 2017-12-04
Some possibilities ...

[https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not](https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not)

[https://askubuntu.com/questions/321753/df-h-thinks-my-drive-is-full-but-it-shouldnt-even-be-half-way-cant-inst](https://askubuntu.com/questions/321753/df-h-thinks-my-drive-is-full-but-it-shouldnt-even-be-half-way-cant-inst)

[https://serverfault.com/questions/275206/disk-full-du-tells-different-how-to-further-investigate](https://serverfault.com/questions/275206/disk-full-du-tells-different-how-to-further-investigate)

From .. google search pattern .. "ubuntu disk full when it should be half full"

---

### Post by crazybear on 2017-12-04
> **dragonfly41 said:**
> Some possibilities ...

[https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not](https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not)

[https://askubuntu.com/questions/321753/df-h-thinks-my-drive-is-full-but-it-shouldnt-even-be-half-way-cant-inst](https://askubuntu.com/questions/321753/df-h-thinks-my-drive-is-full-but-it-shouldnt-even-be-half-way-cant-inst)

[https://serverfault.com/questions/275206/disk-full-du-tells-different-how-to-further-investigate](https://serverfault.com/questions/275206/disk-full-du-tells-different-how-to-further-investigate)

From .. google search pattern .. "ubuntu disk full when it should be half full"
None of the above. I found the problem, but am at a total loss for a solution - even difficult here to describe. What frightens me though is that with every step I've made to try to fix the problem, I've come a step closer to making it worse. grsync is too powerful for me to use. It does things I never expected it too. In a second session I added the /etc folder, but it has a mind of its own and started a new session with a new name for my disk [called data transfer]. It renamed the first run as Data Transfer1 and the next as Data Transfer [I had assumed it would place it in Data Transfer as I had instructed it to and it said it was going to do to the eye reading the from and to].
So when I hit Home - it is there [with some strange locked folders - not all, but too many], but if I go up/back further up there is another Home! Thus there being twice the number of files. But, because the OS for Ubuntu and even the program that draws the pie charts never expects this, it shows only one of everything - but there are two of everything nested. I'm not very comfortable as to how to delete the half I don't need, nor even if it is possible. As I was running the grsync last night [now aware and able to control that monster] the computer  crashed [the original problem that started this entire mess] due to gpu panic of some kind. I just went to bed disheartened. I'm a bit at a loss. Maybe I'll forget the grsync - it doesn't work without a lot of careful planning if an intermediary disk is being used. I might use that intermediary disk to clone the bad updated drive and then attempt to remove and reinstall on one clone. But this is one step forward, two back and all the time I'm really hardly able to work and when I work I am afraid my new work will get lost on one disk or the other and I get confused. What a mess. Something I thought might take hours, then days is turning into weeks. And there is no answer yet to the original problem and I'm not even dealing with that now....I'm fighting to undo new problems I created. If anyone understands the problem with nested Home's and how one would tell the computer to delete the second one, let me know. Somehow I think it can't easily be done [perhaps can't be done at all]. That would make this disk I'm on now back to where I started in one command. I realize it is hard to even describe and I can't find any program that will show visually the nested homes. But, if I keep moving back deeper into the file system I can see it. If I chose 'Home' via the 'places' it chooses the lower nested one, not the uppermost one - making it look as if there were only one, but there are clearly two - I can even see the differences and the lower one has in every case one less file in it. Exhausting and a lesson I'll never forget.

---

### Post by dragonfly41 on 2017-12-05
I suspect that you did not use closing slashes in your grsync session ...   source and destination ... resulting in nested home > home

[http://qdosmsq.dunbar-it.co.uk/blog/2013/02/rsync-to-slash-or-not-to-slash/](http://qdosmsq.dunbar-it.co.uk/blog/2013/02/rsync-to-slash-or-not-to-slash/)

[https://serverfault.com/questions/529287/rsync-creates-a-directory-with-the-same-name-inside-of-destination-directory](https://serverfault.com/questions/529287/rsync-creates-a-directory-with-the-same-name-inside-of-destination-directory)

In grsync, Basic Options, click on the [COLOR=#008080]**[?]**[/COLOR] button next to Source Destination to read help on trailing slashes.

Too late now to remind you to always try a dry run and enable logging.

You might see more in Disk Usage app by running .. sudo baobab

---

### Post by crazybear on 2017-12-05
> **dragonfly41 said:**
> I suspect that you did not use closing slashes in your grsync session ...   source and destination ... resulting in nested home > home

[http://qdosmsq.dunbar-it.co.uk/blog/2013/02/rsync-to-slash-or-not-to-slash/](http://qdosmsq.dunbar-it.co.uk/blog/2013/02/rsync-to-slash-or-not-to-slash/)

[https://serverfault.com/questions/529287/rsync-creates-a-directory-with-the-same-name-inside-of-destination-directory](https://serverfault.com/questions/529287/rsync-creates-a-directory-with-the-same-name-inside-of-destination-directory)

In grsync, Basic Options, click on the [COLOR=#008080]**[?]**[/COLOR] button next to Source Destination to read help on trailing slashes.

Too late now to remind you to always try a dry run and enable logging.

You might see more in Disk Usage app by running .. sudo baobab

Thanks! I'm learning a LOT through all this....for 'next time'.....

---

### Post by crazybear on 2017-12-05
I'm holding my breath, but I may just have fixed the WHOLE mess! PFFFT! It will take some hours or days to know, but right now...this computer is stable, looking just fine, working just fine too!

I gave up on the grsync - but thanks for the pointers [for some other time]. I made a clone of the messed-up, but updated drive...just in case.

I then took the clone and uninstalled the hwe-16.04 packages [and it wasn't easy nor pretty]...kept telling me it couldn't do this or that due to broken packages. I kept working at fixing them using various strategies. Then I reinstalled all with

```

[COLOR=#333333][FONT=monospace] sudo apt-get install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04

```

checked for broken packages - none
held my breath and rebooted - and it rebooted fine!

I won't mark this as solved for a few days...but maybe, just maybe....wow! what a trip...and steep learning curve!

So the 4.10.0-40 that was totally messed-up is what I'm using now and it is purring along just fine so far [only been up for about 20 min though]....

even fixed the strange right two screens of three that had somehow switched on their own in the process.

Thanks all for your help and suggestions. Sorry I was so upset and negative...it is positively horrible when one has no working computer or one that was missing two and a half months of work and files. Gonna set up a regular backup on the morrow!

Will let all know how this goes. In theory it should not work without special work building the kernel, as my Tahiti AMD GPU is not supposed to be supported with this stack...but some say it does and some say it doesn't with theirs. If I start having crashes again [and that may be likely], I'll try that special whoo-haa I pointed to somewhere above in this loooong thread. I'll keep a clone cloned until things are stable. In doing this, I noticed I had the hwe-16.04 packages installed but NOT the xorg-16.04 packages. Now they are. Testing, one, two, three....[/FONT][/COLOR]

---

### Post by dragonfly41 on 2017-12-05
> So when I hit Home - it is there [with some strange locked folders - not all, but too many], but if I go up/back further up there is another Home!

Trying to think through how to unwind your state.
I think I can see what you might have done.

In your HOME folder you will see a folder which is the name you use to LOGIN ( e.g. crazybear).
Use a File Manager such as Nautilus or Thunar to view your file system.

But if you have copied another HOME folder using grsync without trailing slashes I believe that you will see an apparent false second user by name HOME.

home >
---- crazybear
---- home             << copied by using incorrect grsync command
      
If you do see this then it should be a matter of deleting the sub folder named "home" (not the parent folder).

And after deleting clear TRASH bin.

But please double check this theory before taking any action.
Following same line of thought you might have a folder** /etc** INSIDE the parent folder **/etc**.

One useful command to search for folder names (not file names) is ...

find / -xdev 2>/dev/null -name "foldername" 

[http://www.omgubuntu.co.uk/2017/09/finding-files-in-command-line](http://www.omgubuntu.co.uk/2017/09/finding-files-in-command-line)

find <where to start searching> <search criteria> <actions to take>

,,,

So try ... ```
[COLOR=#000000]find / -xdev 2>/dev/null -name "home"
```
and wait while it searches .. might take some minutes to complete search.[/COLOR]

---

### Post by crazybear on 2017-12-06
I haven't looked into the double Home situation yet - that is on the too full disk. On the other disk, however, I just had the usual crash that was the reason for starting this thread....so 8 pages in I'm back to where I started and obviously my GPU doesn't work with this configuration. The problem is what is the best way to move forward to get it to work well or as best as possible until 18.04 [hopefully] will address this issue. I have a clone of this version [I really need the disks for something else, but for now I am using them for this]. One is a fast disk, one a slow disk. The slow disk doesn't crash as often, but is annoying slow - I usually use it for the clone, not for working on...but the fast disk crashes almost immediately after I start the session. I don't think the situation would be different on the drive with two home folders, or only slightly different. The recipe for making my GPU compatible with amdgpu looks VERY complex to me, someone would have to help me do that. I can't follow the instructions, it assumes I know things I don't. Going back to before 4.10 and hwe I also had problems, that is why I added them. The only difference now from before [or the disk with the two homes] is this has an updated xorg-hwe-16.04 which I thought was supposed to be installed with the hwe-16.04. Maybe that makes things worse. Any ideas? I've got lots of disks with 16.04 on them - too many, in fact.......

---

### Post by dragonfly41 on 2017-12-06
In recent months I moved some development to google cloud.
I don't know if you could offload some of your private research work
onto a google cloud VM. At least until you get your local system to work and/or 18.04 arrives.

[https://cloud.google.com/gpu/](https://cloud.google.com/gpu/)

Google has a free tier option for experimenting. 
 It uses command line extensively so this would be another steep learning curve.

Meanwhile I will be trying to get 18.04 daily build up and running.

[P.S.}

I read also that Amazon offers AMD GPU in the cloud.

[https://venturebeat.com/2017/09/12/amd-works-with-amazon-to-create-virtualized-graphics-in-the-cloud/](https://venturebeat.com/2017/09/12/amd-works-with-amazon-to-create-virtualized-graphics-in-the-cloud/)

---

### Post by crazybear on 2017-12-07
Sorry, but for reasons I can't go into I can not, and never will be able to, use a cloud *anything* - Google least of all. The nature of what I do and a cloud server do NOT go together - quite the opposite - and that would be the biggest security breach I could EVER make. So thanks, but that is out. The slower drive is being quite stable at the moment. I'm trying to tweek it a bit, and then will clone again the faster drive. This drive works OK, but things load slowly sometimes, close slowly, etc. Strangely, when I boot up if I leave it to boot automatically, I get a tty1 screen, yet if I simply make it display all the kernels and choose the one at the top [which should be the choice made automatically], it boots up fine. That is a small annoyance. If 18.04 is running and supports my GPU, and will automatically be updated if I had it, I might try it. I've never tried using a distribution before its release and don't know how much trouble that usually involves. I was surprised that the faster drive crashed. I'd think maybe a faster processor might compound the gpu 'panic', but not a faster drive...but of these things I do not claim to know much. I have a very fast PSU and GPU and usually use the fast drives [not SSD], but the slower one with this configuration is doing better just now. Will try the fast drive tomorrow, but all this switching makes my head spin - as I have to move off new files to the other via a USB drive and I might forget something.

---

### Post by crazybear on 2017-12-08
OK, I couldn't use a cloud anyway even if I didn't have security issues, as they charge for that. I'm not well off. 
Anyway, some good news. I have stabilized the fast disk. I seem to have the GPU panic and crash only [on average] every few days. Not great...but where it was before. Intense use of graphics, yes, can prompt the crash, but not in any very predictable way.
Everything is updated. Now, I have to decide and move carefully to either remove one of the drivers and/or build that special kernel for my GPU...or live with constant crashes for six more months. I have a clone of this disk and will keep it updated every few days, so I don't loose new data or any new good changes to the OS...and if the changes are bad, I have that as a back-up minus a few days work. [which I try to keep in a USB drive]. Any ideas? Remember that back at the beginning of this thread I tried to blacklist each of the two drivers individually, but both still loaded, as is the case now. Originally, I added the hwe-16.04 as I read after some research that it was a better alternative in most [not all] cases where and AMD GPU was having problems [and mine was with just the radeon - the problem was not this kind of crash, but one or two monitors [of three] sometimes going wavy and the only way to cure that was to reboot - sometimes reboot a few times.

---

### Post by rbmorse on 2017-12-08
While I've skimmed all eight pages of this thread I might have missed a detailed description of your hardware suite, beyond the ATI HD7950 graphics adapter.  You did mention that your motherboard predates support for UEFI.  If your motherboard and power supply are of the same vintage as the graphics adapter, it leads me to wonder if the otherwise unexplained crashes and GPU panic might be age-related hardware issues? 

In particular, the voltage regulators on motherboard and in the power supply and video adapter are subject to heat-related degradation over time.  When their performance migrates out to the ragged edge of the specification envelope they can produce symptoms as you have described and other mysterious, often spurious and unexplained behavior that doesn't produce logged events.  Would also be consistent with your report that the system was working fine until one day it wasn't.  Hardware can do that to you. 

If you get a chance could you list your motherboard, CPU and power supply make and model and the approximate length of time they have been in service?

---

### Post by crazybear on 2017-12-08
> **rbmorse said:**
> While I've skimmed all eight pages of this thread I might have missed a detailed description of your hardware suite, beyond the ATI HD7950 graphics adapter.  You did mention that your motherboard predates support for UEFI.  If your motherboard and power supply are of the same vintage as the graphics adapter, it leads me to wonder if the otherwise unexplained crashes and GPU panic might be age-related hardware issues? 

In particular, the voltage regulators on motherboard and in the power supply and video adapter are subject to heat-related degradation over time.  When their performance migrates out to the ragged edge of the specification envelope they can produce symptoms as you have described and other mysterious, often spurious and unexplained behavior that doesn't produce logged events.  Would also be consistent with your report that the system was working fine until one day it wasn't.  Hardware can do that to you. 

If you get a chance could you list your motherboard, CPU and power supply make and model and the approximate length of time they have been in service?

Gigabyte GA-X58A-UD7 ver. 1 MB - about 7 years
Intel i7-995-X CPU - about 3 years
Seasonic 1200W Platinum PSU - about two years
24 GB Corsair DDR3 1600 SDRAM - about 3 years
All HDD are WD Black or Gold...one is Green [clone]

I'm not sure there are not logged events. There are lots of indications of problems with the video software and/or hardware 'screaming' and then collapsing. Strangely....after the screen goes black, after about one minute a very pretty screen comes on with a nice artistic pattern on all monitors and the time of the crash - nothing more....but that is helpful I look at the log and sure enough at that time and for some seconds or milliseconds before there are repeated messages that scream PROBLEM...some samples I gave at the beginning of this long thread...but I could give more extensive ones, if needed. True, I am not able to read exactly what the problem is from those logs....perhaps they 'say', but I just can't understand what it is reporting. The MB is not the newest, but was top notch when purchased. I watch heat very closely and nothing gets very hot. GPU max at 46C; everything else less to much less; CPU rarely over 40C max for a few microseconds; usually idles at 24-27C; PSU fan doesn't even go on as it never gets hot. MB temp. about 35-37C. I also have Ubuntu 12.04 which I don't use, but have...and Win7 which I use once every few months. Each OS is on its own disk and I don't remember either of them crashing. I also had a Ubuntu 14.04, but it went strange [no connection to internet - which I've not bothered to solve yet]...it also never crashed. It used flgrx as did 12.04 and Win7 the AMD windows drivers....making me think it is unlikely to be the hardware. True I now almost exclusively use the 16.04 after the 14.04 wouldn't connect to internet [about four months ago]...but then it didn't crash and 16.04 did from the get go. How often it crashes has varied and is not linear and I have not seen any pattern I can report. Is there a way to better interpret the [to me] incomprehensible log entries?

---

### Post by dragonfly41 on 2017-12-09
More reading here ...

[ https://wiki.ubuntu.com/X/Troubleshooting/Freeze]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze")

[http://odm.ubuntu.com/](http://odm.ubuntu.com/)

---

### Post by crazybear on 2017-12-09
Just had a crash. Trying to post logs that might hint at the problem...never before looked at this /var/log/xorg.0.log file...it keeps saying can't loadt modules 'ati', 'fbdev' and 'vesa'. fbdev is a frambuffer and xorg driver.

```

   266.698] (--) Log file renamed from "/var/log/Xorg.pid-23784.log" to "/var/log/Xorg.0.log"
[   266.698] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[   266.698] X Protocol Version 11, Revision 0
[   266.698] Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
[   266.698] Current Operating System: Linux peterandcrazybear-GA-X58A-UD7 4.10.0-40-generic #44~16.04.1-Ubuntu SMP Thu Nov 9 15:37:44 UTC 2017 x86_64
[   266.698] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-40-generic root=UUID=5658d31c-d367-4eec-9c41-99d79307e8cd ro recovery nomodeset
[   266.698] Build Date: 13 October 2017  01:57:05PM
[   266.698] xorg-server 2:1.18.4-0ubuntu0.7 (For technical support please see http://www.ubuntu.com/support) 
[   266.698] Current version of pixman: 0.33.6
[   266.698]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   266.698] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   266.698] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 30 18:17:16 2017
[   266.698] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   266.698] (==) No Layout section.  Using the first Screen section.
[   266.698] (==) No screen section available. Using defaults.
[   266.698] (**) |-->Screen "Default Screen Section" (0)
[   266.698] (**) |   |-->Monitor "<default monitor>"
[   266.698] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   266.698] (==) Automatically adding devices
[   266.698] (==) Automatically enabling devices
[   266.698] (==) Automatically adding GPU devices
[   266.698] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   266.698] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   266.698]     Entry deleted from font path.
[   266.698] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   266.698]     Entry deleted from font path.
[   266.698] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   266.698]     Entry deleted from font path.
[   266.698] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    built-ins
[   266.698] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   266.698] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   266.698] (II) Loader magic: 0x55dd615f7dc0
[   266.698] (II) Module ABI versions:
[   266.699]     X.Org ANSI C Emulation: 0.4
[   266.699]     X.Org Video Driver: 20.0
[   266.699]     X.Org XInput driver : 22.1
[   266.699]     X.Org Server Extension : 9.0
[   266.699] (++) using VT number 7


[   266.700] (II) systemd-logind: took control of session /org/freedesktop/login1/session/c505
[   266.702] (--) PCI:*(0:3:0:0) 1002:6798:1002:3000 rev 0, Mem @ 0xe0000000/268435456, 0xfb480000/262144, I/O @ 0x00007e00/256, BIOS @ 0x????????/131072
[   266.702] (II) LoadModule: "glx"
[   266.702] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   266.703] (II) Module glx: vendor="X.Org Foundation"
[   266.703]     compiled for 1.18.4, module version = 1.0.0
[   266.703]     ABI class: X.Org Server Extension, version 9.0
[   266.703] (==) AIGLX enabled
[   266.703] (==) Matched ati as autoconfigured driver 0
[   266.703] (==) Matched modesetting as autoconfigured driver 1
[   266.703] (==) Matched fbdev as autoconfigured driver 2
[   266.703] (==) Matched vesa as autoconfigured driver 3
[   266.703] (==) Assigned the driver to the xf86ConfigLayout
[   266.703] (II) LoadModule: "ati"
[   266.703] (WW) Warning, couldn't open module ati
[   266.703] (II) UnloadModule: "ati"
[   266.703] (II) Unloading ati
[   266.703] (EE) Failed to load module "ati" (module does not exist, 0)
[   266.703] (II) LoadModule: "modesetting"
[   266.703] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   266.703] (II) Module modesetting: vendor="X.Org Foundation"
[   266.703]     compiled for 1.18.4, module version = 1.18.4
[   266.703]     Module class: X.Org Video Driver
[   266.703]     ABI class: X.Org Video Driver, version 20.0
[   266.703] (II) LoadModule: "fbdev"
[   266.703] (WW) Warning, couldn't open module fbdev
[   266.703] (II) UnloadModule: "fbdev"
[   266.703] (II) Unloading fbdev
[   266.703] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   266.703] (II) LoadModule: "vesa"
[   266.704] (WW) Warning, couldn't open module vesa
[   266.704] (II) UnloadModule: "vesa"
[   266.704] (II) Unloading vesa
[   266.704] (EE) Failed to load module "vesa" (module does not exist, 0)
[   266.704] (==) Matched ati as autoconfigured driver 0
[   266.704] (==) Matched modesetting as autoconfigured driver 1
[   266.704] (==) Matched fbdev as autoconfigured driver 2
[   266.704] (==) Matched vesa as autoconfigured driver 3
[   266.704] (==) Assigned the driver to the xf86ConfigLayout
[   266.704] (II) LoadModule: "ati"
[   266.704] (WW) Warning, couldn't open module ati
[   266.704] (II) UnloadModule: "ati"
[   266.704] (II) Unloading ati
[   266.704] (EE) Failed to load module "ati" (module does not exist, 0)
[   266.704] (II) LoadModule: "modesetting"
[   266.704] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   266.704] (II) Module modesetting: vendor="X.Org Foundation"
[   266.704]     compiled for 1.18.4, module version = 1.18.4
[   266.704]     Module class: X.Org Video Driver
[   266.704]     ABI class: X.Org Video Driver, version 20.0
[   266.704] (II) UnloadModule: "modesetting"
[   266.704] (II) Unloading modesetting
[   266.704] (II) Failed to load module "modesetting" (already loaded, 0)
[   266.704] (II) LoadModule: "fbdev"
[   266.704] (WW) Warning, couldn't open module fbdev
[   266.704] (II) UnloadModule: "fbdev"
[   266.704] (II) Unloading fbdev
[   266.704] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   266.704] (II) LoadModule: "vesa"
[   266.704] (WW) Warning, couldn't open module vesa
[   266.704] (II) UnloadModule: "vesa"
[   266.704] (II) Unloading vesa
[   266.704] (EE) Failed to load module "vesa" (module does not exist, 0)
[   266.704] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   266.704] (EE) open /dev/dri/card0: No such file or directory
[   266.704] (EE) open /dev/dri/card0: No such file or directory
[   266.704] (WW) Falling back to old probe method for modesetting
[   266.704] (EE) open /dev/dri/card0: No such file or directory
[   266.704] (EE) open /dev/dri/card0: No such file or directory
[   266.704] (EE) Screen 0 deleted because of no matching config section.
[   266.704] (II) UnloadModule: "modesetting"
[   266.704] (EE) Screen 0 deleted because of no matching config section.
[   266.704] (II) UnloadModule: "modesetting"
[   266.704] (EE) Device(s) detected, but none match those in the config file.
[   266.704] (EE) 
Fatal server error:
[   266.704] (EE) no screens found(EE) 
[   266.704] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   266.704] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   266.704] (EE) 
[   266.705] (EE) Server terminated with error (1). Closing log file.


```

This person has a very similar GPU and somewhat similar problems [https://bbs.archlinux.org/viewtopic.php?id=229332](https://bbs.archlinux.org/viewtopic.php?id=229332)

```

$ dmesg | grep radeon
[    1.096514] [drm] radeon kernel modesetting enabled.
[    1.101409] fb: switching to radeondrmfb from VESA VGA
[    1.101790] radeon 0000:03:00.0: VRAM: 3072M 0x0000000000000000 - 0x00000000BFFFFFFF (3072M used)
[    1.101791] radeon 0000:03:00.0: GTT: 2048M 0x00000000C0000000 - 0x000000013FFFFFFF
[    1.101853] [drm] radeon: 3072M of VRAM memory ready
[    1.101853] [drm] radeon: 2048M of GTT memory ready.
[    1.109552] [drm] radeon: dpm initialized
[    1.152110] radeon 0000:03:00.0: WB enabled
[    1.152112] radeon 0000:03:00.0: fence driver on ring 0 use gpu addr 0x00000000c0000c00 and cpu addr 0xffff9e6eb96a3c00
[    1.152113] radeon 0000:03:00.0: fence driver on ring 1 use gpu addr 0x00000000c0000c04 and cpu addr 0xffff9e6eb96a3c04
[    1.152114] radeon 0000:03:00.0: fence driver on ring 2 use gpu addr 0x00000000c0000c08 and cpu addr 0xffff9e6eb96a3c08
[    1.152115] radeon 0000:03:00.0: fence driver on ring 3 use gpu addr 0x00000000c0000c0c and cpu addr 0xffff9e6eb96a3c0c
[    1.152116] radeon 0000:03:00.0: fence driver on ring 4 use gpu addr 0x00000000c0000c10 and cpu addr 0xffff9e6eb96a3c10
[    1.152409] radeon 0000:03:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc0a3c8235a18
[    1.172399] radeon 0000:03:00.0: fence driver on ring 6 use gpu addr 0x00000000c0000c18 and cpu addr 0xffff9e6eb96a3c18
[    1.172400] radeon 0000:03:00.0: fence driver on ring 7 use gpu addr 0x00000000c0000c1c and cpu addr 0xffff9e6eb96a3c1c
[    1.172403] radeon 0000:03:00.0: radeon: MSI limited to 32-bit
[    1.172429] radeon 0000:03:00.0: radeon: using MSI.
[    1.172448] [drm] radeon: irq initialized.
[    3.500370] fbcon: radeondrmfb (fb0) is primary device
[    3.500538] radeon 0000:03:00.0: fb0: radeondrmfb frame buffer device
[    3.518573] [drm] Initialized radeon 2.49.0 20080528 for 0000:03:00.0 on minor 0


```

```

$ sudo lshw -c video
[sudo] password for peter-and-crazybear: 
  *-display               
       description: VGA compatible controller
       product: Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:44 memory:e0000000-efffffff memory:fb480000-fb4bffff ioport:7e00(size=256) memory:c0000-dffff

```

```

[    1.101853] [drm] radeon: 3072M of VRAM memory ready
[    1.101853] [drm] radeon: 2048M of GTT memory ready.
[    1.101858] [drm] Loading tahiti Microcode
[    1.101933] [drm] Internal thermal controller with fan control
[    1.101975] [drm] probing gen 2 caps for device 8086:340e = 393d02/0
[    1.109552] [drm] radeon: dpm initialized
[    1.110894] [drm] Found VCE firmware/feedback version 50.0.1 / 17!
[    1.110900] [drm] GART: num cpu pages 524288, num gpu pages 524288
[    1.111924] [drm] probing gen 2 caps for device 8086:340e = 393d02/0
[    1.111926] [drm] PCIE gen 2 link speeds already enabled
[    1.127415] scsi host4: ahci
[    1.127870] scsi host5: ahci
[    1.128293] scsi host6: ahci
[    1.128519] scsi host7: ahci
[    1.128802] scsi host8: ahci
[    1.129045] scsi host9: ahci
[    1.129088] ata5: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc100 irq 38
[    1.129090] ata6: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc180 irq 38
[    1.129091] ata7: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc200 irq 38
[    1.129092] ata8: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc280 irq 38
[    1.129093] ata9: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc300 irq 38
[    1.129094] ata10: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc380 irq 38
[    1.129259] ahci 0000:01:00.0: AHCI 0001.0000 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    1.129261] ahci 0000:01:00.0: flags: 64bit ncq sntf led only pmp fbs pio slum part sxs 
[    1.129264] ahci 0000:01:00.0: port 0 is not capable of FBS
[    1.129296] ahci 0000:01:00.0: port 1 is not capable of FBS
[    1.129556] scsi host10: ahci
[    1.129772] scsi host11: ahci
[    1.129812] ata11: SATA max UDMA/133 abar m2048@0xfb6ff000 port 0xfb6ff100 irq 41
[    1.129813] ata12: SATA max UDMA/133 abar m2048@0xfb6ff000 port 0xfb6ff180 irq 41
[    1.129866] ahci 0000:04:00.0: controller can do FBS, turning on CAP_FBS
[    1.139054] r8169 0000:09:00.0 eth3: renamed from eth1
[    1.140079] ahci 0000:04:00.0: AHCI 0001.0200 32 slots 8 ports 6 Gbps 0xff impl SATA mode
[    1.140082] ahci 0000:04:00.0: flags: 64bit ncq fbs pio 
[    1.140861] scsi host12: ahci
[    1.141107] scsi host13: ahci
[    1.141382] scsi host14: ahci
[    1.141822] scsi host15: ahci
[    1.142091] scsi host16: ahci
[    1.142259] scsi host17: ahci
[    1.142443] scsi host18: ahci
[    1.142545] scsi host19: ahci
[    1.142590] ata13: SATA max UDMA/133 abar m2048@0xfbeff000 port 0xfbeff100 irq 42
[    1.142592] ata14: SATA max UDMA/133 abar m2048@0xfbeff000 port 0xfbeff180 irq 42
[    1.142594] ata15: SATA max UDMA/133 abar m2048@0xfbeff000 port 0xfbeff200 irq 42
[    1.142596] ata16: SATA max UDMA/133 abar m2048@0xfbeff000 port 0xfbeff280 irq 42
[    1.142598] ata17: SATA max UDMA/133 abar m2048@0xfbeff000 port 0xfbeff300 irq 42
[    1.142599] ata18: SATA max UDMA/133 abar m2048@0xfbeff000 port 0xfbeff380 irq 42
[    1.142601] ata19: SATA max UDMA/133 abar m2048@0xfbeff000 port 0xfbeff400 irq 42
[    1.142603] ata20: SATA max UDMA/133 abar m2048@0xfbeff000 port 0xfbeff480 irq 42
[    1.151982] [drm] PCIE GART of 2048M enabled (table at 0x00000000001D6000).
[    1.152110] radeon 0000:03:00.0: WB enabled
[    1.152112] radeon 0000:03:00.0: fence driver on ring 0 use gpu addr 0x00000000c0000c00 and cpu addr 0xffff9e6eb96a3c00
[    1.152113] radeon 0000:03:00.0: fence driver on ring 1 use gpu addr 0x00000000c0000c04 and cpu addr 0xffff9e6eb96a3c04
[    1.152114] radeon 0000:03:00.0: fence driver on ring 2 use gpu addr 0x00000000c0000c08 and cpu addr 0xffff9e6eb96a3c08
[    1.152115] radeon 0000:03:00.0: fence driver on ring 3 use gpu addr 0x00000000c0000c0c and cpu addr 0xffff9e6eb96a3c0c
[    1.152116] radeon 0000:03:00.0: fence driver on ring 4 use gpu addr 0x00000000c0000c10 and cpu addr 0xffff9e6eb96a3c10
[    1.152409] radeon 0000:03:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc0a3c8235a18
[    1.152790] ahci 0000:05:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.152792] ahci 0000:05:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.153193] scsi host20: ahci
[    1.153436] scsi host21: ahci
[    1.153494] ata21: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe100 irq 17
[    1.153497] ata22: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe180 irq 17
[    1.153571] ahci 0000:06:00.0: controller can do FBS, turning on CAP_FBS
[    1.163787] ahci 0000:06:00.0: AHCI 0001.0200 32 slots 8 ports 6 Gbps 0xff impl SATA mode
[    1.163788] ahci 0000:06:00.0: flags: 64bit ncq fbs pio 
[    1.164917] scsi host22: ahci
[    1.165166] scsi host23: ahci
[    1.165339] scsi host24: ahci
[    1.165582] scsi host25: ahci
[    1.165708] scsi host26: ahci
[    1.165872] scsi host27: ahci
[    1.166021] scsi host28: ahci
[    1.166245] scsi host29: ahci
[    1.166287] ata23: SATA max UDMA/133 abar m2048@0xfbcff000 port 0xfbcff100 irq 43
[    1.166289] ata24: SATA max UDMA/133 abar m2048@0xfbcff000 port 0xfbcff180 irq 43
[    1.166291] ata25: SATA max UDMA/133 abar m2048@0xfbcff000 port 0xfbcff200 irq 43
[    1.166293] ata26: SATA max UDMA/133 abar m2048@0xfbcff000 port 0xfbcff280 irq 43
[    1.166295] ata27: SATA max UDMA/133 abar m2048@0xfbcff000 port 0xfbcff300 irq 43
[    1.166296] ata28: SATA max UDMA/133 abar m2048@0xfbcff000 port 0xfbcff380 irq 43
[    1.166298] ata29: SATA max UDMA/133 abar m2048@0xfbcff000 port 0xfbcff400 irq 43
[    1.166300] ata30: SATA max UDMA/133 abar m2048@0xfbcff000 port 0xfbcff480 irq 43
[    1.166409] ahci 0000:07:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.166411] ahci 0000:07:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.166640] scsi host30: ahci
[    1.166707] scsi host31: ahci
[    1.166739] ata31: SATA max UDMA/133 abar m8192@0xfbbfe000 port 0xfbbfe100 irq 19
[    1.166741] ata32: SATA max UDMA/133 abar m8192@0xfbbfe000 port 0xfbbfe180 irq 19
[    1.172399] radeon 0000:03:00.0: fence driver on ring 6 use gpu addr 0x00000000c0000c18 and cpu addr 0xffff9e6eb96a3c18
[    1.172400] radeon 0000:03:00.0: fence driver on ring 7 use gpu addr 0x00000000c0000c1c and cpu addr 0xffff9e6eb96a3c1c
[    1.172402] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.172402] [drm] Driver supports precise vblank timestamp query.
[    1.172403] radeon 0000:03:00.0: radeon: MSI limited to 32-bit
[    1.172429] radeon 0000:03:00.0: radeon: using MSI.
[    1.172448] [drm] radeon: irq initialized.
[    1.248458] ata1.01: HPA detected: current 976764911, native 976773168
[    1.248460] ata1.01: ATA-8: WDC WD5000AAKB-00H8A0, 05.04E05, max UDMA/133
[    1.248461] ata1.01: 976764911 sectors, multi 0: LBA48 
[    1.254515] ata1.01: configured for UDMA/100
[    1.254919] scsi 0:0:1:0: Direct-Access     ATA      WDC WD5000AAKB-0 4E05 PQ: 0 ANSI: 5
[    1.333995] [drm] ring test on 0 succeeded in 1 usecs
[    1.334000] [drm] ring test on 1 succeeded in 1 usecs
[    1.334004] [drm] ring test on 2 succeeded in 1 usecs
[    1.334012] [drm] ring test on 3 succeeded in 3 usecs
[    1.334018] [drm] ring test on 4 succeeded in 3 usecs
[    1.441421] ata5: SATA link down (SStatus 0 SControl 300)
[    1.445985] ata12: SATA link down (SStatus 0 SControl 330)
[    1.456245] ata13: SATA link down (SStatus 0 SControl 300)
[    1.457585] ata15: SATA link down (SStatus 0 SControl 300)
[    1.457862] ata18: SATA link down (SStatus 0 SControl 300)
[    1.458165] ata20: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.458193] ata16: SATA link down (SStatus 0 SControl 300)
[    1.458237] ata19: SATA link down (SStatus 0 SControl 300)
[    1.458284] ata17: SATA link down (SStatus 0 SControl 300)
[    1.458311] ata14: SATA link down (SStatus 0 SControl 300)
[    1.458323] ata20.00: ATAPI: MARVELL VIRTUALL, 1.09, max UDMA/66
[    1.458540] ata20.00: configured for UDMA/66
[    1.473687] ata22: SATA link down (SStatus 0 SControl 300)
[    1.474592] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[    1.481544] ata23: SATA link down (SStatus 0 SControl 300)
[    1.481750] ata31: SATA link down (SStatus 0 SControl 300)
[    1.481846] ata26: SATA link down (SStatus 0 SControl 300)
[    1.481872] ata28: SATA link down (SStatus 0 SControl 300)
[    1.481936] ata29: SATA link down (SStatus 0 SControl 300)
[    1.481969] ata24: SATA link down (SStatus 0 SControl 300)
[    1.485800] ata30: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.485827] ata27: SATA link down (SStatus 0 SControl 300)
[    1.485868] ata25: SATA link down (SStatus 0 SControl 300)
[    1.485870] ata32: SATA link down (SStatus 0 SControl 300)
[    1.486021] ata30.00: ATAPI: MARVELL VIRTUALL, 1.09, max UDMA/66
[    1.486269] ata30.00: configured for UDMA/66
[    1.509697] [drm] ring test on 5 succeeded in 2 usecs
[    1.509700] [drm] UVD initialized successfully.
[    1.606585] ata11: SATA link up 6.0 Gbps (SStatus 133 SControl 330)
[    1.607092] ata11.00: HPA detected: current 5860524911, native 5860533168
[    1.607184] ata11.00: ATA-9: WDC WD3003FZEX-00Z4SA0, 01.01A01, max UDMA/133
[    1.607185] ata11.00: 5860524911 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.607831] ata11.00: configured for UDMA/133
[    1.618879] [drm] ring test on 6 succeeded in 19 usecs
[    1.618888] [drm] ring test on 7 succeeded in 3 usecs
[    1.618888] [drm] VCE initialized successfully.
[    1.619073] [drm] ib test on ring 0 succeeded in 0 usecs
[    1.619097] [drm] ib test on ring 1 succeeded in 0 usecs
[    1.619119] [drm] ib test on ring 2 succeeded in 0 usecs
[    1.619142] [drm] ib test on ring 3 succeeded in 0 usecs
[    1.619163] [drm] ib test on ring 4 succeeded in 0 usecs
[    1.638601] ata21: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.639233] ata21.00: ATA-9: WDC WD3003FZEX-00Z4SA0, 01.01A01, max UDMA/133
[    1.639234] ata21.00: 5860533168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.639952] ata21.00: configured for UDMA/133
[    1.651657] usb 3-1: New USB device found, idVendor=e0ff, idProduct=0002
[    1.651658] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.651659] usb 3-1: Product: G3
[    1.651660] usb 3-1: Manufacturer: A.....
[    1.658006] hidraw: raw HID events driver (C) Jiri Kosina
[    1.664822] usbcore: registered new interface driver usbhid
[    1.664823] usbhid: USB HID core driver
[    1.667648] input: A..... G3 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/0003:E0FF:0002.0001/input/input3
[    1.667816] hid-generic 0003:E0FF:0002.0001: input,hidraw0: USB HID v1.00 Mouse [A..... G3] on usb-0000:00:1a.0-1/input0
[    1.670753] input: A..... G3 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.1/0003:E0FF:0002.0002/input/input4
[    1.698594] usb 6-2: new full-speed USB device number 2 using uhci_hcd
[    1.735030] hid-generic 0003:E0FF:0002.0002: input,hiddev0,hidraw1: USB HID v1.00 Keyboard [A..... G3] on usb-0000:00:1a.0-1/input1
[    1.786815] sd 0:0:1:0: Attached scsi generic sg0 type 0
[    1.786854] sd 0:0:1:0: [sda] 976764911 512-byte logical blocks: (500 GB/466 GiB)
[    1.786862] sd 0:0:1:0: [sda] Write Protect is off
[    1.786863] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    1.786871] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.797132]  sda: sda1
[    1.797134] sda: p1 size 976769024 extends beyond EOD, enabling native capacity
[    1.797218] ata1: soft resetting link
[    1.882647] usb 6-2: New USB device found, idVendor=1b1c, idProduct=1b11
[    1.882650] usb 6-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.882652] usb 6-2: Product: Corsair K95 RGB Gaming Keyboard 
[    1.882654] usb 6-2: Manufacturer: Corsair
[    1.882655] usb 6-2: SerialNumber: 11016031AE3D8C805397856EF5001945
[    1.889859] input: Corsair Corsair K95 RGB Gaming Keyboard  as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/0003:1B1C:1B11.0003/input/input5
[    1.890172] hid-generic 0003:1B1C:1B11.0003: input,hidraw2: USB HID v1.11 Keyboard [Corsair Corsair K95 RGB Gaming Keyboard ] on usb-0000:00:1d.0-2/input0
[    1.894074] input: Corsair Corsair K95 RGB Gaming Keyboard  as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.1/0003:1B1C:1B11.0004/input/input6
[    1.894500] hid-generic 0003:1B1C:1B11.0004: input,hiddev0,hidraw3: USB HID v1.11 Keyboard [Corsair Corsair K95 RGB Gaming Keyboard ] on usb-0000:00:1d.0-2/input1
[    1.894535] usbhid 6-2:1.2: couldn't find an input interrupt endpoint
[    1.938581] tsc: Refined TSC clocksource calibration: 3464.204 MHz
[    1.938940] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x31ef39c80a3, max_idle_ns: 440795279516 ns
[    1.964384] ata1.01: n_sectors mismatch 976764911 != 976773168
[    1.964385] ata1.01: new n_sectors matches native, probably late HPA unlock, n_sectors updated
[    1.970227] ata1.01: configured for UDMA/100
[    1.970230] ata1: EH complete
[    1.970570] sd 0:0:1:0: [sda] 976773168 512-byte logical blocks: (500 GB/466 GiB)
[    1.970614] sda: detected capacity change from 500103634432 to 500107862016
[    1.980367]  sda: sda1
[    1.980743] sd 0:0:1:0: [sda] Attached SCSI disk
[    2.006708] sda: detected capacity change from 0 to 500107862016
[    2.174556] usb 1-2: new high-speed USB device number 3 using ehci-pci
[    2.190554] usb 2-3: new high-speed USB device number 3 using ehci-pci
[    2.290637] [drm] ib test on ring 5 succeeded
[    2.327015] usb 1-2: New USB device found, idVendor=04a9, idProduct=176b
[    2.327017] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.327019] usb 1-2: Product: MX920 series
[    2.327021] usb 1-2: Manufacturer: Canon
[    2.327022] usb 1-2: SerialNumber: 11156D
[    2.441810] ata6: SATA link down (SStatus 0 SControl 300)
[    2.446550] usb 1-3: new high-speed USB device number 4 using ehci-pci
[    2.597034] usb 1-3: New USB device found, idVendor=1b1c, idProduct=1a95
[    2.597036] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.597038] usb 1-3: Product: Survivor GTR
[    2.597040] usb 1-3: Manufacturer: Corsair
[    2.597041] usb 1-3: SerialNumber: 000000000000000B
[    2.601477] usb-storage 1-3:1.0: USB Mass Storage device detected
[    2.601604] scsi host32: usb-storage 1-3:1.0
[    2.601657] usbcore: registered new interface driver usb-storage
[    2.602890] usbcore: registered new interface driver uas
[    2.615542] usb 2-3: New USB device found, idVendor=046d, idProduct=0821
[    2.615543] usb 2-3: New USB device strings: Mfr=0, Product=0, SerialNumber=1
[    2.615544] usb 2-3: SerialNumber: 17E2B2A0
[    2.757704] ata7: SATA link down (SStatus 0 SControl 300)
[    2.802509] [drm] ib test on ring 6 succeeded
[    2.962633] clocksource: Switched to clocksource tsc
[    3.234552] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.291876] ata8.00: ATA-10: WDC WD2005FBYZ-01YCBB1, RR04, max UDMA/133
[    3.291877] ata8.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    3.311043] ata8.00: configured for UDMA/133
[    3.311555] scsi 7:0:0:0: Direct-Access     ATA      WDC WD2005FBYZ-0 RR04 PQ: 0 ANSI: 5
[    3.314663] [drm] ib test on ring 7 succeeded
[    3.316821] [drm] Radeon Display Connectors
[    3.316822] [drm] Connector 0:
[    3.316822] [drm]   DP-1
[    3.316823] [drm]   HPD6
[    3.316823] [drm]   DDC: 0x6550 0x6550 0x6554 0x6554 0x6558 0x6558 0x655c 0x655c
[    3.316824] [drm]   Encoders:
[    3.316824] [drm]     DFP1: INTERNAL_UNIPHY1
[    3.316824] [drm] Connector 1:
[    3.316825] [drm]   DP-2
[    3.316825] [drm]   HPD1
[    3.316826] [drm]   DDC: 0x6560 0x6560 0x6564 0x6564 0x6568 0x6568 0x656c 0x656c
[    3.316826] [drm]   Encoders:
[    3.316826] [drm]     DFP2: INTERNAL_UNIPHY1
[    3.316826] [drm] Connector 2:
[    3.316827] [drm]   DP-3
[    3.316827] [drm]   HPD5
[    3.316828] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[    3.316828] [drm]   Encoders:
[    3.316828] [drm]     DFP3: INTERNAL_UNIPHY2
[    3.316828] [drm] Connector 3:
[    3.316829] [drm]   DP-4
[    3.316829] [drm]   HPD4
[    3.316829] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[    3.316830] [drm]   Encoders:
[    3.316830] [drm]     DFP4: INTERNAL_UNIPHY2
[    3.316830] [drm] Connector 4:
[    3.316830] [drm]   DVI-I-1
[    3.316831] [drm]   HPD2
[    3.316831] [drm]   DDC: 0x6570 0x6570 0x6574 0x6574 0x6578 0x6578 0x657c 0x657c
[    3.316832] [drm]   Encoders:
[    3.316832] [drm]     DFP5: INTERNAL_UNIPHY
[    3.316832] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    3.316833] [drm] Connector 5:
[    3.316833] [drm]   DVI-D-1
[    3.316833] [drm]   HPD3
[    3.316834] [drm]   DDC: 0x6580 0x6580 0x6584 0x6584 0x6588 0x6588 0x658c 0x658c
[    3.316834] [drm]   Encoders:
[    3.316834] [drm]     DFP6: INTERNAL_UNIPHY
[    3.342740] sd 7:0:0:0: Attached scsi generic sg1 type 0
[    3.342895] sd 7:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.82 TiB)
[    3.342934] sd 7:0:0:0: [sdb] Write Protect is off
[    3.342935] sd 7:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.343021] sd 7:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.369699]  sdb: sdb1 sdb2
[    3.371005] sd 7:0:0:0: [sdb] Attached SCSI disk
[    3.385494] random: fast init done
[    3.500255] [drm] fb mappable at 0xE05D8000
[    3.500256] [drm] vram apper at 0xE0000000
[    3.500256] [drm] size 9216000
[    3.500256] [drm] fb depth is 24
[    3.500257] [drm]    pitch is 7680
[    3.500370] fbcon: radeondrmfb (fb0) is primary device
[    3.500494] Console: switching to colour frame buffer device 240x75
[    3.500538] radeon 0000:03:00.0: fb0: radeondrmfb frame buffer device
[    3.518573] [drm] Initialized radeon 2.49.0 20080528 for 0000:03:00.0 on minor 0
[    3.535925] [drm] amdgpu kernel modesetting enabled.
[    3.603909] scsi 32:0:0:0: Direct-Access     Corsair  Survivor GTR     0.00 PQ: 0 ANSI: 2
[    3.604927] sd 32:0:0:0: Attached scsi generic sg2 type 0
[    3.605548] sd 32:0:0:0: [sdc] 63438848 512-byte logical blocks: (32.5 GB/30.3 GiB)
[    3.606207] sd 32:0:0:0: [sdc] Write Protect is off
[    3.606210] sd 32:0:0:0: [sdc] Mode Sense: 00 00 00 00
[    3.606826] sd 32:0:0:0: [sdc] Asking for cache data failed
[    3.606831] sd 32:0:0:0: [sdc] Assuming drive cache: write through
[    3.610709]  sdc: sdc1
[    3.635297] sd 32:0:0:0: [sdc] Attached SCSI removable disk
[    3.657732] ata9: SATA link down (SStatus 0 SControl 300)
[    3.973778] ata10: SATA link down (SStatus 0 SControl 300)
[    3.974304] scsi 10:0:0:0: Direct-Access     ATA      WDC WD3003FZEX-0 1A01 PQ: 0 ANSI: 5
[    4.006861] sd 10:0:0:0: Attached scsi generic sg3 type 0
[    4.007069] sd 10:0:0:0: [sdd] 5860524911 512-byte logical blocks: (3.00 TB/2.73 TiB)
[    4.007080] sd 10:0:0:0: [sdd] 4096-byte physical blocks
[    4.007131] sd 10:0:0:0: [sdd] Write Protect is off
[    4.007133] sd 10:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    4.007170] sd 10:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.007376] scsi 19:0:0:0: Processor         Marvell  91xx Config      1.01 PQ: 0 ANSI: 5
[    4.007459] scsi 19:0:0:0: Attached scsi generic sg4 type 3
[    4.007609] scsi 20:0:0:0: Direct-Access     ATA      WDC WD3003FZEX-0 1A01 PQ: 0 ANSI: 5
[    4.038573] sd 20:0:0:0: Attached scsi generic sg5 type 0
[    4.038662] sd 20:0:0:0: [sde] 5860533168 512-byte logical blocks: (3.00 TB/2.73 TiB)
[    4.038664] sd 20:0:0:0: [sde] 4096-byte physical blocks
[    4.038678] sd 20:0:0:0: [sde] Write Protect is off
[    4.038679] sd 20:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    4.038716] sd 20:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.038868] scsi 29:0:0:0: Processor         Marvell  91xx Config      1.01 PQ: 0 ANSI: 5
[    4.038959] scsi 29:0:0:0: Attached scsi generic sg6 type 3
[    4.041975]  sdd: sdd1
[    4.042320] sd 10:0:0:0: [sdd] Attached SCSI removable disk
[    4.077660]  sde: sde1
[    4.078430] sd 20:0:0:0: [sde] Attached SCSI disk
[    4.178608] floppy0: no floppy controllers found
[    4.178618] work still pending
[    5.062226] random: crng init done
[   19.017289] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   20.043934] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[   20.044107] systemd[1]: Detected architecture x86-64.
[   20.052945] systemd[1]: Set hostname to <peterandcrazybear-GA-X58A-UD7>.
[   21.952790] systemd[1]: Listening on Device-mapper event daemon FIFOs.
[   21.952901] systemd[1]: Created slice System Slice.
[   21.952931] systemd[1]: Listening on fsck to fsckd communication Socket.
[   21.952939] systemd[1]: Reached target Remote File Systems (Pre).
[   21.952982] systemd[1]: Created slice User and Session Slice.
[   21.953028] systemd[1]: Listening on Journal Audit Socket.
[   21.953037] systemd[1]: Reached target Encrypted Volumes.
[   22.258318] lp: driver loaded but no devices found
[   22.485105] ppdev: user-space parallel port driver
[   22.648054] it87: Found IT8720F chip at 0x290, revision 8
[   22.648062] it87: VID is disabled (pins used for GPIO)
[   22.648070] it87: Routing internal VCCH to in7
[   22.648073] it87: Beeping is supported
[   26.548186] systemd[1]: Started Journal Service.
[   43.724374] ip_tables: (C) 2000-2006 Netfilter Core Team
[   43.891983] nf_conntrack version 0.5.0 (65536 buckets, 262144 max)
[   44.059479] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   45.148113] EXT4-fs (sdb1): re-mounted. Opts: (null)
[   45.325235] systemd-journald[521]: Received request to flush runtime journal from PID 1
[   45.625369] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   45.655666] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x000000000000042C-0x000000000000042D (\GP2C) (20160930/utaddress-247)
[   45.655670] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   45.655719] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   45.739935] SSE version of gcm_enc/dec engaged.
[   45.779626] EDAC MC: Ver: 3.0.0
[   45.876349] EDAC i7core: Device not found: dev 00.0 PCI ID 8086:2c70
[   45.937636] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   46.027588] gpio_ich: GPIO from 451 to 511 on gpio_ich
[   46.171933] media: Linux media interface: v0.10
[   46.389464] snd_hda_intel 0000:03:00.1: Handle vga_switcheroo audio client
[   46.389465] snd_hda_intel 0000:03:00.1: Force to non-snoop mode
[   46.478864] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:07.0/0000:03:00.1/sound/card2/input7
[   46.478905] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:07.0/0000:03:00.1/sound/card2/input8
[   46.478943] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:07.0/0000:03:00.1/sound/card2/input9
[   46.478981] input: HDA ATI HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:07.0/0000:03:00.1/sound/card2/input10
[   46.479017] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:07.0/0000:03:00.1/sound/card2/input11
[   46.479054] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:07.0/0000:03:00.1/sound/card2/input12
[   46.481166] snd_hda_codec_realtek hdaudioC0D2: autoconfig for ALC889: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   46.481168] snd_hda_codec_realtek hdaudioC0D2:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   46.481169] snd_hda_codec_realtek hdaudioC0D2:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   46.481170] snd_hda_codec_realtek hdaudioC0D2:    mono: mono_out=0x0
[   46.481171] snd_hda_codec_realtek hdaudioC0D2:    dig-out=0x11/0x1e
[   46.481172] snd_hda_codec_realtek hdaudioC0D2:    inputs:
[   46.481174] snd_hda_codec_realtek hdaudioC0D2:      Front Mic=0x19
[   46.481175] snd_hda_codec_realtek hdaudioC0D2:      Rear Mic=0x18
[   46.481176] snd_hda_codec_realtek hdaudioC0D2:      Line=0x1a
[   46.481177] snd_hda_codec_realtek hdaudioC0D2:    dig-in=0x1f
[   46.495524] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   46.495571] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   46.495609] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   46.495687] input: HDA Intel Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   46.495770] input: HDA Intel Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[   46.495842] input: HDA Intel Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input18
[   46.495917] input: HDA Intel Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input19
[   46.495992] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input20
[   46.561146] usblp 1-2:1.1: usblp2: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04A9 pid 0x176B
[   46.564947] usblp 1-2:1.2: usblp3: USB Bidirectional printer dev 3 if 2 alt 0 proto 2 vid 0x04A9 pid 0x176B
[   46.564973] usbcore: registered new interface driver usblp
[   46.593632] Linux video capture interface: v2.00
[   46.604591] usb 2-3: current rate 0 is different from the runtime rate 16000
[   46.622816] usb 2-3: current rate 0 is different from the runtime rate 24000
[   46.641067] usb 2-3: current rate 0 is different from the runtime rate 32000
[   46.670629] usbcore: registered new interface driver snd-usb-audio
[   46.684922] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0821)
[   46.697565] uvcvideo 2-3:1.2: Entity type for entity Extension 4 was not initialized!
[   46.697569] uvcvideo 2-3:1.2: Entity type for entity Processing 2 was not initialized!
[   46.697571] uvcvideo 2-3:1.2: Entity type for entity Camera 1 was not initialized!
[   46.697573] uvcvideo 2-3:1.2: Entity type for entity Extension 5 was not initialized!
[   46.697575] uvcvideo 2-3:1.2: Entity type for entity Extension 6 was not initialized!
[   46.697577] uvcvideo 2-3:1.2: Entity type for entity Extension 7 was not initialized!
[   46.697579] uvcvideo 2-3:1.2: Entity type for entity Extension 8 was not initialized!
[   46.697708] input: UVC Camera (046d:0821) as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.2/input/input21
[   46.697772] usbcore: registered new interface driver uvcvideo
[   46.697772] USB Video Class driver (1.1.1)
[   46.734726] audit: type=1400 audit(1512841088.227:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-xpdfimport" pid=1240 comm="apparmor_parser"
[   46.735927] audit: type=1400 audit(1512841088.227:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=1242 comm="apparmor_parser"
[   46.735928] audit: type=1400 audit(1512841088.227:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=1242 comm="apparmor_parser"
[   46.862073] audit: type=1400 audit(1512841088.355:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/vidalia" pid=1235 comm="apparmor_parser"
[   46.872119] audit: type=1400 audit(1512841088.363:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-oopslash" pid=1237 comm="apparmor_parser"
[   46.874912] audit: type=1400 audit(1512841088.367:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-soffice" pid=1239 comm="apparmor_parser"
[   46.888885] audit: type=1400 audit(1512841088.379:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=1238 comm="apparmor_parser"
[   46.890830] audit: type=1400 audit(1512841088.383:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=1230 comm="apparmor_parser"
[   46.890832] audit: type=1400 audit(1512841088.383:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1230 comm="apparmor_parser"
[   46.890832] audit: type=1400 audit(1512841088.383:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=1230 comm="apparmor_parser"
[   47.778042] Adding 9220092k swap on /dev/sdb2.  Priority:-1 extents:1 across:9220092k FS
[   47.830803] cgroup: new mount options do not match the existing superblock, will be ignored
[   48.722114] floppy0: no floppy controllers found
[   48.722125] work still pending
[   53.730621] IPv6: ADDRCONF(NETDEV_UP): eth3: link is not ready
[   53.883288] r8169 0000:09:00.0 eth3: link down
[   53.883296] r8169 0000:09:00.0 eth3: link down
[   53.883337] IPv6: ADDRCONF(NETDEV_UP): eth3: link is not ready
[   53.886897] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
[   53.947284] r8169 0000:08:00.0 eth2: link down
[   53.947291] r8169 0000:08:00.0 eth2: link down
[   53.947321] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
[   54.463549] kauditd_printk_skb: 33 callbacks suppressed
[   54.463550] audit: type=1400 audit(1512841095.955:45): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/proc/1863/status" pid=1863 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=119 ouid=119
[   54.463552] audit: type=1400 audit(1512841095.955:46): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=1863 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=119 ouid=0
[   54.463567] audit: type=1400 audit(1512841095.955:47): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/proc/1863/status" pid=1863 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=119 ouid=119
[   55.605122] r8169 0000:08:00.0 eth2: link up
[   55.605130] IPv6: ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[   56.968951] r8169 0000:09:00.0 eth3: link up
[   56.968962] IPv6: ADDRCONF(NETDEV_CHANGE): eth3: link becomes ready
[   58.484387] audit: type=1400 audit(1512841099.975:48): apparmor="DENIED" operation="capable" profile="/usr/sbin/cupsd" pid=2113 comm="usb" capability=35  capname="wake_alarm"
[   58.487688] usblp2: nonzero read bulk status received: -108
[   58.494366] usblp2: removed
[   58.500552] usblp 1-2:1.1: usblp2: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04A9 pid 0x176B
[   58.500667] usblp3: removed
[   58.501285] audit: type=1400 audit(1512841099.991:49): apparmor="DENIED" operation="capable" profile="/usr/sbin/cupsd" pid=2113 comm="usb" capability=35  capname="wake_alarm"
[   58.505421] usblp 1-2:1.2: usblp3: USB Bidirectional printer dev 3 if 2 alt 0 proto 2 vid 0x04A9 pid 0x176B
[   59.040963] NET: Registered protocol family 4
[   59.044545] NET: Registered protocol family 5
[   59.965567] [UFW BLOCK] IN=eth3 OUT= MAC=6c:f0:49:5e:db:03:14:dd:a9:ca:c0:98:08:00 SRC=67.149.247.208 DST=192.168.1.56 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=3561 PROTO=UDP SPT=32169 DPT=56418 LEN=28 
[   60.189337] [UFW BLOCK] IN=eth2 OUT= MAC= SRC=fe80:0000:0000:0000:4d61:e9b2:98cd:aefa DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=830309 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[   60.189354] [UFW BLOCK] IN=eth2 OUT= MAC= SRC=fe80:0000:0000:0000:4d61:e9b2:98cd:aefa DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=1016503 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[   60.189364] [UFW BLOCK] IN=eth3 OUT= MAC= SRC=fe80:0000:0000:0000:a925:0343:eb4c:7e4f DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=586286 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[   60.189374] [UFW BLOCK] IN=eth3 OUT= MAC= SRC=fe80:0000:0000:0000:a925:0343:eb4c:7e4f DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=966953 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[   60.199509] [UFW BLOCK] IN=eth2 OUT= MAC= SRC=fe80:0000:0000:0000:4d61:e9b2:98cd:aefa DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=830309 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[   60.199525] [UFW BLOCK] IN=eth2 OUT= MAC= SRC=fe80:0000:0000:0000:4d61:e9b2:98cd:aefa DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=1016503 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[   60.199533] [UFW BLOCK] IN=eth3 OUT= MAC= SRC=fe80:0000:0000:0000:a925:0343:eb4c:7e4f DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=586286 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[   60.199542] [UFW BLOCK] IN=eth3 OUT= MAC= SRC=fe80:0000:0000:0000:a925:0343:eb4c:7e4f DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=966953 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[   60.978481] Ebtables v2.0 registered
[   62.836366] bridge: filtering via arp/ip/ip6tables is no longer available by default. Update your scripts to load br_netfilter if you need this.
[   62.905951] virbr0: port 1(virbr0-nic) entered blocking state
[   62.905952] virbr0: port 1(virbr0-nic) entered disabled state
[   62.906012] device virbr0-nic entered promiscuous mode
[   64.392218] virbr0: port 1(virbr0-nic) entered blocking state
[   64.392220] virbr0: port 1(virbr0-nic) entered listening state
[   64.775354] virbr0: port 1(virbr0-nic) entered disabled state
[   64.777249] device virbr0-nic left promiscuous mode
[   64.777263] virbr0: port 1(virbr0-nic) entered disabled state
[   64.996858] [UFW BLOCK] IN=eth3 OUT= MAC=6c:f0:49:5e:db:03:14:dd:a9:ca:c0:98:08:00 SRC=67.149.247.208 DST=192.168.1.56 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=9487 PROTO=UDP SPT=32169 DPT=56418 LEN=28 
[   84.226298] vboxdrv: loading out-of-tree module taints kernel.
[   84.226465] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[   84.234751] vboxdrv: Found 12 processor cores
[   84.252367] vboxdrv: TSC mode is Invariant, tentative frequency 3465965949 Hz
[   84.252367] vboxdrv: Successfully loaded version 5.0.40_Ubuntu (interface 0x00240000)
[   84.256463] VBoxNetFlt: Successfully started.
[   84.260507] VBoxNetAdp: Successfully started.
[   84.264066] VBoxPciLinuxInit
[   84.266351] vboxpci: IOMMU not found (not registered)
[   85.293917] nf_conntrack: default automatic helper assignment has been turned off for security reasons and CT-based  firewall rule not found. Use the iptables CT target to attach helpers instead.
[   89.714725] usb 2-3: reset high-speed USB device number 3 using ehci-pci
[   90.532985] usb 2-3: current rate 0 is different from the runtime rate 32000
[   90.558394] usb 2-3: current rate 0 is different from the runtime rate 32000
[  131.942822] usb 2-3: current rate 0 is different from the runtime rate 32000
[  131.968197] usb 2-3: current rate 0 is different from the runtime rate 32000
[  140.154606] EXT4-fs (sdd1): recovery complete
[  140.154609] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)
[  140.608118] FAT-fs (sdc1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[  615.496689] perf: interrupt took too long (2501 > 2500), lowering kernel.perf_event_max_sample_rate to 79750

```

---

### Post by crazybear on 2017-12-09
What is this all about? Is this worth installing in my case?
[https://wiki.ubuntu.com/Kernel/CrashdumpRecipe?action=show&redirect=KernelTeam%2FCrashdumpRecipe](https://wiki.ubuntu.com/Kernel/CrashdumpRecipe?action=show&redirect=KernelTeam%2FCrashdumpRecipe)

I was just looking at the /var/log/syslog at the time just before this last crash. It is different then the ones before - it repeats for several hundred lines alternating these two:

```

[COLOR=#222222][FONT=Verdana]Dec  9 18:34:30 X-GA-X58A-UD7 gnome-session[8109]: (gnome-shell:8341): libnm-glib-WARNING **: async_got_type: could not read properties for /org/freedesktop/NetworkManager/ActiveConnection/287: No such interface 'org.freedesktop.DBus.Properties' on object at path /org/freedesktop/NetworkManager/ActiveConnection/287[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Dec  9 18:34:30 X-GA-X58A-UD7 gnome-session[8109]: message repeated 2 times: [ (gnome-shell:8341): libnm-glib-WARNING **: async_got_type: could not read properties for /org/freedesktop/NetworkManager/ActiveConnection/287: No such interface 'org.freedesktop.DBus.Properties' on object at path /org/freedesktop/NetworkManager/ActiveConnection/287]
[/FONT][/COLOR]
```
[COLOR=#222222][FONT=Verdana]
meaning?

this is part of the output of lspci -k

[/FONT][/COLOR]```

03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT2 [Radeon HD 7970 GHz Edition]
    Kernel driver in use: radeon
    Kernel modules: radeon, amdgpu
03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti HDMI Audio [Radeon HD 7870 XT / 7950/7970]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT HDMI Audio [Radeon HD 7970 Series]

```

---

### Post by crazybear on 2017-12-09
I just did a stress test on the GPU....temperature went up to 63C for ten minutes, but no crash...?!?!?
Then a GL test for six minutes....temperature went up to 70C, but no crash and the images and results were very good/high.

is there no way to upload a jpg file here unless it is on the internet?

---

### Post by crazybear on 2017-12-09
> **dragonfly41 said:**
> More reading here ...

[ https://wiki.ubuntu.com/X/Troubleshooting/Freeze]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze")

[http://odm.ubuntu.com/](http://odm.ubuntu.com/)

Thanks. I read through that...understood some, didn't understand some.

---

### Post by rbmorse on 2017-12-09
Based on the stress tests, it would appear that the hardware is solid, at least as far as I can tell.

---

### Post by dragonfly41 on 2017-12-09
> [COLOR=#000000]is there no way to upload a jpg file here unless it is on the internet?[/COLOR][COLOR=#000000]

When posting to forum use "Go Advanced" button and then use "Manage Attachments" to upload your .jpg (or other format) file.[/COLOR]

---

### Post by crazybear on 2017-12-10
Just wanted to post the results of the tests which I took screenshots of.

Can anyone make heads or tails of the link I mentioned above. Someone had nearly the same GPU as I and also was having crashes, but on that thread I don't quite get some of the steps he took or others suggested he take. [https://bbs.archlinux.org/viewtopic.php?id=229332](https://bbs.archlinux.org/viewtopic.php?id=229332) He was using Archlinux, if that makes a big difference from Ubuntu - I don't know. He does gaming - I do not.

---

### Post by dragonfly41 on 2017-12-10
Found one tip from the very cryptic discussion threads.

install and run radeontop  to monitor Radeon GPU utilisation.  It is in Ubuntu Software Centre and can be installed using Synaptic.

[http://manpages.ubuntu.com/manpages/zesty/man1/radeontop.1.html](http://manpages.ubuntu.com/manpages/zesty/man1/radeontop.1.html)

Also this is a useful tutorial of Linux Graphics Stack

[http://blog.mecheye.net/2012/06/the-linux-graphics-stack/](http://blog.mecheye.net/2012/06/the-linux-graphics-stack/)

---

### Post by crazybear on 2017-12-14
The situation seems somewhat more stable [but not completely stable nor fixed]. I haven't had a crash in several days, but today had to reboot three times to get one monitor to not be all blurry. Once a blurry monitor is stable, it doesn't change during a session. Both the radeon and amdgpu drivers are there, but according to what I posted above, the radeon driver is being used. I twice listed a reference to how to customize the kernel and xorg for a Tahiti AMD GPU, above, but the instructions are beyond my ability to do without some guidance. I realize one is not [according to Hoyle] supposed to have both drivers, but in fact, the current situation is more stable than when I only had the radeon installed. Do not know why, but perhaps the xorg hwe-16.04 files help out. I'd appreciate any ideas. Radeontop is installed, but gives little information I think I can use. It seems to show how much of various resources in the GPU are being used and with most I do that is very very little of the available resources. Can anyone think of a way to interpret the various reports generated just before the crashes [and which of many logs I should monitor after coming crashes]?

---

### Post by dragonfly41 on 2017-12-14
> [COLOR=#000000]and which of many logs I should monitor after coming crashes[/COLOR][COLOR=#000000]

[/COLOR]I suggest that you need to monitor when/what changes are made to log files (in /var/log) during normal use so that you can focus on these specific log files after a crash/freeze.

Here is one suggestion ..

Reference:
[https://askubuntu.com/questions/541128/monitor-folder-contents-changes](https://askubuntu.com/questions/541128/monitor-folder-contents-changes)

Install inotifywait-tools and glogg (which is a log file viewer)

Run this command

inotifywait /var/log --recursive --monitor

Monitor which log files are being MODIFIED.

Launch glogg and keep glogg open to view log files (one tab per log file derived from inotifywait watch log).

Search in each log file for keywords such as fail, warn, radeon ... etc.

Perhaps pipe the output of inotifywait to a file for future analysis.


[COLOR=#b22222][Later edit][/COLOR]

Reading more about inotify here ..

[https://www.infoq.com/articles/inotify-linux-file-system-event-monitoring](https://www.infoq.com/articles/inotify-linux-file-system-event-monitoring)

it seems that inotifywatch will capture statistics  over a specified time (e.g. 120 seconds) and give a shorter summary report.

```
inotifywatch -v -e access -e modify -t 120 -r /var/log
```

---

### Post by crazybear on 2017-12-15
Thanks, but I'm sure it has to be more exacting on the target than that....as it just sets out a list [about 100 lines per minute or more of very HUGE log files:

```

$ inotifywait /var/log --recursive --monitor
Setting up watches.  Beware: since -r was given, this may take a while!
Watches established.
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY auth.log
/var/log/ OPEN auth.log
/var/log/ ACCESS auth.log
/var/log/ MODIFY auth.log
/var/log/ ACCESS auth.log
/var/log/ MODIFY auth.log
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY auth.log
/var/log/ MODIFY syslog
/var/log/ ACCESS auth.log
/var/log/atsar/ OPEN atsa15
/var/log/atsar/ ACCESS atsa15
/var/log/ CLOSE_NOWRITE,CLOSE auth.log
/var/log/atsar/ MODIFY atsa15
/var/log/atsar/ CLOSE_WRITE,CLOSE atsa15
/var/log/ MODIFY auth.log
/var/log/ OPEN auth.log
/var/log/ ACCESS auth.log
/var/log/ ACCESS auth.log
/var/log/ CLOSE_NOWRITE,CLOSE auth.log
/var/log/munin/ OPEN munin-update.log
/var/log/munin/ MODIFY munin-update.log
/var/log/munin/ MODIFY munin-update.log
/var/log/munin/ MODIFY munin-node.log
/var/log/munin/ MODIFY munin-update.log
/var/log/apache2/ MODIFY access.log
/var/log/apache2/ MODIFY access.log
/var/log/ OPEN mail.log
/var/log/ CLOSE_NOWRITE,CLOSE mail.log
/var/log/apache2/ MODIFY access.log
/var/log/apache2/ MODIFY access.log
/var/log/munin/ OPEN munin-update.log
/var/log/munin/ ACCESS munin-update.log
/var/log/munin/ CLOSE_NOWRITE,CLOSE munin-update.log
/var/log/munin/ OPEN munin-graph.log
/var/log/munin/ CLOSE_NOWRITE,CLOSE munin-graph.log
/var/log/munin/ OPEN munin-html.log
/var/log/munin/ ACCESS munin-html.log
/var/log/munin/ CLOSE_NOWRITE,CLOSE munin-html.log
/var/log/munin/ OPEN munin-limits.log
/var/log/munin/ ACCESS munin-limits.log
/var/log/munin/ CLOSE_NOWRITE,CLOSE munin-limits.log
/var/log/munin/ MODIFY munin-update.log
/var/log/munin/ MODIFY munin-update.log
/var/log/munin/ MODIFY munin-update.log
/var/log/munin/ CLOSE_WRITE,CLOSE munin-update.log
/var/log/munin/ OPEN munin-limits.log
/var/log/munin/ MODIFY munin-limits.log
/var/log/munin/ MODIFY munin-limits.log
/var/log/munin/ CLOSE_WRITE,CLOSE munin-limits.log
/var/log/munin/ OPEN munin-html.log
/var/log/munin/ MODIFY munin-html.log
/var/log/munin/ MODIFY munin-html.log
/var/log/munin/ MODIFY munin-html.log
/var/log/munin/ MODIFY munin-html.log
/var/log/munin/ MODIFY munin-html.log
/var/log/munin/ CLOSE_WRITE,CLOSE munin-html.log
/var/log/munin/ OPEN munin-graph.log
/var/log/munin/ CLOSE_WRITE,CLOSE munin-graph.log
/var/log/ MODIFY auth.log
/var/log/ OPEN auth.log
/var/log/ ACCESS auth.log
/var/log/ ACCESS auth.log
/var/log/ CLOSE_NOWRITE,CLOSE auth.log
/var/log/wicd/ MODIFY wicd.log
/var/log/wicd/ MODIFY wicd.log
/var/log/wicd/ MODIFY wicd.log
/var/log/wicd/ MODIFY wicd.log
/var/log/wicd/ MODIFY wicd.log
/var/log/wicd/ MODIFY wicd.log
/var/log/wicd/ MODIFY wicd.log
/var/log/wicd/ MODIFY wicd.log
/var/log/wicd/ MODIFY wicd.log
/var/log/wicd/ MODIFY wicd.log
/var/log/wicd/ MODIFY wicd.log
/var/log/wicd/ MODIFY wicd.log
/var/log/wicd/ MODIFY wicd.log
/var/log/wicd/ MODIFY wicd.log
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY kern.log
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog
/var/log/ MODIFY syslog




```

I let it run for a few minutes, but it was a list a few hundred lines long of many log files - each of them huge.
My crashes are now, on average, once every 2-3 days. I don't see how I could look through all of the large log files and find the needle in the haystack or really the up charm in the universe. I see it can be made more specific, but don't know what to target - if I did, I'd know what the problem was.

---

### Post by crazybear on 2017-12-20
I have tried unsuccessfully to post for many days. I don't know the problem. On the chance the post was too large, it is broken into two parts here. I had another crash. The two parts of /var/syslog show the last few minutes with NEW and DIFFERENT than past Warnings and a very strange end of zeros. Can anyone make any sense of the problem? Thanks in advance.

```

c 18 15:00:01X-GA-X58A-UD7 CRON[25134]: (munin) CMD (if [ -x /usr/bin/munin-cron]; then /usr/bin/munin-cron; fi)
Dec 18 15:00:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_name: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:00:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_description: assertion 'G_IS_APP_INFO (appinfo)'failed
Dec 18 15:00:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_icon: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:00:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:00:45.436] Could notload desktop item: Object reference not set to an instance of anobject
Dec 18 15:00:45X-GA-X58A-UD7 gnome-session[11979]: Could not locate Tomboy on D-Bus.Perhaps it's not running?
Dec 18 15:00:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:00:45.481][UniverseManager] Error while updating item source "Torrents":Cannot access Transmission RPC service
Dec 18 15:00:47X-GA-X58A-UD7 gnome-session[11979]:[15538:15624:1218/150047.703845:ERROR:service_manager.cc(157)]Connection InterfaceProviderSpec prevented service: content_rendererfrom binding interface: blink::mojom::ReportingServiceProxy exposedby: content_browser
Dec 18 15:01:13X-GA-X58A-UD7 gnome-session[11979]: Gtk-Message: GtkDialog mappedwithout a transient parent. This is discouraged.
Dec 18 15:01:13X-GA-X58A-UD7 dbus[1594]: [system] Activating via systemd: servicename='org.freedesktop.hostname1'unit='dbus-org.freedesktop.hostname1.service'
Dec 18 15:01:13X-GA-X58A-UD7 systemd[1]: Starting Hostname Service...
Dec 18 15:01:13X-GA-X58A-UD7 dbus[1594]: [system] Successfully activated service'org.freedesktop.hostname1'
Dec 18 15:01:13X-GA-X58A-UD7 systemd[1]: Started Hostname Service.
Dec 18 15:01:13X-GA-X58A-UD7 org.gtk.vfs.Daemon[11820]: ** (process:15428): WARNING**: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' onobject at path /org/gtk/vfs/client/enumerator/7 (g-dbus-error-quark,19)
Dec 18 15:01:13X-GA-X58A-UD7 org.gtk.vfs.Daemon[11820]: ** (process:15428): WARNING**: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' onobject at path /org/gtk/vfs/client/enumerator/7 (g-dbus-error-quark,19)
Dec 18 15:01:13X-GA-X58A-UD7 org.gtk.vfs.Daemon[11820]: ** (process:15428): WARNING**: send_done_cb: No such interface 'org.gtk.vfs.Enumerator' onobject at path /org/gtk/vfs/client/enumerator/7 (g-dbus-error-quark,19)
Dec 18 15:01:41X-GA-X58A-UD7 gnome-session[11979]: Traceback (most recent calllast):
Dec 18 15:01:41X-GA-X58A-UD7 gnome-session[11979]:   File"/usr/share/nautilus-python/extensions/RabbitVCS.py", line392, in get_file_items_full
Dec 18 15:01:41X-GA-X58A-UD7 gnome-session[11979]:     menu =NautilusMainContextMenu(self, window.base_dir, paths,conditions).get_menu()
Dec 18 15:01:41X-GA-X58A-UD7 gnome-session[11979]: AttributeError:'NautilusDesktopWindow' object has no attribute 'base_dir'
Dec 18 15:02:19X-GA-X58A-UD7 hddtemp[7672]: /dev/sda: WDC WD5000AAKB-00H8A0: 27 C
Dec 18 15:02:19X-GA-X58A-UD7 hddtemp[7672]: /dev/sdb: WDC WD1502FAEX-007BA0: 30 C
Dec 18 15:02:19X-GA-X58A-UD7 hddtemp[7672]: /dev/sdc: WDC WD2005FBYZ-01YCBB1: 28 C
Dec 18 15:02:19X-GA-X58A-UD7 hddtemp[7672]: /dev/sde: WDC WD1005FBYZ-01YCBB1: 28 C
Dec 18 15:02:19X-GA-X58A-UD7 hddtemp[7672]: /dev/sdf: WDC WD2003FZEX-00Z4SA0: 30 C
Dec 18 15:02:19X-GA-X58A-UD7 hddtemp[7672]: /dev/sdg: WDC WD3003FZEX-00Z4SA0: 28 C
Dec 18 15:02:19X-GA-X58A-UD7 hddtemp[7672]: /dev/sdh: WDC WD3003FZEX-00Z4SA0: 28 C
Dec 18 15:02:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_name: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:02:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_description: assertion 'G_IS_APP_INFO (appinfo)'failed
Dec 18 15:02:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_icon: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:02:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:02:45.483] Could notload desktop item: Object reference not set to an instance of anobject
Dec 18 15:02:45X-GA-X58A-UD7 gnome-session[11979]: Could not locate Tomboy on D-Bus.Perhaps it's not running?
Dec 18 15:02:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:02:45.532][UniverseManager] Error while updating item source "Torrents":Cannot access Transmission RPC service
Dec 18 15:03:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605807.3440]policy: auto-activating connection 'Wired connection 2'
Dec 18 15:03:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605807.3449]device (eth2): Activation: starting connection 'Wired connection 2'(a98d58b2-6397-3af5-b113-858cff6ccc3e)
Dec 18 15:03:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605807.3451]device (eth2): state change: disconnected -> prepare (reason'none') [30 40 0]
Dec 18 15:03:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605807.3455]device (eth2): state change: prepare -> config (reason 'none') [4050 0]
Dec 18 15:03:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605807.3459]device (eth2): state change: config -> ip-config (reason 'none')[50 70 0]
Dec 18 15:03:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605807.3461]dhcp4 (eth2): activation: beginning transaction (timeout in 45seconds)
Dec 18 15:03:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605807.3472]dhcp4 (eth2): dhclient started with pid 819
Dec 18 15:03:27X-GA-X58A-UD7 dhclient[819]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 3 (xid=0x71965a21)
Dec 18 15:03:29X-GA-X58A-UD7 ntpd[7515]: bind(21) AF_INET6fe80::4d61:e9b2:98cd:aefa%2#123 flags 0x11 failed: Cannot assignrequested address
Dec 18 15:03:29X-GA-X58A-UD7 ntpd[7515]: unable to create socket on eth2 (100) forfe80::4d61:e9b2:98cd:aefa%2#123
Dec 18 15:03:29X-GA-X58A-UD7 ntpd[7515]: failed to init interface for addressfe80::4d61:e9b2:98cd:aefa%2
Dec 18 15:03:29X-GA-X58A-UD7 avahi-daemon[1584]: Joining mDNS multicast group oninterface eth2.IPv6 with address fe80::4d61:e9b2:98cd:aefa.
Dec 18 15:03:29X-GA-X58A-UD7 avahi-daemon[1584]: New relevant interface eth2.IPv6for mDNS.
Dec 18 15:03:29X-GA-X58A-UD7 avahi-daemon[1584]: Registering new address record forfe80::4d61:e9b2:98cd:aefa on eth2.*.
Dec 18 15:03:30X-GA-X58A-UD7 dhclient[819]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 4 (xid=0x71965a21)
Dec 18 15:03:31X-GA-X58A-UD7 ntpd[7515]: Listen normally on 101 eth2[fe80::4d61:e9b2:98cd:aefa%2]:123
Dec 18 15:03:31X-GA-X58A-UD7 ntpd[7515]: new interface(s) found: waking up resolver
Dec 18 15:03:34X-GA-X58A-UD7 dhclient[819]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 5 (xid=0x71965a21)
Dec 18 15:03:39X-GA-X58A-UD7 dhclient[819]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 5 (xid=0x71965a21)
Dec 18 15:03:44X-GA-X58A-UD7 dhclient[819]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 7 (xid=0x71965a21)
Dec 18 15:03:51X-GA-X58A-UD7 dhclient[819]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 7 (xid=0x71965a21)
Dec 18 15:03:58X-GA-X58A-UD7 dhclient[819]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 15 (xid=0x71965a21)
Dec 18 15:04:12X-GA-X58A-UD7 NetworkManager[1827]: <warn>  [1513605852.3501]dhcp4 (eth2): request timed out
Dec 18 15:04:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605852.3502]dhcp4 (eth2): state changed unknown -> timeout
Dec 18 15:04:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605852.4146]dhcp4 (eth2): canceled DHCP transaction, DHCP client pid 819
Dec 18 15:04:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605852.4146]dhcp4 (eth2): state changed timeout -> done
Dec 18 15:04:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605852.4148]device (eth2): state change: ip-config -> failed (reason'ip-config-unavailable') [70 120 5]
Dec 18 15:04:12X-GA-X58A-UD7 NetworkManager[1827]: <warn>  [1513605852.4152]device (eth2): Activation: failed for connection 'Wired connection 2'
Dec 18 15:04:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605852.4160]device (eth2): state change: failed -> disconnected (reason'none') [120 30 0]
Dec 18 15:04:12X-GA-X58A-UD7 avahi-daemon[1584]: Withdrawing address record forfe80::4d61:e9b2:98cd:aefa on eth2.
Dec 18 15:04:12X-GA-X58A-UD7 avahi-daemon[1584]: Leaving mDNS multicast group oninterface eth2.IPv6 with address fe80::4d61:e9b2:98cd:aefa.
Dec 18 15:04:12X-GA-X58A-UD7 avahi-daemon[1584]: Interface eth2.IPv6 no longerrelevant for mDNS.
Dec 18 15:04:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605852.4208]policy: auto-activating connection 'Wired connection 2'
Dec 18 15:04:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605852.4216]device (eth2): Activation: starting connection 'Wired connection 2'(a98d58b2-6397-3af5-b113-858cff6ccc3e)
Dec 18 15:04:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605852.4217]device (eth2): state change: disconnected -> prepare (reason'none') [30 40 0]
Dec 18 15:04:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605852.4220]device (eth2): state change: prepare -> config (reason 'none') [4050 0]
Dec 18 15:04:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605852.4224]device (eth2): state change: config -> ip-config (reason 'none')[50 70 0]
Dec 18 15:04:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605852.4228]dhcp4 (eth2): activation: beginning transaction (timeout in 45seconds)
Dec 18 15:04:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605852.4238]dhcp4 (eth2): dhclient started with pid 3084
Dec 18 15:04:12X-GA-X58A-UD7 dhclient[3084]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 3 (xid=0xfd806c4f)
Dec 18 15:04:13X-GA-X58A-UD7 avahi-daemon[1584]: Joining mDNS multicast group oninterface eth2.IPv6 with address fe80::4d61:e9b2:98cd:aefa.
Dec 18 15:04:13X-GA-X58A-UD7 avahi-daemon[1584]: New relevant interface eth2.IPv6for mDNS.
Dec 18 15:04:13X-GA-X58A-UD7 avahi-daemon[1584]: Registering new address record forfe80::4d61:e9b2:98cd:aefa on eth2.*.
Dec 18 15:04:15X-GA-X58A-UD7 dhclient[3084]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 8 (xid=0xfd806c4f)
Dec 18 15:04:23X-GA-X58A-UD7 dhclient[3084]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 17 (xid=0xfd806c4f)
Dec 18 15:04:40X-GA-X58A-UD7 dhclient[3084]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 14 (xid=0xfd806c4f)
Dec 18 15:04:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_name: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:04:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_description: assertion 'G_IS_APP_INFO (appinfo)'failed
Dec 18 15:04:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_icon: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:04:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:04:45.535] Could notload desktop item: Object reference not set to an instance of anobject
Dec 18 15:04:45X-GA-X58A-UD7 gnome-session[11979]: Could not locate Tomboy on D-Bus.Perhaps it's not running?
Dec 18 15:04:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:04:45.588][UniverseManager] Error while updating item source "Torrents":Cannot access Transmission RPC service
Dec 18 15:04:54X-GA-X58A-UD7 dhclient[3084]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 15 (xid=0xfd806c4f)
Dec 18 15:04:57X-GA-X58A-UD7 NetworkManager[1827]: <warn>  [1513605897.3509]dhcp4 (eth2): request timed out
Dec 18 15:04:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605897.3510]dhcp4 (eth2): state changed unknown -> timeout
Dec 18 15:04:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605897.4153]dhcp4 (eth2): canceled DHCP transaction, DHCP client pid 3084
Dec 18 15:04:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605897.4154]dhcp4 (eth2): state changed timeout -> done
Dec 18 15:04:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605897.4156]device (eth2): state change: ip-config -> failed (reason'ip-config-unavailable') [70 120 5]
Dec 18 15:04:57X-GA-X58A-UD7 NetworkManager[1827]: <warn>  [1513605897.4161]device (eth2): Activation: failed for connection 'Wired connection 2'
Dec 18 15:04:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605897.4170]device (eth2): state change: failed -> disconnected (reason'none') [120 30 0]
Dec 18 15:04:57X-GA-X58A-UD7 avahi-daemon[1584]: Withdrawing address record forfe80::4d61:e9b2:98cd:aefa on eth2.
Dec 18 15:04:57X-GA-X58A-UD7 avahi-daemon[1584]: Leaving mDNS multicast group oninterface eth2.IPv6 with address fe80::4d61:e9b2:98cd:aefa.
Dec 18 15:04:57X-GA-X58A-UD7 avahi-daemon[1584]: Interface eth2.IPv6 no longerrelevant for mDNS.
Dec 18 15:04:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605897.4215]policy: auto-activating connection 'Wired connection 2'
Dec 18 15:04:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605897.4230]device (eth2): Activation: starting connection 'Wired connection 2'(a98d58b2-6397-3af5-b113-858cff6ccc3e)
Dec 18 15:04:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605897.4232]device (eth2): state change: disconnected -> prepare (reason'none') [30 40 0]
Dec 18 15:04:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605897.4236]device (eth2): state change: prepare -> config (reason 'none') [4050 0]
Dec 18 15:04:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605897.4240]device (eth2): state change: config -> ip-config (reason 'none')[50 70 0]
Dec 18 15:04:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605897.4243]dhcp4 (eth2): activation: beginning transaction (timeout in 45seconds)
Dec 18 15:04:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605897.4256]dhcp4 (eth2): dhclient started with pid 4495
Dec 18 15:04:57X-GA-X58A-UD7 dhclient[4495]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 3 (xid=0xefe68835)
Dec 18 15:04:58X-GA-X58A-UD7 avahi-daemon[1584]: Joining mDNS multicast group oninterface eth2.IPv6 with address fe80::4d61:e9b2:98cd:aefa.
Dec 18 15:04:58X-GA-X58A-UD7 avahi-daemon[1584]: New relevant interface eth2.IPv6for mDNS.
Dec 18 15:04:58X-GA-X58A-UD7 avahi-daemon[1584]: Registering new address record forfe80::4d61:e9b2:98cd:aefa on eth2.*.
Dec 18 15:05:00X-GA-X58A-UD7 dhclient[4495]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 7 (xid=0xefe68835)
Dec 18 15:05:01X-GA-X58A-UD7 CRON[4535]: (root) CMD (if [ -x/etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then/etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Dec 18 15:05:01X-GA-X58A-UD7 CRON[4536]: (munin) CMD (if [ -x /usr/bin/munin-cron ];then /usr/bin/munin-cron; fi)
Dec 18 15:05:01X-GA-X58A-UD7 CRON[4537]: (root) CMD (command -v debian-sa1 >/dev/null && debian-sa1 1 1)
Dec 18 15:05:07X-GA-X58A-UD7 dhclient[4495]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 10 (xid=0xefe68835)
Dec 18 15:05:17X-GA-X58A-UD7 dhclient[4495]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 8 (xid=0xefe68835)
Dec 18 15:05:25X-GA-X58A-UD7 dhclient[4495]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 13 (xid=0xefe68835)
Dec 18 15:05:38X-GA-X58A-UD7 dhclient[4495]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 21 (xid=0xefe68835)
Dec 18 15:05:42X-GA-X58A-UD7 NetworkManager[1827]: <warn>  [1513605942.3502]dhcp4 (eth2): request timed out
Dec 18 15:05:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605942.3503]dhcp4 (eth2): state changed unknown -> timeout
Dec 18 15:05:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605942.3824]dhcp4 (eth2): canceled DHCP transaction, DHCP client pid 4495
Dec 18 15:05:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605942.3825]dhcp4 (eth2): state changed timeout -> done
Dec 18 15:05:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605942.3827]device (eth2): state change: ip-config -> failed (reason'ip-config-unavailable') [70 120 5]
Dec 18 15:05:42X-GA-X58A-UD7 NetworkManager[1827]: <warn>  [1513605942.3830]device (eth2): Activation: failed for connection 'Wired connection 2'
Dec 18 15:05:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605942.3835]device (eth2): state change: failed -> disconnected (reason'none') [120 30 0]
Dec 18 15:05:42X-GA-X58A-UD7 avahi-daemon[1584]: Withdrawing address record forfe80::4d61:e9b2:98cd:aefa on eth2.
Dec 18 15:05:42X-GA-X58A-UD7 avahi-daemon[1584]: Leaving mDNS multicast group oninterface eth2.IPv6 with address fe80::4d61:e9b2:98cd:aefa.
Dec 18 15:05:42X-GA-X58A-UD7 avahi-daemon[1584]: Interface eth2.IPv6 no longerrelevant for mDNS.
Dec 18 15:05:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605942.3860]policy: auto-activating connection 'Wired connection 2'
Dec 18 15:05:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605942.3869]device (eth2): Activation: starting connection 'Wired connection 2'(a98d58b2-6397-3af5-b113-858cff6ccc3e)
Dec 18 15:05:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605942.3871]device (eth2): state change: disconnected -> prepare (reason'none') [30 40 0]
Dec 18 15:05:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605942.3875]device (eth2): state change: prepare -> config (reason 'none') [4050 0]
Dec 18 15:05:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605942.3888]device (eth2): state change: config -> ip-config (reason 'none')[50 70 0]
Dec 18 15:05:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605942.3891]dhcp4 (eth2): activation: beginning transaction (timeout in 45seconds)
Dec 18 15:05:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605942.3906]dhcp4 (eth2): dhclient started with pid 6507
Dec 18 15:05:42X-GA-X58A-UD7 dhclient[6507]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 3 (xid=0xd4bfb44d)
Dec 18 15:05:44X-GA-X58A-UD7 avahi-daemon[1584]: Joining mDNS multicast group oninterface eth2.IPv6 with address fe80::4d61:e9b2:98cd:aefa.
Dec 18 15:05:44X-GA-X58A-UD7 avahi-daemon[1584]: New relevant interface eth2.IPv6for mDNS.
Dec 18 15:05:44X-GA-X58A-UD7 avahi-daemon[1584]: Registering new address record forfe80::4d61:e9b2:98cd:aefa on eth2.*.
Dec 18 15:05:45X-GA-X58A-UD7 dhclient[6507]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 6 (xid=0xd4bfb44d)
Dec 18 15:05:51X-GA-X58A-UD7 dhclient[6507]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 14 (xid=0xd4bfb44d)
Dec 18 15:06:05X-GA-X58A-UD7 dhclient[6507]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 11 (xid=0xd4bfb44d)
Dec 18 15:06:16X-GA-X58A-UD7 dhclient[6507]: DHCPDISCOVER on eth2 to 255.255.255.255port 67 interval 20 (xid=0xd4bfb44d)
Dec 18 15:06:27X-GA-X58A-UD7 NetworkManager[1827]: <warn>  [1513605987.3502]dhcp4 (eth2): request timed out
Dec 18 15:06:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605987.3503]dhcp4 (eth2): state changed unknown -> timeout
Dec 18 15:06:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605987.3824]dhcp4 (eth2): canceled DHCP transaction, DHCP client pid 6507
Dec 18 15:06:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605987.3824]dhcp4 (eth2): state changed timeout -> done
Dec 18 15:06:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605987.3826]device (eth2): state change: ip-config -> failed (reason'ip-config-unavailable') [70 120 5]
Dec 18 15:06:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605987.3827]policy: disabling autoconnect for connection 'Wired connection 2'.
Dec 18 15:06:27X-GA-X58A-UD7 NetworkManager[1827]: <warn>  [1513605987.3829]device (eth2): Activation: failed for connection 'Wired connection 2'
Dec 18 15:06:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513605987.3832]device (eth2): state change: failed -> disconnected (reason'none') [120 30 0]
Dec 18 15:06:27X-GA-X58A-UD7 avahi-daemon[1584]: Withdrawing address record forfe80::4d61:e9b2:98cd:aefa on eth2.
Dec 18 15:06:27X-GA-X58A-UD7 avahi-daemon[1584]: Leaving mDNS multicast group oninterface eth2.IPv6 with address fe80::4d61:e9b2:98cd:aefa.
Dec 18 15:06:27X-GA-X58A-UD7 avahi-daemon[1584]: Interface eth2.IPv6 no longerrelevant for mDNS.
Dec 18 15:06:29X-GA-X58A-UD7 ntpd[7515]: Deleting interface #101 eth2,fe80::4d61:e9b2:98cd:aefa%2#123, interface stats: received=0, sent=0,dropped=0, active_time=178 secs
Dec 18 15:06:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_name: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:06:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_description: assertion 'G_IS_APP_INFO (appinfo)'failed
Dec 18 15:06:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_icon: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:06:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:06:45.590] Could notload desktop item: Object reference not set to an instance of anobject
Dec 18 15:06:45X-GA-X58A-UD7 gnome-session[11979]: Could not locate Tomboy on D-Bus.Perhaps it's not running?
Dec 18 15:06:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:06:45.636][UniverseManager] Error while updating item source "Torrents":Cannot access Transmission RPC service
Dec 18 15:07:19X-GA-X58A-UD7 gnome-session[11979]:[15538:15624:1218/150719.041750:ERROR:service_manager.cc(157)]Connection InterfaceProviderSpec prevented service: content_rendererfrom binding interface: blink::mojom::ReportingServiceProxy exposedby: content_browser
Dec 18 15:07:57X-GA-X58A-UD7 gnome-session[11979]: Gtk-Message: GtkDialog mappedwithout a transient parent. This is discouraged.
Dec 18 15:07:57X-GA-X58A-UD7 dbus[1594]: [system] Activating via systemd: servicename='org.freedesktop.hostname1'unit='dbus-org.freedesktop.hostname1.service'
Dec 18 15:07:57X-GA-X58A-UD7 systemd[1]: Starting Hostname Service...
Dec 18 15:07:57X-GA-X58A-UD7 dbus[1594]: [system] Successfully activated service'org.freedesktop.hostname1'
Dec 18 15:07:57X-GA-X58A-UD7 systemd[1]: Started Hostname Service.
Dec 18 15:07:57X-GA-X58A-UD7 org.gtk.vfs.Daemon[11820]: ** (process:15428): WARNING**: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' onobject at path /org/gtk/vfs/client/enumerator/9 (g-dbus-error-quark,19)
Dec 18 15:07:57X-GA-X58A-UD7 org.gtk.vfs.Daemon[11820]: ** (process:15428): WARNING**: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' onobject at path /org/gtk/vfs/client/enumerator/9 (g-dbus-error-quark,19)
Dec 18 15:07:57X-GA-X58A-UD7 org.gtk.vfs.Daemon[11820]: ** (process:15428): WARNING**: send_done_cb: No such interface 'org.gtk.vfs.Enumerator' onobject at path /org/gtk/vfs/client/enumerator/9 (g-dbus-error-quark,19)
Dec 18 15:08:14X-GA-X58A-UD7 gnome-session[11979]: Traceback (most recent calllast):
Dec 18 15:08:14X-GA-X58A-UD7 gnome-session[11979]:   File"/usr/share/nautilus-python/extensions/RabbitVCS.py", line392, in get_file_items_full
Dec 18 15:08:14X-GA-X58A-UD7 gnome-session[11979]:     menu =NautilusMainContextMenu(self, window.base_dir, paths,conditions).get_menu()
Dec 18 15:08:14X-GA-X58A-UD7 gnome-session[11979]: AttributeError:'NautilusDesktopWindow' object has no attribute 'base_dir'
Dec 18 15:08:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_name: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:08:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_description: assertion 'G_IS_APP_INFO (appinfo)'failed
Dec 18 15:08:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_icon: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:08:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:08:45.639] Could notload desktop item: Object reference not set to an instance of anobject
Dec 18 15:08:45X-GA-X58A-UD7 gnome-session[11979]: Could not locate Tomboy on D-Bus.Perhaps it's not running?
Dec 18 15:08:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:08:45.693][UniverseManager] Error while updating item source "Torrents":Cannot access Transmission RPC service
Dec 18 15:09:01X-GA-X58A-UD7 CRON[13884]: (root) CMD (  [ -x/usr/lib/php5/maxlifetime ] && [ -x/usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] &&/usr/lib/php5/sessionclean /var/lib/php5$(/usr/lib/php5/maxlifetime))
Dec 18 15:09:01X-GA-X58A-UD7 CRON[13883]: (root) CMD (  [ -x/usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Dec 18 15:10:01X-GA-X58A-UD7 CRON[16277]: (root) CMD (test -x /usr/lib/atsar/atsa1&& /usr/lib/atsar/atsa1)
Dec 18 15:10:01X-GA-X58A-UD7 CRON[16276]: (root) CMD (if [ -x/etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then/etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Dec 18 15:10:01X-GA-X58A-UD7 CRON[16278]: (munin) CMD (if [ -x /usr/bin/munin-cron]; then /usr/bin/munin-cron; fi)
Dec 18 15:10:16X-GA-X58A-UD7 gnome-session[11979]:[15538:15624:1218/151016.199547:ERROR:service_manager.cc(157)]Connection InterfaceProviderSpec prevented service: content_rendererfrom binding interface: blink::mojom::ReportingServiceProxy exposedby: content_browser
Dec 18 15:10:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_name: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:10:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_description: assertion 'G_IS_APP_INFO (appinfo)'failed
Dec 18 15:10:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_icon: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:10:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:10:45.695] Could notload desktop item: Object reference not set to an instance of anobject
Dec 18 15:10:45X-GA-X58A-UD7 gnome-session[11979]: Could not locate Tomboy on D-Bus.Perhaps it's not running?
Dec 18 15:10:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:10:45.744][UniverseManager] Error while updating item source "Torrents":Cannot access Transmission RPC service
Dec 18 15:11:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606287.4177]policy: auto-activating connection 'Wired connection 2'
Dec 18 15:11:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606287.4185]device (eth2): Activation: starting connection 'Wired connection 2'(a98d58b2-6397-3af5-b113-858cff6ccc3e)
Dec 18 15:11:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606287.4186]device (eth2): state change: disconnected -> prepare (reason'none') [30 40 0]
Dec 18 15:11:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606287.4189]device (eth2): state change: prepare -> config (reason 'none') [4050 0]
Dec 18 15:11:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606287.4193]device (eth2): state change: config -> ip-config (reason 'none')[50 70 0]
Dec 18 15:11:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606287.4196]dhcp4 (eth2): activation: beginning transaction (timeout in 45seconds)
Dec 18 15:11:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606287.4206]dhcp4 (eth2): dhclient started with pid 20085
Dec 18 15:11:27X-GA-X58A-UD7 dhclient[20085]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 3 (xid=0x9305669)
Dec 18 15:11:28X-GA-X58A-UD7 avahi-daemon[1584]: Joining mDNS multicast group oninterface eth2.IPv6 with address fe80::4d61:e9b2:98cd:aefa.
Dec 18 15:11:28X-GA-X58A-UD7 avahi-daemon[1584]: New relevant interface eth2.IPv6for mDNS.
Dec 18 15:11:28X-GA-X58A-UD7 avahi-daemon[1584]: Registering new address record forfe80::4d61:e9b2:98cd:aefa on eth2.*.
Dec 18 15:11:30X-GA-X58A-UD7 ntpd[7515]: Listen normally on 102 eth2[fe80::4d61:e9b2:98cd:aefa%2]:123
Dec 18 15:11:30X-GA-X58A-UD7 ntpd[7515]: new interface(s) found: waking up resolver
Dec 18 15:11:30X-GA-X58A-UD7 dhclient[20085]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 7 (xid=0x9305669)
Dec 18 15:11:37X-GA-X58A-UD7 dhclient[20085]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 15 (xid=0x9305669)
Dec 18 15:11:52X-GA-X58A-UD7 dhclient[20085]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 8 (xid=0x9305669)
Dec 18 15:11:55X-GA-X58A-UD7 gnome-session[11979]:[15538:15624:1218/151155.646855:ERROR:service_manager.cc(157)]Connection InterfaceProviderSpec prevented service: content_rendererfrom binding interface: blink::mojom::ReportingServiceProxy exposedby: content_browser
Dec 18 15:12:00X-GA-X58A-UD7 dhclient[20085]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 8 (xid=0x9305669)
Dec 18 15:12:08X-GA-X58A-UD7 dhclient[20085]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 8 (xid=0x9305669)
Dec 18 15:12:12X-GA-X58A-UD7 NetworkManager[1827]: <warn>  [1513606332.3502]dhcp4 (eth2): request timed out

```

---

### Post by crazybear on 2017-12-20
Part two of crash log here:
```



Dec 18 15:12:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606332.3502]dhcp4 (eth2): state changed unknown -> timeout
Dec 18 15:12:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606332.3824]dhcp4 (eth2): canceled DHCP transaction, DHCP client pid 20085
Dec 18 15:12:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606332.3824]dhcp4 (eth2): state changed timeout -> done
Dec 18 15:12:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606332.3826]device (eth2): state change: ip-config -> failed (reason'ip-config-unavailable') [70 120 5]
Dec 18 15:12:12X-GA-X58A-UD7 NetworkManager[1827]: <warn>  [1513606332.3830]device (eth2): Activation: failed for connection 'Wired connection 2'
Dec 18 15:12:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606332.3836]device (eth2): state change: failed -> disconnected (reason'none') [120 30 0]
Dec 18 15:12:12X-GA-X58A-UD7 avahi-daemon[1584]: Withdrawing address record forfe80::4d61:e9b2:98cd:aefa on eth2.
Dec 18 15:12:12X-GA-X58A-UD7 avahi-daemon[1584]: Leaving mDNS multicast group oninterface eth2.IPv6 with address fe80::4d61:e9b2:98cd:aefa.
Dec 18 15:12:12X-GA-X58A-UD7 avahi-daemon[1584]: Interface eth2.IPv6 no longerrelevant for mDNS.
Dec 18 15:12:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606332.3873]policy: auto-activating connection 'Wired connection 2'
Dec 18 15:12:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606332.3881]device (eth2): Activation: starting connection 'Wired connection 2'(a98d58b2-6397-3af5-b113-858cff6ccc3e)
Dec 18 15:12:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606332.3883]device (eth2): state change: disconnected -> prepare (reason'none') [30 40 0]
Dec 18 15:12:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606332.3887]device (eth2): state change: prepare -> config (reason 'none') [4050 0]
Dec 18 15:12:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606332.3909]device (eth2): state change: config -> ip-config (reason 'none')[50 70 0]
Dec 18 15:12:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606332.3913]dhcp4 (eth2): activation: beginning transaction (timeout in 45seconds)
Dec 18 15:12:12X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606332.3924]dhcp4 (eth2): dhclient started with pid 22431
Dec 18 15:12:12X-GA-X58A-UD7 dhclient[22431]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 3 (xid=0xbb72685b)
Dec 18 15:12:13X-GA-X58A-UD7 avahi-daemon[1584]: Joining mDNS multicast group oninterface eth2.IPv6 with address fe80::4d61:e9b2:98cd:aefa.
Dec 18 15:12:13X-GA-X58A-UD7 avahi-daemon[1584]: New relevant interface eth2.IPv6for mDNS.
Dec 18 15:12:13X-GA-X58A-UD7 avahi-daemon[1584]: Registering new address record forfe80::4d61:e9b2:98cd:aefa on eth2.*.
Dec 18 15:12:15X-GA-X58A-UD7 dhclient[22431]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 8 (xid=0xbb72685b)
Dec 18 15:12:23X-GA-X58A-UD7 dhclient[22431]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 8 (xid=0xbb72685b)
Dec 18 15:12:31X-GA-X58A-UD7 dhclient[22431]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 11 (xid=0xbb72685b)
Dec 18 15:12:42X-GA-X58A-UD7 dhclient[22431]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 18 (xid=0xbb72685b)
Dec 18 15:12:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_name: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:12:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_description: assertion 'G_IS_APP_INFO (appinfo)'failed
Dec 18 15:12:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_icon: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:12:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:12:45.746] Could notload desktop item: Object reference not set to an instance of anobject
Dec 18 15:12:45X-GA-X58A-UD7 gnome-session[11979]: Could not locate Tomboy on D-Bus.Perhaps it's not running?
Dec 18 15:12:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:12:45.790][UniverseManager] Error while updating item source "Torrents":Cannot access Transmission RPC service
Dec 18 15:12:57X-GA-X58A-UD7 NetworkManager[1827]: <warn>  [1513606377.3433]dhcp4 (eth2): request timed out
Dec 18 15:12:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606377.3434]dhcp4 (eth2): state changed unknown -> timeout
Dec 18 15:12:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606377.3755]dhcp4 (eth2): canceled DHCP transaction, DHCP client pid 22431
Dec 18 15:12:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606377.3755]dhcp4 (eth2): state changed timeout -> done
Dec 18 15:12:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606377.3757]device (eth2): state change: ip-config -> failed (reason'ip-config-unavailable') [70 120 5]
Dec 18 15:12:57X-GA-X58A-UD7 NetworkManager[1827]: <warn>  [1513606377.3760]device (eth2): Activation: failed for connection 'Wired connection 2'
Dec 18 15:12:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606377.3763]device (eth2): state change: failed -> disconnected (reason'none') [120 30 0]
Dec 18 15:12:57X-GA-X58A-UD7 avahi-daemon[1584]: Withdrawing address record forfe80::4d61:e9b2:98cd:aefa on eth2.
Dec 18 15:12:57X-GA-X58A-UD7 avahi-daemon[1584]: Leaving mDNS multicast group oninterface eth2.IPv6 with address fe80::4d61:e9b2:98cd:aefa.
Dec 18 15:12:57X-GA-X58A-UD7 avahi-daemon[1584]: Interface eth2.IPv6 no longerrelevant for mDNS.
Dec 18 15:12:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606377.3790]policy: auto-activating connection 'Wired connection 2'
Dec 18 15:12:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606377.3808]device (eth2): Activation: starting connection 'Wired connection 2'(a98d58b2-6397-3af5-b113-858cff6ccc3e)
Dec 18 15:12:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606377.3810]device (eth2): state change: disconnected -> prepare (reason'none') [30 40 0]
Dec 18 15:12:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606377.3813]device (eth2): state change: prepare -> config (reason 'none') [4050 0]
Dec 18 15:12:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606377.3827]device (eth2): state change: config -> ip-config (reason 'none')[50 70 0]
Dec 18 15:12:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606377.3830]dhcp4 (eth2): activation: beginning transaction (timeout in 45seconds)
Dec 18 15:12:57X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606377.3841]dhcp4 (eth2): dhclient started with pid 23842
Dec 18 15:12:57X-GA-X58A-UD7 dhclient[23842]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 3 (xid=0x343f8741)
Dec 18 15:12:59X-GA-X58A-UD7 avahi-daemon[1584]: Joining mDNS multicast group oninterface eth2.IPv6 with address fe80::4d61:e9b2:98cd:aefa.
Dec 18 15:12:59X-GA-X58A-UD7 avahi-daemon[1584]: New relevant interface eth2.IPv6for mDNS.
Dec 18 15:12:59X-GA-X58A-UD7 avahi-daemon[1584]: Registering new address record forfe80::4d61:e9b2:98cd:aefa on eth2.*.
Dec 18 15:13:00X-GA-X58A-UD7 dhclient[23842]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 6 (xid=0x343f8741)
Dec 18 15:13:06X-GA-X58A-UD7 dhclient[23842]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 6 (xid=0x343f8741)
Dec 18 15:13:12X-GA-X58A-UD7 dhclient[23842]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 13 (xid=0x343f8741)
Dec 18 15:13:25X-GA-X58A-UD7 dhclient[23842]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 18 (xid=0x343f8741)
Dec 18 15:13:42X-GA-X58A-UD7 NetworkManager[1827]: <warn>  [1513606422.3514]dhcp4 (eth2): request timed out
Dec 18 15:13:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606422.3514]dhcp4 (eth2): state changed unknown -> timeout
Dec 18 15:13:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606422.3836]dhcp4 (eth2): canceled DHCP transaction, DHCP client pid 23842
Dec 18 15:13:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606422.3836]dhcp4 (eth2): state changed timeout -> done
Dec 18 15:13:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606422.3838]device (eth2): state change: ip-config -> failed (reason'ip-config-unavailable') [70 120 5]
Dec 18 15:13:42X-GA-X58A-UD7 NetworkManager[1827]: <warn>  [1513606422.3841]device (eth2): Activation: failed for connection 'Wired connection 2'
Dec 18 15:13:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606422.3846]device (eth2): state change: failed -> disconnected (reason'none') [120 30 0]
Dec 18 15:13:42X-GA-X58A-UD7 avahi-daemon[1584]: Withdrawing address record forfe80::4d61:e9b2:98cd:aefa on eth2.
Dec 18 15:13:42X-GA-X58A-UD7 avahi-daemon[1584]: Leaving mDNS multicast group oninterface eth2.IPv6 with address fe80::4d61:e9b2:98cd:aefa.
Dec 18 15:13:42X-GA-X58A-UD7 avahi-daemon[1584]: Interface eth2.IPv6 no longerrelevant for mDNS.
Dec 18 15:13:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606422.3869]policy: auto-activating connection 'Wired connection 2'
Dec 18 15:13:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606422.3887]device (eth2): Activation: starting connection 'Wired connection 2'(a98d58b2-6397-3af5-b113-858cff6ccc3e)
Dec 18 15:13:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606422.3889]device (eth2): state change: disconnected -> prepare (reason'none') [30 40 0]
Dec 18 15:13:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606422.3893]device (eth2): state change: prepare -> config (reason 'none') [4050 0]
Dec 18 15:13:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606422.3902]device (eth2): state change: config -> ip-config (reason 'none')[50 70 0]
Dec 18 15:13:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606422.3906]dhcp4 (eth2): activation: beginning transaction (timeout in 45seconds)
Dec 18 15:13:42X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606422.3918]dhcp4 (eth2): dhclient started with pid 25279
Dec 18 15:13:42X-GA-X58A-UD7 dhclient[25279]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 3 (xid=0xad788210)
Dec 18 15:13:44X-GA-X58A-UD7 avahi-daemon[1584]: Joining mDNS multicast group oninterface eth2.IPv6 with address fe80::4d61:e9b2:98cd:aefa.
Dec 18 15:13:44X-GA-X58A-UD7 avahi-daemon[1584]: New relevant interface eth2.IPv6for mDNS.
Dec 18 15:13:44X-GA-X58A-UD7 avahi-daemon[1584]: Registering new address record forfe80::4d61:e9b2:98cd:aefa on eth2.*.
Dec 18 15:13:45X-GA-X58A-UD7 dhclient[25279]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 7 (xid=0xad788210)
Dec 18 15:13:52X-GA-X58A-UD7 dhclient[25279]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 20 (xid=0xad788210)
Dec 18 15:14:12X-GA-X58A-UD7 dhclient[25279]: DHCPDISCOVER on eth2 to255.255.255.255 port 67 interval 16 (xid=0xad788210)
Dec 18 15:14:27X-GA-X58A-UD7 NetworkManager[1827]: <warn>  [1513606467.3501]dhcp4 (eth2): request timed out
Dec 18 15:14:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606467.3502]dhcp4 (eth2): state changed unknown -> timeout
Dec 18 15:14:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606467.3825]dhcp4 (eth2): canceled DHCP transaction, DHCP client pid 25279
Dec 18 15:14:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606467.3825]dhcp4 (eth2): state changed timeout -> done
Dec 18 15:14:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606467.3827]device (eth2): state change: ip-config -> failed (reason'ip-config-unavailable') [70 120 5]
Dec 18 15:14:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606467.3828]policy: disabling autoconnect for connection 'Wired connection 2'.
Dec 18 15:14:27X-GA-X58A-UD7 NetworkManager[1827]: <warn>  [1513606467.3830]device (eth2): Activation: failed for connection 'Wired connection 2'
Dec 18 15:14:27X-GA-X58A-UD7 NetworkManager[1827]: <info>  [1513606467.3834]device (eth2): state change: failed -> disconnected (reason'none') [120 30 0]
Dec 18 15:14:27X-GA-X58A-UD7 avahi-daemon[1584]: Withdrawing address record forfe80::4d61:e9b2:98cd:aefa on eth2.
Dec 18 15:14:27X-GA-X58A-UD7 avahi-daemon[1584]: Leaving mDNS multicast group oninterface eth2.IPv6 with address fe80::4d61:e9b2:98cd:aefa.
Dec 18 15:14:27X-GA-X58A-UD7 avahi-daemon[1584]: Interface eth2.IPv6 no longerrelevant for mDNS.
Dec 18 15:14:29X-GA-X58A-UD7 ntpd[7515]: Deleting interface #102 eth2,fe80::4d61:e9b2:98cd:aefa%2#123, interface stats: received=0, sent=0,dropped=0, active_time=179 secs
Dec 18 15:14:34X-GA-X58A-UD7 gnome-session[11979]: Gtk-Message: GtkDialog mappedwithout a transient parent. This is discouraged.
Dec 18 15:14:34X-GA-X58A-UD7 dbus[1594]: [system] Activating via systemd: servicename='org.freedesktop.hostname1'unit='dbus-org.freedesktop.hostname1.service'
Dec 18 15:14:34X-GA-X58A-UD7 systemd[1]: Starting Hostname Service...
Dec 18 15:14:34X-GA-X58A-UD7 dbus[1594]: [system] Successfully activated service'org.freedesktop.hostname1'
Dec 18 15:14:34X-GA-X58A-UD7 systemd[1]: Started Hostname Service.
Dec 18 15:14:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_name: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:14:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_description: assertion 'G_IS_APP_INFO (appinfo)'failed
Dec 18 15:14:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_icon: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:14:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:14:45.792] Could notload desktop item: Object reference not set to an instance of anobject
Dec 18 15:14:45X-GA-X58A-UD7 gnome-session[11979]: Could not locate Tomboy on D-Bus.Perhaps it's not running?
Dec 18 15:14:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:14:45.842][UniverseManager] Error while updating item source "Torrents":Cannot access Transmission RPC service
Dec 18 15:14:53X-GA-X58A-UD7 gnome-session[11979]: Traceback (most recent calllast):
Dec 18 15:14:53X-GA-X58A-UD7 gnome-session[11979]:   File"/usr/share/nautilus-python/extensions/RabbitVCS.py", line392, in get_file_items_full
Dec 18 15:14:53X-GA-X58A-UD7 gnome-session[11979]:     menu =NautilusMainContextMenu(self, window.base_dir, paths,conditions).get_menu()
Dec 18 15:14:53X-GA-X58A-UD7 gnome-session[11979]: AttributeError:'NautilusDesktopWindow' object has no attribute 'base_dir'
Dec 18 15:15:01X-GA-X58A-UD7 CRON[28234]: (root) CMD (command -v debian-sa1 >/dev/null && debian-sa1 1 1)
Dec 18 15:15:01X-GA-X58A-UD7 CRON[28235]: (root) CMD (if [ -x/etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then/etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Dec 18 15:15:01X-GA-X58A-UD7 CRON[28236]: (munin) CMD (if [ -x /usr/bin/munin-cron]; then /usr/bin/munin-cron; fi)
Dec 18 15:15:33X-GA-X58A-UD7 gnome-session[11979]:[15538:15624:1218/151533.416451:ERROR:service_manager.cc(157)]Connection InterfaceProviderSpec prevented service: content_rendererfrom binding interface: blink::mojom::ReportingServiceProxy exposedby: content_browser
Dec 18 15:16:20X-GA-X58A-UD7 hddtemp[7672]: /dev/sda: WDC WD5000AAKB-00H8A0: 27 C
Dec 18 15:16:20X-GA-X58A-UD7 hddtemp[7672]: /dev/sdb: WDC WD1502FAEX-007BA0: 30 C
Dec 18 15:16:20X-GA-X58A-UD7 hddtemp[7672]: /dev/sdc: WDC WD2005FBYZ-01YCBB1: 28 C
Dec 18 15:16:20X-GA-X58A-UD7 hddtemp[7672]: /dev/sde: WDC WD1005FBYZ-01YCBB1: 28 C
Dec 18 15:16:20X-GA-X58A-UD7 hddtemp[7672]: /dev/sdf: WDC WD2003FZEX-00Z4SA0: 30 C
Dec 18 15:16:20X-GA-X58A-UD7 hddtemp[7672]: /dev/sdg: WDC WD3003FZEX-00Z4SA0: 28 C
Dec 18 15:16:20X-GA-X58A-UD7 hddtemp[7672]: /dev/sdh: WDC WD3003FZEX-00Z4SA0: 28 C
Dec 18 15:16:38X-GA-X58A-UD7 gnome-session[11979]: Gtk-Message: GtkDialog mappedwithout a transient parent. This is discouraged.
Dec 18 15:16:39X-GA-X58A-UD7 dbus[1594]: [system] Activating via systemd: servicename='org.freedesktop.hostname1'unit='dbus-org.freedesktop.hostname1.service'
Dec 18 15:16:39X-GA-X58A-UD7 systemd[1]: Starting Hostname Service...
Dec 18 15:16:39X-GA-X58A-UD7 dbus[1594]: [system] Successfully activated service'org.freedesktop.hostname1'
Dec 18 15:16:39X-GA-X58A-UD7 systemd[1]: Started Hostname Service.
Dec 18 15:16:39X-GA-X58A-UD7 org.gtk.vfs.Daemon[11820]: ** (process:15428): WARNING**: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' onobject at path /org/gtk/vfs/client/enumerator/13 (g-dbus-error-quark,19)
Dec 18 15:16:39X-GA-X58A-UD7 org.gtk.vfs.Daemon[11820]: ** (process:15428): WARNING**: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' onobject at path /org/gtk/vfs/client/enumerator/13 (g-dbus-error-quark,19)
Dec 18 15:16:39X-GA-X58A-UD7 org.gtk.vfs.Daemon[11820]: ** (process:15428): WARNING**: send_done_cb: No such interface 'org.gtk.vfs.Enumerator' onobject at path /org/gtk/vfs/client/enumerator/13 (g-dbus-error-quark,19)
Dec 18 15:16:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_name: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:16:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_description: assertion 'G_IS_APP_INFO (appinfo)'failed
Dec 18 15:16:45X-GA-X58A-UD7 gnome-session[11979]: (Do:15090): GLib-GIO-CRITICAL **:g_app_info_get_icon: assertion 'G_IS_APP_INFO (appinfo)' failed
Dec 18 15:16:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:16:45.844] Could notload desktop item: Object reference not set to an instance of anobject
Dec 18 15:16:45X-GA-X58A-UD7 gnome-session[11979]: Could not locate Tomboy on D-Bus.Perhaps it's not running?
Dec 18 15:16:45X-GA-X58A-UD7 gnome-session[11979]: [Error 15:16:45.897][UniverseManager] Error while updating item source "Torrents":Cannot access Transmission RPC service
Dec 18 15:16:51X-GA-X58A-UD7 gnome-session[11979]: Traceback (most recent calllast):
Dec 18 15:16:51X-GA-X58A-UD7 gnome-session[11979]:   File"/usr/share/nautilus-python/extensions/RabbitVCS.py", line392, in get_file_items_full
Dec 18 15:16:51X-GA-X58A-UD7 gnome-session[11979]:     menu =NautilusMainContextMenu(self, window.base_dir, paths,conditions).get_menu()
Dec 18 15:16:51X-GA-X58A-UD7 gnome-session[11979]: AttributeError:'NautilusDesktopWindow' object has no attribute 'base_dir'
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00Dec18 15:19:41 X-GA-X58A-UD7 rsyslogd: [origin software="rsyslogd"

```

---

### Post by dragonfly41 on 2017-12-20
Looks like gnome-do package needs investigating.

---

### Post by QIII on 2017-12-20
Thanks, dragonfly.  But I think the OP might appreciate a bit more detail.  ; )

---

### Post by crazybear on 2017-12-20
> **dragonfly41 said:**
> Looks like gnome-do package needs investigating.

It is a little program that adds on to Gnome desktop. I just reinstalled it and updated it. If I suspect it is a problem, it is easy to live without. It is only a minor convenience launching programs. I will wait until the next crash and see if I can see a pattern in the logs. So far, to my untrained eye, each crash lists different things in the 'warnings'....so I think I'm looking at the wrong log...and seeing the results not the event that is causing the problem.

---

### Post by crazybear on 2018-02-18
Well, it has been a long time....for reasons unknown [perhaps updates and new kernels] the computer is quite stable now - the fuzzy monitors are still a problem and I guess I'll just hope that 18.04 doesn't have them. I never really figured out the problem causing the crashes. I think the last one was a month ago - so they haven't stopped, but certainly have decreased.

---

### Post by oskar12 on 2018-02-19
It happened to me as well!! Installed Ubuntu Studio, launched it for the second time and entire Desktop Icons were off. Just X sign in every Folder of the entire Desktop. FireFox looks OK. ...I ve got installed and used 14.04 version before= Trusty Thar and got never experienced any such issue. What I had been done was just to upgrade and downloaded some software to update...and suddenly all gone. I think it is better to downgrade back to 14.04 Trusty Thar. Have no time and energy to tweak new version entirely. Cos a musician not a programmer!! This way U Studio distract artists and musicians...they need a tool to work not a childish gadget to play along with for a while.

---

### Post by mörgæs on 2018-02-19
> **crazybear said:**
> Well, it has been a long time....for reasons unknown [perhaps updates and new kernels] the computer is quite stable now - the fuzzy monitors are still a problem and I guess I'll just hope that 18.04 doesn't have them. I never really figured out the problem causing the crashes. I think the last one was a month ago - so they haven't stopped, but certainly have decreased.

In case other people are following the thread: Yes, it's possible that kernel updates have finally found their way back to 16.04. 

When dealing with 'mystery' problems it's always a good idea to test various releases against each other. Maybe the problem could have been solved in November:
[https://ubuntuforums.org/showthread.php?t=2378204&page=4&p=13716379&viewfull=1#post13716379](https://ubuntuforums.org/showthread.php?t=2378204&page=4&p=13716379&viewfull=1#post13716379)

---

### Post by cruzer001 on 2018-02-19
Crashes/fuzzy monitor;  I wonder how the 4.4 kernel is holding up.

---

