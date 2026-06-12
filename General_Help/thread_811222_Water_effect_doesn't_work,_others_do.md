---
title: "Water effect doesn't work, others do"
date: 2008-05-28
forum: General Help
---

### Post by DouglasK on 2008-05-28
Hi, I can't get the Water effect to work.  I can get all the other effects to work fine including Motion blur, fire, etc.

Here's my basic system info...
Hardy Heron 8.04 (clean install)
nVidia binary driver
nVidia GeForce4 Ti 4200 Go AGP 8x

Is there anything more I should provide to help figure this out, or is it simply a hopeless case?

~~Douglas

---

### Post by brnetonboy on 2008-05-29
I have the same problem. Same OS, my video card is integrated motherboard Dell...

---

### Post by FuturePilot on 2008-05-29
> **DouglasK said:**
> Hi, I can't get the Water effect to work.  I can get all the other effects to work fine including Motion blur, fire, etc.

Here's my basic system info...
Hardy Heron 8.04 (clean install)
nVidia binary driver
nVidia GeForce4 Ti 4200 Go AGP 8x

Is there anything more I should provide to help figure this out, or is it simply a hopeless case?

~~Douglas

Post the output of
```
glxinfo | grep GL_ARB_fragment
```

Your card may be too old to support the necessary pixelshaders needed for the water effects.

---

### Post by coombesy on 2008-06-29
Future Pilot,

i'm having the same problem as above. I'm using an ati mobility m6 LY card on a sony vaio with 512 ram.

Everything is working, cube, fire, switchers etc etc. The only problem i can find is the water effect.
glxinfo | grep GL_ARB_fragment returned nothing

here is glxinfo | grep GL_ARB*:
> :~$ glxinfo | grep GL_ARB*
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 


---

### Post by Forlong on 2008-06-29
coombesy, your graphics chip is definitely to old to be capable of that. Sorry.

---

### Post by vergeh on 2008-09-29
I think I'm having some alpha channel issues with water effects. All my windows go completely grey while the effect is running, and I lose my desktop overlay. I can see the ripples on the other desktops of my transparent cube.

Output of compiz-check:
 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


Output of glxinfo | grep GL_ARB_fragment:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 


*edit:* Oh, there's my graphics card info right there...

*edit 2:* Before and after shots!
Before:
[[IMG]http://img204.imageshack.us/img204/46/beforehz1.th.png[/IMG]](http://img204.imageshack.us/my.php?image=beforehz1.png)[[IMG]http://img204.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

After:
[[IMG]http://img175.imageshack.us/img175/2589/afterzt3.th.png[/IMG]](http://img175.imageshack.us/my.php?image=afterzt3.png)[[IMG]http://img175.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

*edit 3:* This also goes haywire when I enable bicubic filtering.

---

### Post by FerN(SA) on 2008-09-30
Hey, I also have the same graphics card (GeForce 4 Ti) and mine doesnt work either.  This is because our card doesnt support pixel shading or something along those lines.  We cant get water effect :(

---

### Post by borlosky on 2008-10-04
i had similar issue on clean install of hardy 64bit. found the issue to be with the bicubic filter in compiz. that is to say, with the filter enabled, i could get no water effects, (all other effects, 3dcube, fire, ect, still worked fine), but as soon as i turned the filter off, water worked fine. not sure why it worked that way, my pc has good enough stats to run everything with no issues (dual core intel 2.0, 2 gigs ddr2, 2x500gig sata hard drives, geforce 8600gt pci-e 512m ram.) but needless to say, just disabling the filter worked.

---

