---
title: "Problem with 8800GTS and nVidia Drivers"
date: 2007-05-27
forum: General Help
---

### Post by xUNDEROATHx21 on 2007-05-27
Hi there, I have recently set up ubuntu on my machine, it is dual-booting with XP...

I am wanting to set up beryl, but I am having some problems getting my nVidia drivers installed... I have looked throughout this forum as well as other,s and have not found a complete way to install them...

I have resorted to using the "Envy" app, but I still got the same results. Xorg crashes and I am left witha  black screen followed by a blue error screen(pics posted once I get on my XP machine again.. (Im currenly on my FC6 setup)

I am just wondeirn if anyone has successfully installed 8800GTS320 drivers, and if they can give me a step-by-step guide on how to install...


thanks,
-underOATH

---

### Post by Crafty Kisses on 2007-05-27
Same thing happens here man, I havn't got my drivers installed ever since I installed Ubuntu, but the problem lies within the xorg.conf file, you have to change "nv" to "Nvidia" in the xorg.conf file. Hope this helps.

---

### Post by xUNDEROATHx21 on 2007-05-27
> **Codename said:**
> Same thing happens here man, I havn't got my drivers installed ever since I installed Ubuntu, but the problem lies within the xorg.conf file, you have to change "nv" to "Nvidia" in the xorg.conf file. Hope this helps.

thanks man...

Ive heard stuff like that, but Im not sure what version of drivers to use, or even how to install them... Im new to linux, and Ive read alot of good things about ubuntu and beryl, so I thought I would give it a try... Didnt know I would have so many problems with my 8800GTS :(

Here's some screens of the error screen if that helps... 

[http://i45.photobucket.com/albums/f89/xUNDEROAThx21/emoticons/DSC_0001-1.jpg](http://i45.photobucket.com/albums/f89/xUNDEROAThx21/emoticons/DSC_0001-1.jpg)
[http://i45.photobucket.com/albums/f89/xUNDEROAThx21/emoticons/DSC_0002-1.jpg](http://i45.photobucket.com/albums/f89/xUNDEROAThx21/emoticons/DSC_0002-1.jpg)
[http://i45.photobucket.com/albums/f89/xUNDEROAThx21/emoticons/DSC_0003-1.jpg](http://i45.photobucket.com/albums/f89/xUNDEROAThx21/emoticons/DSC_0003-1.jpg)

---

### Post by mmilitia9 on 2007-05-27
Hey!  Ubuntu will rock your socks off when you get everything properly installed.  Nvidia drivers are annoying.. I have the SAME EXACT PROBLEMS.. But, I've figured them out :) 

Check this,

Do you have a on board graphics card?  If you do.. Go to your BIOS and make sure to run your integrated graphics for now and switch your monitor plug to that plug.

Okay.. Boot up Ubuntu.. you should successfully boot into Ubuntu live CD.  Partition and Install while your in the live CD.  

Okay.. After that.. Reboot your machine and change back the BIOS settings to use your normal video card.  

Let it fail again.

Now.. Log into your ubuntu account that you've set up earlier. 

Run these commands from this website:
[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

Make sure you PRINT that and follow EVERY step.  

This is what got me going and it should get you going too.  

Your welcome, :-P

Dominick

---

### Post by xUNDEROATHx21 on 2007-05-27
> **mmilitia9 said:**
> Hey!  Ubuntu will rock your socks off when you get everything properly installed.  Nvidia drivers are annoying.. I have the SAME EXACT PROBLEMS.. But, I've figured them out :) 

Check this,

Do you have a on board graphics card?  If you do.. Go to your BIOS and make sure to run your integrated graphics for now and switch your monitor plug to that plug.

Okay.. Boot up Ubuntu.. you should successfully boot into Ubuntu live CD.  Partition and Install while your in the live CD.  

Okay.. After that.. Reboot your machine and change back the BIOS settings to use your normal video card.  

Let it fail again.

Now.. Log into your ubuntu account that you've set up earlier. 

Run these commands from this website:
[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

Make sure you PRINT that and follow EVERY step.  

This is what got me going and it should get you going too.  

Your welcome, :-P

Dominick

I actually followed this EXACT guide... but I still received X errors... Anyone ere actually have their 8800GTS 320MB running w/ drivers installed? I'm installing fedora and seeing if I can get the drivers set up on there...

thanks!

-underOATH

---

### Post by mmilitia9 on 2007-05-27
That's weird.  According to Ubuntu theres only 2 Nvidia drivers.

One for old legacy driver and the other for all that is new.  Thats it.  

Hmm... Well, anyone else?

---

### Post by Crafty Kisses on 2007-05-27
> **xUNDEROATHx21 said:**
> thanks man...

Ive heard stuff like that, but Im not sure what version of drivers to use, or even how to install them... Im new to linux, and Ive read alot of good things about ubuntu and beryl, so I thought I would give it a try... Didnt know I would have so many problems with my 8800GTS :(

Here's some screens of the error screen if that helps... 

[http://i45.photobucket.com/albums/f89/xUNDEROAThx21/emoticons/DSC_0001-1.jpg](http://i45.photobucket.com/albums/f89/xUNDEROAThx21/emoticons/DSC_0001-1.jpg)
[http://i45.photobucket.com/albums/f89/xUNDEROAThx21/emoticons/DSC_0002-1.jpg](http://i45.photobucket.com/albums/f89/xUNDEROAThx21/emoticons/DSC_0002-1.jpg)
[http://i45.photobucket.com/albums/f89/xUNDEROAThx21/emoticons/DSC_0003-1.jpg](http://i45.photobucket.com/albums/f89/xUNDEROAThx21/emoticons/DSC_0003-1.jpg)

I get those errors too, I'v had to reinstall Ubuntu about 13 times already, but that's besides the point. Basically what you want to do is back up the xorg.conf file.

Before you install the driver, type this in the console.

> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

That backs up the xorg.conf file, and if your drivers crash, and you can recover it. So you don't have to reinstall.

---

### Post by Crafty Kisses on 2007-05-27
How to install Beta Graphics Driver (NVIDIA)

    * WARNING this is very error prone.. a better method is to use Alberto Milones Envy program; [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 

    * Thanks to Alberto Milone 

    * The nVidia driver has been split into different branches; latest and new legacy. See [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html) to find out which driver you should be using. Latest=97xx / New Legacy=96xx 

    * Read #How to add extra repositories 

sudo gedit /etc/apt/sources.list

    * Add ONE of the following lines based on your architecture 

deb [http://www.albertomilone.com/drivers/edgy/latest/32bit](http://www.albertomilone.com/drivers/edgy/latest/32bit) binary/
deb [http://www.albertomilone.com/drivers/edgy/latest/64bit](http://www.albertomilone.com/drivers/edgy/latest/64bit) binary/

deb [http://www.albertomilone.com/drivers/edgy/newlegacy/32bit](http://www.albertomilone.com/drivers/edgy/newlegacy/32bit) binary/
deb [http://www.albertomilone.com/drivers/edgy/newlegacy/64bit](http://www.albertomilone.com/drivers/edgy/newlegacy/64bit) binary/

    * Save the edited file 

    * Add the GPG key 

wget [http://albertomilone.com/drivers/tseliot.asc](http://albertomilone.com/drivers/tseliot.asc)
gpg --import tseliot.asc
gpg --export --armor [email]albertomilone@alice.it[/email] | sudo apt-key add -

    * Update and install 

sudo apt-get update
sudo apt-get install nvidia-glx
sudo apt-get upgrade

    * The upgrade should update your linux-restricted-modules & linux-restricted-modules-common packages. 

sudo nvidia-xconfig

    * Add a menu option for nVidia Settings 

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

    * Insert these lines in the new file and save 

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

    * Restart the computer and your new drivers should be installed. 

    * Test the install with these 2 programs 

glxinfo
glxgears

---

### Post by Linkerator on 2007-05-27
I once had the same problem, but with a bit of tweaking to the Xorg file for me, I got it fixed. Try this to see if it will work. 

When booting, press ESC when GRUB is booting and switch to recovery mode. This will cause it to have no GUI. Login and then type:

```
sudo nano /etc/X11/xorg.conf
```

Press ctrl+O and save it as /etc/X11/xorg_backup.conf To back it up in case.

Scroll down until you see something like "Generic Video card" or something similar, it might say Nvidia card but I don't know for sure.

Change the nv drivers into Nvidia.

It should look something like this:

```
Section "Device"
        Identifier      "Video Card name"

        Driver          "Nvidia"
        BusID           "PCI:1:0:0"
EndSection
```

Not exactly, mind you. ;-)

Then hit Ctrl+O to save it as "/etc/X11/xorg.conf".

---

### Post by Crafty Kisses on 2007-05-27
Is there any way I can get your glx info.

Simply open up terminal and type:

```
glxinfo
```

---

### Post by xUNDEROATHx21 on 2007-05-28
> **Codename said:**
> I get those errors too, I'v had to reinstall Ubuntu about 13 times already, but that's besides the point. Basically what you want to do is back up the xorg.conf file.

Before you install the driver, type this in the console.



That backs up the xorg.conf file, and if your drivers crash, and you can recover it. So you don't have to reinstall.

how do i recover it?

again, I am new to ubuntu and am unsure how to do stuff...

Edit: I am reinstalling again, I am on my Fedora box right now... I will try all this when I get ubuntu reinstalled... thanks guys!

---

### Post by xUNDEROATHx21 on 2007-05-28
here is my glx info...

> name of display: :0.0
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
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

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
0x42 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by xUNDEROATHx21 on 2007-05-28
bump?

---

### Post by Crafty Kisses on 2007-05-28
To recover your xorg.conf back up, go into terminal and type:

```
cp /backupdir/xorg.bak /etc/x11/xorg.conf
```

---

### Post by Crafty Kisses on 2007-05-28
If you have any other questions you can reach me at my AIM, or I'll keep posting with you on this untill we get this figured out man.

You have a good night, and good luck and i'll do everything I can to help you out.

---

### Post by xUNDEROATHx21 on 2007-05-28
well, Im back at it today... Im restoring my xorg file now...

then I'll mess with it a little...

---

### Post by xUNDEROATHx21 on 2007-05-28
> **Codename said:**
> To recover your xorg.conf back up, go into terminal and type:

```
cp /backupdir/xorg.bak /etc/x11/xorg.conf
```

I tried that and I got the error ```
cp:cannot create regular file '/etc/X11/xorg.conf' : Permission denied
```


I am going to try another reinstall right now....

---

### Post by tijnz0r on 2007-05-28
I found a workaround for using this card (geforce 8800GTS 320mb, club3d brand) working in feisty fawn, including desktop effects:

If you have the same problems as me, booting normally presents you with a black screen.
This can be averted by pressing the escape key when GRUB is loading and selecting the recovery mode of your most recent kernel.

Your computer will boot in command line mode. use a text editor (vi or nano) to open /etc/X11/xorg.conf and change the graphics card driver from "*nvidia*" to "*vesa¨* 

The section looks something like this after your done:

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8800 GTS]"
    Driver         "vesa"

Now we can start X by typing:

*startx*

Next we need to download a new nvidia driver, as the one included doesn't seem to work. I didn't try the apt-get version (which seems to be preferred in debian-based distros), but downloaded the linux package:

*NVIDIA-Linux-x86_64-1.0-9755-pkg2.run* (or the 32 bit package if you run that)

save or copy the file in /root.

Now we need some extra packages installed, so the easiest way is to start synaptic.
Do a search on libc6 and make sure *libc6* and *libc6-dev* are installed, else mark them for installation.

Also make sure your kernel headers are installed by searching for *linux-headers* and making sure the headers for your newest kernel is installed (2.6.20-16.28 in my case).

Now that we have the right packages installed, it's time to install the nvidia drivers.

Log out from your graphical environment and marvel at the pretty command line.

type:

*cd /root*

and follow that up with
[I]
sh NVIDIA-Linux-x86_64-1.0-9755-pkg2.run[/I] (sh NV and hitting tab should do, also in case you downloaded the 32 bit package or a newer version of the driver)

Now, nvidia will give you a warning about not being in runlevel 3. I ignored it and am still breathing, so select no to continue.

Now it asks you to accept the license agreement, check online for a kernel module. While it won´t find one it will build one for you and offer you to change your xorg.conf file, do so.

After the nvidia installer informs you (hopefully) that the driver install went smoothly, you are ready to start using your system.

Unfortunately, the normal bootup still doesn't work for me, but by choosing the recovery option, and after bootup in runlevel 1 (you are here now if you followed the above), you can continue the boot process by typing:
[I]
telinit 3[/I]

You are greeted by the standard ubuntu login screen.

Now all that remains is to login and set your screen resolution via *Applications/system tools/NVIDIA X Server Settings*, after that it's safe to enable desktop effects for some pretty eyecandy. 
Trying to change the screen resolution while desktop effects are on crashes my system.

I tried to look into startup scripts for the different runlevels to get normal bootup working, but haven't been successful, being still kind of a linux n00b.

---

### Post by Crafty Kisses on 2007-05-28
> **xUNDEROATHx21 said:**
> I tried that and I got the error ```
cp:cannot create regular file '/etc/X11/xorg.conf' : Permission denied
```


I am going to try another reinstall right now....

Hmmm, it's possible you didn't back up the xorg.conf file properly, I've done that plenty of times. Agian dude don't feel bad, I HAVEN'T been able to install my drivers since I've had Ubuntu and that's like 2 months now.

---

### Post by Crafty Kisses on 2007-06-04
> **xUNDEROATHx21 said:**
> I tried that and I got the error ```
cp:cannot create regular file '/etc/X11/xorg.conf' : Permission denied
```


I am going to try another reinstall right now....

Are you root? If not you can become root by going into terminal and typing:
```
sudo -i
```

---

### Post by Sockerdrickan on 2007-06-04
This won't be a problem with 7.10 since it has 100.14.06 right?

---

