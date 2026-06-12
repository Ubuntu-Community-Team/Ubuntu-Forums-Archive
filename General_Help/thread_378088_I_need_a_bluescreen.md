---
title: "I need a bluescreen"
date: 2007-03-06
forum: General Help
---

### Post by HugoRune on 2007-03-06
(System: Ubuntu edgy 64bit with kubuntu-desktop installed)

I frequently get random crashes while using opengl programs (for example gtklookat or openSG)

For example while displaying some 3D model and moving it with the mouse Ubuntu either suddenly reboots or jumps to the login screen,
var/log/messages  says something like 
"exiting on signal 15"
"syslogd 1.4.1#18ubuntu6: restart."
(the message before that seems to be unrelated)

I have no idea how to find out the cause of the crashes with this data.
This might sound weird, but is there any way to get some sort of bluescreen or other more detailed error messages instead of the silent reboots?


(the graphics card is recognized as: nvidia corporation Unknown device 014d(rev a2)(prog-if 00 [VGA]). This is an office PC, so probably nothing fancy, but I do not know for sure)

---

### Post by FIONEX on 2007-03-06
Actually it's funny that you say that but even windows wouldn't give you a bluescreen in something like this.  Linux never resets on a crash even if it's major.  It's not designed to do that.  Your computer on the other hand is set to reset on error from the bios.  That means the application is asking the computer to do something that's causing an internal problem.  If you change your PC settings from the bios, it can give you a nice blue screen that won't even respond to Ctrl+Alt+Del or any combination of buttons that is.  I think it's Halt On Error.

---

### Post by HugoRune on 2007-03-06
I am not sure if this can be caused by the bios alone.

While sometimes the computer did a full reset, in several crashes I just got dumped straight to the login screen for ubuntu, without any power-on messages or grub comming up.

It also took only a few seconds, far shorter than the usual boot up time. I thought that indicated a software problem.

---

### Post by HugoRune on 2007-03-20
The problem is getting a lot more frequent recently. It is also not just limited to vrml anymore, often this happens when I am doing nothing special at all.
I just had the 4. crash for this day. one was while compiling, and one while saving a text file

The symptoms are: computer stops responding for a few seconds, and then the ubuntu login screen instantly comes up. 

No bios message, no boot menu, no linux power-on messages or similar are visible, so I do not think this is a hardware reset.

Nevertheless all my open applications are gone and unsaved files lost.

After a lot of googling I found some clues that this could be the x-server crashing, but I did not get further with that information.

Is there any way to trace the cause of these crashes?

---

### Post by rich.bradshaw on 2007-03-20
Sounds like it is the x-server crashing. Press cntrl-alt-backspace to restart X - is it the same as if you manually reset it?

Could be your drivers - do you have an nvidia/ati card?

---

### Post by HugoRune on 2007-03-20
Yes, cntrl-alt-backspace has exactly the same effect.

the graphics card is recognized as: nvidia corporation Unknown device 014d(rev a2)(prog-if 00 [VGA]). This is an office PC (Dell), so probably nothing fancy, but I do not know for sure

At first I thought it was only when doing openGL tasks, but since recently it crashes frequently even when  doing nothing related to graphics at all, such as saving a file. or starting a compile.

---

### Post by HugoRune on 2007-03-22
Is there anywhere else I could ask for help, or anything I could do to improve the error description so someone can recognize the cause more easily?

I really do not want to sound ungrateful, and I realize I get what I pay for and all that, but these crashes are driving me crazy, and make working normally very difficult, so I am getting a bit desperate.

---

### Post by mcduck on 2007-03-22
To get more info about what caused the crash check ~./xsession-errors and the logs in /var/log directory.

For bluescreen, the closes you can get is the BSOD screensaver ;)

---

### Post by HugoRune on 2007-03-22
Thank you very much!

~/.xsession-errors contains quite a few lines, but all seem to be related to the current session, nothing to the one before the crash, I think that this file is recreated with each login?

However, I looked thought the various files in /var/log and found  one entry that seems to be strongly corelated with the crashes:

in file /var/log/messages
```
Mar 22 19:13:51 XXXX kernel: [31740.198286] mtrr: type mismatch for d8000000,8000000 old: write-back new: write-combining
Mar 22 19:14:12 XXXX gconfd (USERNAME-32710): SIGHUP received, reloading all databases

```

The line before that seems to be unrelated.
googling for the error message I found nothing I could use so far, but it is a start.

Does this reveal the cause of the crashes?


(by the way, the mentioning of a bluescreen was probably confusing, sorry. 
I just thought initially that there must be some sort of setting to tell linux not to jump to the login screen without any error message, just like windows does when "automatic reboot on error" is enabled, and that I was just missing the obvious. I had no idea that this was so complicated)

---

### Post by eXidos on 2007-03-22
can you post your xorg.conf so i can see your driver and hardware config

---

### Post by HugoRune on 2007-03-22
/etc/X11/xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600?]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "DELL 1703FP"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV43 [GeForce 6600?]"
        Monitor         "DELL 1703FP"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

I did not install any special drivers, anything should still be as it was set up by the ubuntu installer

---

### Post by eXidos on 2007-03-22
your not using the nvidia driver just a generic driver for your card go here and fallow the instructions [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29) I think opengl errors are crashing your xserver because you driver does not support the glx version, you could also try:

glxinfo

in terminal first to test your opengl if all checks out...id still recommend installing the nvidia driver it will help performance at the very least.

---

### Post by HugoRune on 2007-03-22
I thought the purpose of proprietary beta graphics drivers was more speed at the cost of less stability?

Are you certain this is is wise, or did I misunderstand something? 

I really do not care about performance at all, this machine is not used for games, my only concern is stability.


glxinfo returns this text:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control,
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer,
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_logic_op,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
    GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_ATIX_texture_env_combine3, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_NV_blend_square, GL_NV_point_sprite, GL_NV_texgen_reflection,
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x62 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by eXidos on 2007-03-22
try this:

sudo apt-get upgrade

hopefully it will upgrade your generic driver first, if you are having problems with the nvidia driver after the install all you have to do is change your driver back to "nv" insted of "nvidia" this will set it back to the generic driver.

if the driver fails to load after the install enter the recovery mode during boot and:

sudo pico /etc/X11/xorg.conf 

change the cards driver back to "nv", I'd give it a try just backup your xorg.conf. I have been using the nvidia driver since 5.10 and have never had a problem with it, even with 7.04 it works great.

---

### Post by Death_Sargent on 2007-03-22
What you need is some sort of crash handeler or error reporter.

---

### Post by HugoRune on 2007-03-22
I installed the nvidia drivers. so far I have not had a crash today, I will test it during the day. 
Thank you.


@Death_Sargent:
Where could i get such a crash handler?

---

### Post by jeffathehutt on 2007-03-22
Does this computer also run Windows?

This problem sounds like your computer is overheating.  If your ram or processor gets too hot, it can cause errors to occur.  If the ram that holds X is corrupt, it could cause X to crash, thus dumping you to the login screen.  If another part of the ram gets errors, such as the kernel, it could cause the computer to completely reboot.

If you don't have the nvidia drivers installed, most of the graphic processing happens in your processor.  This would cause the system to crash when running opengl programs, because they are processor intensive and create more heat.  If this is the case, installing the official drivers could help, because it would lighten the load on your processor.

Also, when you compile programs, it is very processor intensive, which would explain the more frequent crashes when compiling.

---

### Post by HugoRune on 2007-03-23
That is an interesting possibility.

I cannot really open it up to check the cooling, since this is an office pc. At least the air blowing out seems quite cool.

This computer also runs windows in dual-boot. I have not noticed any instabilities on windows so far.

Still no crash for today. hope it lasts!

---

