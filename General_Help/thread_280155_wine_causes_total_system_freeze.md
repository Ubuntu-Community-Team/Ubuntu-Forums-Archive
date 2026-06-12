---
title: "wine causes total system freeze"
date: 2006-10-19
forum: General Help
---

### Post by Nakajoe on 2006-10-19
Hey everybody; I`ve done a lot of googling about this, but can`t find any answers; since there aren`t really any error messages, I`m not even sure what to specifically look for.

Running Drake, been using it for the past several months with no undue problems. However, I can`t get wine to work whatsoever. It seems to install fine, but every time I try to run it, or even winetools, the system says something about configuring a <home>/.wine directory and hangs after a couple of seconds. Cursor stops blinking, mouse pointer doesn`t move, no response to keyboard shortcuts, etc., and I end up doing a hard reboot. Anybody heard of this, or have any ideas/solutions?

---

### Post by aidanr on 2006-10-19
whats your free disk space like, do you have enough room for wine to set up the ~/.wine folder?

also run winecfg in the terminal and post the output if you can

---

### Post by Nakajoe on 2006-10-19
110Gb free space; forgot to say so earlier, sorry. winecfg also causes a total system freeze.

---

### Post by aidanr on 2006-10-19
try a different version? how did you install (from source, easyubuntu, automatix, synaptic?)

---

### Post by Old Pink on 2006-10-19
Try an older version, I had problems with the latest version. :)

---

### Post by Nakajoe on 2006-10-19
I`ve tried through Synapic and apt (which I suppose would get the same version). I tried to confirm the version with wine --version, but that causes a total system lock as well. I`ll try an older version and post the results. Thanks for the suggestions everybody.

---

### Post by Nakajoe on 2006-10-19
Tried older versions back to the oldest one winehq has up, they all freeze in the same way.

---

### Post by crumja on 2006-10-19
Remove all things wine related, including winetools.
Remove the .wine folder from your home directory.
Reinstall the latest wine from winehq.
Rune winecfg before running any other programs.

See how that goes.

---

### Post by Nakajoe on 2006-10-20
Well, that got me further than before; I at least got some sort of error message before it froze up. I copied it down in a notebook, here`s the output in its entirety:

wine: creating configuration directory /home/nakajoe/.wine
*****************WARN_ONCE**********************************
File r300_state.c function r300 Enable line 456
TODO - double side stencil!
************************************************************
NO ctx->FragmentProgram._Current!!
*****************WARN_ONCE**********************************
File r300_state.c function r300 Enable line 456
TODO - double side stencil!
************************************************************
NO ctx->FragmentProgram._Current!!
err:ntdll:RtlpWaitForCriticalSection section0x7e9c5000 "xlldrv_main.c:X11ORV_CritSection" wait timed out in thread 00c, blocked by 00b, retrying (60 sec)

That`s just my retyping, so spaces etc. might be a bit off. The lockup happens immediately (less than 1 sec) after the above message comes up. I went off and made and ate some lunch after seeing this, hoping that it might get around to that retry sometime, but no luck. Not real sure what to do with this, any ideas?

Thanks,
Joe

---

### Post by TrD on 2006-10-20
Im having problems with wine too. Every time I run winecfg or some program using the wine command my screen goes black and then im back at the login screen.

---

### Post by SpEcIeS on 2006-10-20
Happening here also. Tried **0.9.22** and **0.9.23** from [COLOR="Red"]*winehq*[/COLOR]. Not sure what is going on here, but has anyone tried compiling the source themselves? 

Going to try the Edgy packages first.

---

### Post by SpEcIeS on 2006-10-20
Ok.. here is the deal ...  tried out **[COLOR="DarkOrange"]Edgy[/COLOR]'s** wine and it did the same as the **[COLOR="Red"]winehq[/COLOR]'s** package; then I compiled, without problems, installed, but *winecfg* and *wine* produce a _*seg fault*_. The next thing is to try the git. ](*,)

Very odd. :confused:

---

### Post by crumja on 2006-10-20
The error message seems to indicate that your graphics renderer is having problems. You're probably using the r300 driver, which is not suited for wine (unstable at times and lacking in complete implementation). It might be against your values, but I recommend switching to fglrx (ati official driver) for all things wine related.

Let me know if that isn't the case and I guessed wrong. Also, can you post the outputs of glxinfo?

---

### Post by Nakajoe on 2006-10-24
Sorry for the late reply, job`s been rather turbulent lately... I`ll have a look at the driver. The (long) output of glxinfo is as follows:

name of display: :0.0
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20040924 AGP 1x TCL
OpenGL version string: 1.2 Mesa 6.4.1
OpenGL extensions:
    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample,
    GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_histogram, GL_EXT_packed_pixels,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent,
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

---

### Post by crumja on 2006-10-24
Yes, the 

*********************************WARN_ONCE******** *************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
************************************************** *************************

line shows that you're using r300 driver.

It's currently not feature complete and doesn't fully support the card. I'd recommend using fglrx if you want optimal wine compatibility.

---

### Post by Nakajoe on 2006-10-24
Well, after a couple hours of work I think I got the fglrx driver installed. My home system must be really weird, very very few installs go as they should. Builds from source without exception take many hours of error searching and configuration adjustment, when I succeed at all.

fglrxinfo displays

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

which I don`t think it`s supposed to, but when I check xorg.conf it has fglrx in it where it should.

Now when I run wine or winecfg, the previous message I got is gone, but the lockup is unchanged. It just locks directly after the creating .wine/ message.

---

### Post by crumja on 2006-10-25
You need to enable direct rendering.

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

has some info on that.

My xorg file has key sections:

Section "DRI"
        Mode         0666
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Make sure glxinfo | grep rendering gives you
direct rendering: Yes

There are definitely existing threads on how to enable direct rendering under fglrx.

---

### Post by ba5e on 2006-10-25
simple answer for you - run:

```
winecfg
```

After installing WINE.

This has to be used once WINE is installed to configure it correctly - I can not see in your post any mention about you configuring wine 1st.

It might be a good idea to remove your $HOME/.wine dir, as it may be dodgy (back up everything 1st please)

Hope this helps!

---

### Post by ba5e on 2006-10-25
Opps, didn't see the second page of posts before I posted above....

---

### Post by Nakajoe on 2006-10-25
Thanks. To enable direct rendering it seems the second, manual method seems necessary. I tried it, have fixed several errors but new ones keep coming; I`ll be back when I have something that seems relevant to wine. 

If there`s no way around a kernel recompile, I confess to being doubtful this will ever work. A few months ago at work on a seperate system I spent almost all of a 45-hour workweek trying to get a kernel to compile... Never did work, ended up with a system so messed up (it would boot, but doing anything at all triggered a crash) I had to completely reinstall Ubuntu before giving up. Solving one problem always created others that had not existed before.

---

### Post by Nakajoe on 2006-10-27
Sorry guys, it just isn`t working. Having spent most of yesterday trying to figure out why the kernel module wouldn`t compile, I have to give up for awhile; I`m getting ready to move from Japan to the US in a couple of weeks, and just don`t have time to work on it for at least another month. For some arcane reason that ATI driver seems to have killed my sound (although it made bootup faster); it was working until I rebooted after installing it, since then nothing. If my system goes down I`ll really be in trouble, and don`t want to risk touching anything.

I really do appreciate all the help, and am holding onto hope that with the suggestions everybody made I can get it working before the end of the year. :oops:

---

### Post by SpEcIeS on 2006-10-27
Well I am having _*no luck*_ either. Even tried the latest version **0.9.24**..  no luck. ](*,)  This is very strange.

---

### Post by crumja on 2006-11-06
You shouldn't even have to install fglrx manually from the ATI site. It's available in the ubuntu reps. After installing that, edit the xorg.conf file and add the lines disabling composite and changing the driver used from ati to fglrx.

---

### Post by Nakajoe on 2006-11-06
Hmm, must have missed it. Thanks for the heads up, I`ll try the reps as soon as I can. 

My HDD is in a box being shipped now (writing this from a net cafe), I`ll have it back and up in a rebuilt computer in about two weeks. I appreciate the help.

---

### Post by hikaricore on 2006-11-06
Depending on what you're wanting to run in wine, you may want to look into using vmware instead.  If it's a normal application and not a massivly system intensive fps game.. you know the kind I mean here, then you should be able to install some random version of windows via vmware and have a virtual desktop you can run when you need said application.  I use my virtual windows2000 system to run simple things like winrar (sadly some rar archives I come across will only extract with winrar... *sigh*) and photoshop and other apps work perfectly that way too.  Eh just a suggestion.  There's plenty of vmware threads around the board if you want to look more into it.

---

### Post by Nakajoe on 2006-11-06
I`ll look into it; the main reason I was wanting to install wine in the first place was actually to install Windows Firefox to use Flashplayer to access those annoying sites that have flash-only content. I finally got the video part to work in Ubuntu Firefox, except when whatever site tells me I don`t have the latest version, except the sound never worked, and attempts to fix the sound with instructions on this or that thread (killall esd, use ALSA directly etc) always resulted in ALL sounds from Ubuntu disappearing. But that`s complicated and long and another thread. 

Back on topic, I`ll read up on vmware. Thanks!

---

### Post by hikaricore on 2006-11-06
You're getting latest version errors?  Hmm... have you tried the flash 9 beta that's availible.  This solved every problem I ever had with flash except for the incorrectable issue that google video looks like horse &@%#...  but that's google's fault for using flash badly.  =)    Just another idea, not trying to send you in 15 different directions lol >.<

---

### Post by Nakajoe on 2006-11-06
I was getting a LOT of errors, fix one and the solution usually caused something else. For instance after one video driver update the screensaver would crash xserver. Only thing I could figure is that my setup must have been really weird, but after I get off the plane next week I`m going to build another one, which hopefully will be better.

---

### Post by SpEcIeS on 2006-11-20
Wow... still no success. ](*,) Even used **0.9.25** deb packages and compiled my own, so this tells me something internal on my system is not cooperating. 

When the system locks up it does a _*soft CPU lockup*_. Any ideas? 

Again, I have a test drive with **[COLOR="Blue"]Fedora Core 6[/COLOR]** on it and wine, **0.9.25**, works as it should. No problems.

---

### Post by SuperDindon on 2006-12-03
I sended a mail to ALSA ML that might have your interest :D 
> **Subject:**	Serious issue : some MIDI module lockup when Wine is launched

Hi,

I just FINALLY found out the problem preventing me to use Wine since 4 months !
One of those modules : snd_seq_midi, snd_seq_oss, snd_seq_midi_event and
snd_seq lockup the system immediately after Wine is launched ( even
"wineprefixcreate" ). No lockup if I remove the modules before launching Wine..

I'm a Gentoo user, but some Ubuntu fellas experienced this problem as well :
[http://ubuntuforums.org/showthread.php?t=280155](http://ubuntuforums.org/showthread.php?t=280155)
[http://ubuntuforums.org/showthread.php?t=195409](http://ubuntuforums.org/showthread.php?t=195409)


---

### Post by Nakajoe on 2007-01-01
After I rebuilt the machine, the freezes did indeed stop. Still no clue why though. Thanks again for all the suggestions!

---

### Post by sinaen on 2007-05-29
Im running guild wars with wine. maybe ill try to do the -nosound switch when i run it after all.. :) see if it locks up my computer then

---

