---
title: "Google Earth Problems"
date: 2006-10-17
forum: General Help
---

### Post by DougieFresh4U on 2006-10-17
When I open google earth, the earth map keeps flashing and my curser keeps freezing. any one have ideas what is wrong and how to fix?  Thanks in advance 8)

---

### Post by velo on 2006-10-17
Perhaps this is because Google Earth tries to render in software mode when OpenGL is not set up correctly. 
When I hadn't installed the closed source driver for my Nvidia card, it did the same thing.
Try running *glxinfo* from the terminal and check if it says "direct rendering: Yes". If it does, my idea was wrong ;)

---

### Post by IusedTObeSOMEONEelse on 2006-10-17
~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2                                                        This is part of what output was. I do not know what any of it means. Thanks for your reply! What next?

---

### Post by DougieFresh4U on 2006-10-17
dougie@DougiesToyBox:~$ glxinfo
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
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
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
0x43 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
I don't know how to interpet!!

---

### Post by IusedTObeSOMEONEelse on 2006-10-17
Hey Dougie! Sorry Bro to but in on your thread, but I'm having the same type of problem. Also Dougie , we haven't heard from you latley. How about messaging us. You make us worry :( Hope some one helps us out. Google Earth Rocks 8)

---

### Post by velo on 2006-10-18
Ok, as far as I know, this means you (both) don't have the right drivers for your graphics card installed. For ATI and Nvidia you need to install binary drivers, which are closed source.

There are several guides for installing the 3D Accelerated Drivers for [Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") (the Nvidia ones have big security flaw - perhaps you might consider using their [beta drivers]("http://ubuntuforums.org/showthread.php?t=273462&highlight=nvidia+beta")), [ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") or [Matrox]("https://help.ubuntu.com/community/BinaryDriverHowto/MatroxParhelia") available - perhaps this helps you.

---

### Post by DougieFresh4U on 2006-10-18
Ok, I don't really understand much about the nvidia drivers. I do not know what exactly is in my machine. How do I find out what is installed already  so I have an idea about my next step in the right driver to be installed?

---

### Post by velo on 2006-10-18
To figure out what card is installed in your computer, start a terminal and execute
```
lspci|grep VGA
```
and paste the output line here...

---

### Post by DougieFresh4U on 2006-10-19
dougie@DougiesToyBox:~$ lspci|grep VGA
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03                      OK, this is what came up. I have gone to intels website and can not find this particular CGC. How can I upgrade this if nothing is listed? Thank you for reply!

---

### Post by DougieFresh4U on 2006-10-19
Can some one tell me what drivers that are compatible with the graphics card I need to install to make Google Earth work?

---

### Post by DougieFresh4U on 2006-10-19
Bump! Help

---

### Post by emarkay on 2006-10-19
> **DougieFresh4U said:**
> dougie@DougiesToyBox:~$ lspci|grep VGA
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03                      OK, this is what came up. I have gone to intels website and can not find this particular CGC. How can I upgrade this if nothing is listed? Thank you for reply!

0000:00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)

Me too! 
However:

"Intel® 82810 Graphics Controller
End of Interactive Support Announcement
These products are no longer being manufactured by Intel."
[http://support.intel.com/support/graphics/intel810/](http://support.intel.com/support/graphics/intel810/)
 
Drivers:
[http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?ProductID=798](http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?ProductID=798)

Most recent drivers are from 2002, however.

Just thought I'd offer my input. :)

MRK

---

### Post by DougieFresh4U on 2006-10-19
Thank you. My sister also has the same problem  with Intel card.

---

### Post by DougieFresh4U on 2006-10-22
oops! Bump

---

### Post by DarkN00b on 2006-10-22
You can install the i810 drivers through Synaptic, just search for i810. Do this before doing anything else.

Then make changes to /etx/X11/xorg.conf

```
gksudo gedit /etc/X11/xoug.conf
```

Make these sections look like this:
```
Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"				#your monitor may differ
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection
```

You should leave section "monitor" like it is and not make changes to that section.

This should enable direct rendering on your Intel chipset.

---

### Post by DougieFresh4U on 2006-10-22
Thank you, finally a lead to some where. What I foung in synap was the i810-switch. Is that what I want? As that was the only thing there.

---

### Post by DarkN00b on 2006-10-22
You need the "xserver-xorg-driver-i810" package. Install that, make changes to your xorg.conf and restart. That should enable direct rendering.

---

### Post by DougieFresh4U on 2006-10-22
ok I found Xserver-Xorg video- intel driver for i8xx. i hope that is right. the display driver was already installed -Xserver-Xorg-display driver for i8xx- I just want to make sure I am doing the correct move

---

### Post by DarkN00b on 2006-10-22
That's good, you should be able to make the changes to your xorg.conf file and enable direct rendering.

Make sure you back up xorg.conf before you change anything!

---

### Post by DougieFresh4U on 2006-10-22
~$ gksudo gedit /etc/X11/xoug.conf

(gedit:7447): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed. What did I dio wrong? Also another screen comes up blank

---

### Post by DarkN00b on 2006-10-22
Well you can open a terminal and type ```
sudo nano /etc/X11/xorg.conf
```

Nano is a command-line text editor.
Enter your password. Make your changes and then press ctrl+o to save the file, then press ctrl+x to exit nano. then restart. The path is case sensitive, so make sure to capitalize the 'X' in X11.

---

### Post by DougieFresh4U on 2006-10-22
Sorry, you must think I am total screw-up. This is what I get with that last code:                                                                                GNU nano 1.3.12           File: /etc/X11/xorg.conf                            

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
                               [ Read 148 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by DarkN00b on 2006-10-22
That's perfect! You have successfully opened your xorg.conf file in nano. Use the arrow keys to scroll down and make the changes you need, it works just like windows notepad. Then use ctrl+o to save and ctrl+x to exit. 

And no, I don't think you are a screw up. :-D  I'm still somewhat of a noob myself. The only difference between me and you is that I happen to have a lot of experience with Intel video problems.

---

### Post by DougieFresh4U on 2006-10-22
Thanks for the vote of confidence! I do not see any of the sectionsw as you posted. Am I supposed to open some thing in one of those lines?

---

### Post by DarkN00b on 2006-10-22
If you look above at the example I posted, you will see that there is a section called ' Section "Device" '. That is as long as you are using the Gnome desktop. I don't think I asked, but I've been working on the assumption that you are and since you have an xorg.conf I guess you are.

Anyway, you are interested in the ' Section "Device" ' part for now. Change the Driver line to "i810".

---

### Post by DougieFresh4U on 2006-10-22
I made changes before your last post. I kept scrolling down and got to those section. I made changes but some how I thought I saved -cont+x & cont+o but when I restarted, They were not saved so I guess I will make changes again. I do not know what I did wrong. Thanks for hanging in there for me :cool:

---

### Post by DarkN00b on 2006-10-22
Make sure you type ctrl+o first, then ctrl-x. ctrl+o is ctrl+(the letter o)

If you typed ctrl+x first, you exited before saving.

EDIT: Also, make sure you used the sudo command to start nano.
```
sudo nano /etc/X11/xorg.conf
```

EDIT: I seem to have had a small problem here at home - the electrical breaker to my water heater went out. I need to go to town and get another one so I won't be around for a couple hours. I'll check back then. I hope you get your video working.

---

### Post by DougieFresh4U on 2006-10-22
I copy and pasted the nano . I've made changes twice and saved the way you specified and restarted. when I check the changes didn't hold. What am I doing wrong? Thanks so much

---

### Post by DarkN00b on 2006-10-22
Well dang. I gotta go for a while, but try this.

Reboot and press escape at the grub menu and boot into recovery mode. wait until you get to the command line and type ```
startx
```

Once gnome has loaded, navigate to /etc/X11/xorg.conf.
Double-click xorg.conf and make your changes when it comes up.
After saving your changes, reboot as normal and see what happens.

See ya in a couple of hours.

---

### Post by DougieFresh4U on 2006-10-22
I have not saved any thing yet but this is what I changed. couldn't paste it all but 1024x768 or whatever is correct now about saving?  Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Devive"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"

---

### Post by DougieFresh4U on 2006-10-22
Absolute trauma now. (I have to use windows machine) after restart, actualy wouldn't restart. So I grub into recovery mode and get errors -Data incomplete in file: /etc/X11/xorg.conf - Undefined Device "Intel Corporation 82852/855GM Itegrated Graphics Device" referenced by Screen "Default Screen"  (EE) Problem parsing the config file. (EE) Error parsing the config file.   Fatal server error: no screens found.  XIO: fatalIO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0known processed) with 0events remaining.   Now its at:: root@DougiesToyBox:~$    Help. I know it's some thing that can be fixed but just do noty know how.

---

### Post by xtknight on 2006-10-22
> **DougieFresh4U said:**
> Can some one tell me what drivers that are compatible with the graphics card I need to install to make Google Earth work?

[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=798&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=798&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

---

### Post by DarkN00b on 2006-10-22
I seem to have made your problems worse. I'm sorry for that.

But there is hope. Assuming you can boot into recovery mode at the command line, type:
```
sudo dpkg-reconfigure xserver-xorg
```

This will let you configure the entire file. You need to know about the hardware in your computer. When it comes to the part about the video dtiver, select "i810".

Choosing the default values for everything else should be safe.

Again, sorry I caused more problems for you.

---

### Post by DougieFresh4U on 2006-10-22
No problem. It was a learning exp..
It's back up and running again. I guess I can stick to google earth on my winxp machine. I do not fire up that box to much. Actually I'm gonna shut it down now and go online on other machine to see if all is ok. thanks so much for your effort as no one else attempted to help over the last few days and I believe you were in the right direction, be back

---

### Post by DougieFresh4U on 2006-10-22
ok, ubuntu back up and running. I'm open for suggestions, even willing to give it another try?? :confused:

---

### Post by DarkN00b on 2006-10-22
Well I guess you could try ```
sudo dpkg-reconfigure xserver-xorg
```

Like I said in the post above, you can configure your xserver with this. The first thing it asks you is if you want to autodetect video hardware. Hit enter to select YES. It should autodetect your hardware, if it does not then select "i810" and continue with the configuration. With any luck, you will get everything working correctly.

---

### Post by DougieFresh4U on 2006-10-22
yeah every thing is back the way it was in the begining, meaning that crappy old driver for intel that won't let me use google earth

---

### Post by DougieFresh4U on 2006-10-22
ok, the direct rendering says no which is not right so what can I do to correct this please? Anybody!!                               dougie@DougiesToyBox:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
**direct rendering: No**
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
0x43 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by DougieFresh4U on 2006-10-23
oops, Bump

---

### Post by DougieFresh4U on 2006-10-24
Bump again

---

### Post by CatKiller on 2006-10-25
I really don't know much about the i810 driver, but **man i810** says this: >        By default 8 Megabytes of system memory are used for graphics.  For the
       830M  and later, the default is 8 Megabytes when DRI is not enabled and
       32 Megabytes with DRI is enabled.  This amount may be changed with  the
       VideoRam entry in the config file Device section.  It may be set to any
       reasonable value up to 64MB for  older  chipsets  or  128MB  for  newer
       chipets.   It  is  advisable to check the Xorg log file to check if any
       features have been disabled because of insufficient video  memory.   [B]In
       particular,  DRI  support  or tiling mode may be disabled with insuffi&#8208;
       cient video memory.[/B]  Either of these being disabled will reduce perfor&#8208;
       mance  for  3D  applications.  Note however, that increasing this value
       too much will reduce the amount of system memory  available  for  other
       applications.
 Emphasis mine. You can check the log with ```
less /var/log/Xorg.0.log
``` Use Page Up/Down or the up & down arrows to scroll through the log. Q to quit.

---

### Post by DougieFresh4U on 2006-10-25
That gives me pages and pages of some thing I may never understand :confused:

---

### Post by CatKiller on 2006-10-25
> **DougieFresh4U said:**
> That gives me pages and pages of some thing I may never understand :confused:

Have a look for warnings about DRI not being turned on because of not having *x* amount of memory, and then allocate more than that amount of memory in the BIOS or as an option in your xorg.conf.

As I said, I don't know much about that driver. Other people seem to have problems with it too.

---

### Post by DougieFresh4U on 2006-10-25
can some please help me on this?

---

### Post by IusedTObeSOMEONEelse on 2006-10-30
Well, it's been a week now. Iwould like to try another attempt to get google earth up & working. If any one has any ideas I'm ready. Hopefully I won't cause to much breakage!!** (again)** My specs are the same as my Brother's (Dougiefresh) as we both have the same kind of machine's

---

### Post by IusedTObeSOMEONEelse on 2006-10-30
Well after waiting all Day, I have come to the conclusion that I must keep WindowsXP on my other machine to be able to Google Earth as not one single person has stepped up to the task of helping me out on this!! Moderaters, you may as well close this thread as it's old and useless.

---

### Post by DougieFresh4U on 2006-10-30
Hi SiS,  I agree 100%

---

### Post by tomjennings on 2007-07-02
The problem seems to be that the generic "vesa" driver (selected by ubuntu install on my Sony laptop) makes googleearth crash X. The solution is to pick the right video driver.

On my Sony laptop, which uses the i810 chip, there's an i810 driver available. Simply change the xorg.conf file to tell X to use it:

Find the output (screen) driver, it'll probably say "Generic Video Card".




in file /etc/X11/xorg.conf:

Section "Device"
        Identifier      "Generic Video Card"
#tomj   Driver          "vesa"
        Driver          "i810"
        BusID           "PCI:0:2:0"




Edit, save, restart X (Control-Alt-Backspace) should be ready to go.

---

### Post by bsawler on 2007-07-05
Thanks TJ,

That worked for me. Commented out #Driver "vesa", and added Driver "i810" then ALT+CTRL+Backspace.

---

