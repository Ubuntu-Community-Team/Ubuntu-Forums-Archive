---
title: "GPU acceleration problem"
date: 2014-09-21
forum: General Help
---

### Post by bodaw117 on 2014-09-21
Hello guys,
I'm having issues while setting up hardware acceleration on my chromium - lenovo M5400 touch laptop.
I had installed pepper flash plugin
I have active [COLOR=#333333][FONT=Georgia]Override software rendering list 
but still output from chrome://gpu is still the same:

[/FONT][/COLOR]**Graphics Feature Status**


[LIST]
[*]Canvas: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Flash: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Flash Stage3D: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Flash Stage3D Baseline profile: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Compositing: [COLOR=#808000]Software only, threaded. Hardware acceleration unavailable[/COLOR]
[*]Rasterization: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Threaded Rasterization: [COLOR=#FF0000]Unavailable[/COLOR]
[*]Video Decode: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Video Encode: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]WebGL: [COLOR=#FF0000]Unavailable[/COLOR]
[/LIST]
[h=3]Problems Detected[/h]


[LIST]
[/LIST]

[LIST]
[*]GPU process was unable to boot: GPU access is disabled in chrome://settings.
*Disabled Features: [COLOR=#FF0000]all[/COLOR]*
[*][I]EXT_occlusion_query appears to be buggy with Intel GPUs on Linux
*Applied Workarounds: [COLOR=#808000]disable_ext_occlusion_query[/COLOR]*[/I]
[*][I][I]Clear uniforms before first program use on all platforms: [124764]("http://crbug.com/124764"), [349137]("http://crbug.com/349137")
*Applied Workarounds: [COLOR=#808000]clear_uniforms_before_first_program_use[/COLOR]*[/I][/I]
[*][I][I][I]Mesa drivers in Linux handle varyings without static use incorrectly: [333885]("http://crbug.com/333885")
*Applied Workarounds: [COLOR=#808000]count_all_in_varyings_packing[/COLOR]*[/I][/I][/I]
[*][I][I][I]Disable partial swaps on linux drivers: [339493]("http://crbug.com/339493")
*Applied Workarounds: [COLOR=#808000]disable_post_sub_buffers_for_onscreen_surfaces[/COLOR]*[/I][/I][/I]
[/LIST]

Can anyone help?[COLOR=#FF0000]
[/COLOR]

---

### Post by Rob Sayer on 2014-09-21
It's impossible to tell without knowing what video adapter you have.  See here:

[http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card](http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card)

POst the results from the terminal, using [CODE] tags for readability, which is important considering no one is being paid to do this.

---

### Post by bodaw117 on 2014-09-21
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)

---

### Post by gifford on 2014-09-21
Try disabling threaded Rasterization and WebGL. See if that does not correct your problem.

---

### Post by bodaw117 on 2014-09-21
no, actualy using this with flash player is much worse :-(

---

