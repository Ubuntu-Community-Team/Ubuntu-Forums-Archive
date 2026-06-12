---
title: "Help with Special Effects with Ubuntu 8.04"
date: 2008-04-26
forum: General Help
---

### Post by Cpuboye11 on 2008-04-26
Hi,

I have a dell notebook- with a 1.8Ghz P4 Mini Cpu- and a ATI 7500m..... in ubuntu 7.10 or what ever was before 8.04 update- i could use all ( Normal and Extra ) Visual Effects. Since the update i can't use any. I ran skip_checks=yes compiz and this is what is came up with -

> Checking for Xgl: Not present
Found laptop using ati driver
aborting and using fallback: /usr/bin/metacity


How do i go about fixing this small issue. I'm not sure where to go from here. 

Thanks,
Kyle

---

### Post by Zorael on 2008-04-26
skip_checks=yes or SKIP_CHECKS=yes? I'm fairly sure caps matter, see. :>

---

### Post by MeanEYE on 2008-04-26
> **Cpuboye11 said:**
> Hi,

I have a dell notebook- with a 1.8Ghz P4 Mini Cpu- and a ATI 7500m..... in ubuntu 7.10 or what ever was before 8.04 update- i could use all ( Normal and Extra ) Visual Effects. Since the update i can't use any. I ran skip_checks=yes compiz and this is what is came up with -



How do i go about fixing this small issue. I'm not sure where to go from here. 

Thanks,
Kyle

I had similar problem. Try with this and then restart your computer:

```

sudo apt-get install xserver-xgl

```

---

### Post by Zorael on 2008-04-26
> **MeanEYE said:**
> I had similar problem. Try with this and then restart your computer:

```

sudo apt-get install xserver-xgl

```
This will likely work, but it'll make compiz stupid slow. :<

---

### Post by Cpuboye11 on 2008-04-26
> **Zorael said:**
> This will likely work, but it'll make compiz stupid slow. :<


Yea i know what you mean... Is there a way to speed it up?

---

### Post by Rocket2DMn on 2008-04-26
I made a quick HowTo to enabling Compiz Fusion on cards using the open source ati drivers - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
There is an explanation there as to why CF doesn't work out of the box in Hardy with these cards.

---

### Post by Cpuboye11 on 2008-04-26
I thank you for all the help...

I installed Advanced Desktop Effects just like the tourtal said to. It seems to be working but nothing is showing....I mean i set the effects and to make sure i hit close and then i restart... 



But while going by the tourtal.. 

I got one of these as a error or error groupings... 

With this command:
```
compiz --replace
```

```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
/usr/bin/compiz.real (bicube) - Fatal: GL_ARB_fragment_program not supported.
/usr/bin/compiz.real (bicubic) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'bicubic'
Starting gtk-window-decorator
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```


Is it because i don't have a open source driver??? Because i have a ATI 7500M and the binary driver that is with the flgx or w/e installer does not support the 7500m. Any Ideas?




This still doesn't make sense why it would just stop working because of this new version...

Or am i just misunderstanding that the black list is a list that contains drivers and etc devices that don't work or are very buggy?

---

### Post by Rocket2DMn on 2008-04-26
If you have the restricted fglrx driver installed, you need to uninstall it first
```
sudo apt-get remove --purge xorg-driver-fglrx
```
Then auto-reconfigure X
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Now restart X by logging out and back in or killing it with CTRL+ALT+BACKSPACE
Now you can proceed with
```
compiz --replace
```

---

### Post by Cpuboye11 on 2008-04-26
> **Rocket2DMn said:**
> If you have the restricted fglrx driver installed, you need to uninstall it first
```
sudo apt-get remove --purge xorg-driver-fglrx
```
Then auto-reconfigure X
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Now restart X by logging out and back in or killing it with CTRL+ALT+BACKSPACE
Now you can proceed with
```
compiz --replace
```


Jezzz Thank you for all your help so far... But still no good yet.... :(

I got this problem............................

```
kyle@KylesLaptop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Starting gtk-window-decorator
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

I even went back and did the whole thing over again... But still no luck :(

---

### Post by krelverehan on 2008-04-26
I am not too sure what hardware you are using (I am no expert, so it probably won't matter), but the only way I can get desktop effects is to engage my restricted drives:

Menu >> System >> Administration >> Hardware Drivers

And restart of course :)

I find this always works better than most of the workarounds provided by various tutorials just to use open source drivers.

---

### Post by Cpuboye11 on 2008-04-27
well i thank you for your help all of you... and also i don't have the ATI biny or w/e drivers installed because they don't support the 7500 mobile i have...

But this is what i have done...

```
sudo apt-get remove --purge xorg-driver-fglrx
```

This is what i got ->

```
kyle@KylesLaptop:~$ sudo apt-get remove --purge xorg-driver-fglrx
[sudo] password for kyle: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xorg-driver-fglrx is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kyle@KylesLaptop:~$ 

```

Then: 

```
sudo dpkg-reconfigure xserver-xorg -phigh
```


I got :

```
kyle@KylesLaptop:~$ sudo dpkg-reconfigure xserver-xorg -phigh
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080426235515
kyle@KylesLaptop:~$ 

```

Then I restarted!

Then: ```
compiz --replace
```

Got:

```
kyle@KylesLaptop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

For this next part i'm just going to copy the whole code! for the Hoto Compiz Fusion install.. 

```
kyle@KylesLaptop:~$ gksudo gedit /usr/bin/compiz
kyle@KylesLaptop:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree... 50%

Building dependency tree... 90%

Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kyle@KylesLaptop:~$ 
kyle@KylesLaptop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

kyle@KylesLaptop:~$ metacity --replace

kyle@KylesLaptop:~$ 

```


Did i do something wrong?

Thank you for all your help!!!

---

### Post by Rocket2DMn on 2008-04-27
I really don't know... can you post
```
cat ~/.gconf/apps/compiz/plugins/scale/allscreens/options/initiate_edge
```
I actually don't have that file, so I'm not sure what it is talking about.

---

### Post by Cpuboye11 on 2008-04-27
Dam... I can't even find the folder.. :lolflag:


Hmmm. This maybe very dumb.. And maybe could save us both a headache. could we do a remote desktop... Is that possible?  I mean... I think it would be easier.. of course that is up to you.. I know I'm asking for a lot. and i thank you a million times, but i am pretty dumb when it comes to this... 
  -Kyle

---

### Post by Rocket2DMn on 2008-04-27
We don't really do remote desktop help on these forums, it's a pain to setup and somewhat of a security risk.
I had a user earlier run across the same problem, and it doesn't surprise me that it says the file doesn't exist... it doesn't exist on my machine either, but then again, I never got that error to begin with.  It worked for the other user to remove the backend and reinstall it.  Here's exactly what I told him/her to do:

> I'm not really sure what that means, you may want to try reinstalling the backend part of compiz (it may prompt you to uninstall more parts of compiz, it should be safe to do so, it just needs to be reinstalled, too).  First disable compiz by enabling metacity
```
metacity --replace
```
Now uninstall:
```
sudo apt-get remove --purge compizconfig-backend-gconf
```
Then reinstall (I will include compiz itself just in case)
```
sudo apt-get install compiz compizconfig-backend-gconf
```
Restart X with CTRL+ALT+BACKSPACE, and now try to load compiz again
```
compiz --replace
```

---

### Post by Cpuboye11 on 2008-04-27
Okay.. That makes sense. I tried uninstalling and reinstalling... But no change...
But thanks for everything so far.. I never thought of the risk.... I'm sorry i even brought it up...

This is what i got-

```

kyle@KylesLaptop:~$ metacity --replace

kyle@KylesLaptop:~$ sudo apt-get remove --purge compizconfig-backend-gconf
[sudo] password for kyle: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-compizconfig
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  compiz* compiz-gnome* compizconfig-backend-gconf*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 754kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 141664 files and directories currently installed.)
Removing compiz ...
Removing compiz-gnome ...
Purging configuration files for compiz-gnome ...
Removing compizconfig-backend-gconf ...
kyle@KylesLaptop:~$ sudo apt-get install compiz compizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-compizconfig
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-gnome
The following NEW packages will be installed:
  compiz compiz-gnome compizconfig-backend-gconf
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/163kB of archives.
After this operation, 754kB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Selecting previously deselected package compizconfig-backend-gconf.
(Reading database ... 141606 files and directories currently installed.)
Unpacking compizconfig-backend-gconf (from .../compizconfig-backend-gconf_0.7.4-0ubuntu1_i386.deb) ...
Selecting previously deselected package compiz-gnome.
Unpacking compiz-gnome (from .../compiz-gnome_1%3a0.7.4-0ubuntu6_i386.deb) ...
Selecting previously deselected package compiz.
Unpacking compiz (from .../compiz_1%3a0.7.4-0ubuntu6_all.deb) ...
Setting up compizconfig-backend-gconf (0.7.4-0ubuntu1) ...
Setting up compiz-gnome (1:0.7.4-0ubuntu6) ...

Setting up compiz (1:0.7.4-0ubuntu6) ...
kyle@KylesLaptop:~$ 
```

:Restarted:

```
kyle@KylesLaptop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

Then I exited out of the box.. ( Termaninal)

And all the effects were running slow and i coudn't even do anything.. it took me about 10 mins just to get to apperence and shut the effects off.

---

### Post by Rocket2DMn on 2008-04-27
OK, let's just try deleting what is at that path:
```
metacity --replace
rm ~/.gconf/apps/compiz/plugins/scale/allscreens/options/initiate_edge
compiz --replace
```

In the future, you don't have to shut it off from Appearance, just run the metacity --replace command.

---

### Post by Cpuboye11 on 2008-04-27
> **Rocket2DMn said:**
> OK, let's just try deleting what is at that path:
```
metacity --replace
rm ~/.gconf/apps/compiz/plugins/scale/allscreens/options/initiate_edge
compiz --replace
```

In the future, you don't have to shut it off from Appearance, just run the metacity --replace command.


This is so strange.......

```
kyle@KylesLaptop:~$ rm ~/.conf/apps/compiz/plugins/scale/allscreens/options/initiate_edge
rm: cannot remove `/home/kyle/.conf/apps/compiz/plugins/scale/allscreens/options/initiate_edge': No such file or directory
kyle@KylesLaptop:~$ sudo rm ~/.gconf/apps/compiz/plugins/scale/allscreens/options/initiate_edge
[sudo] password for kyle: 
rm: cannot remove `/home/kyle/.gconf/apps/compiz/plugins/scale/allscreens/options/initiate_edge': No such file or directory
kyle@KylesLaptop:~$ 
```

:confused::confused::confused::confused::confused::confused:

---

### Post by Rocket2DMn on 2008-04-28
OK, I guess the file really isn't there, but something seems to think it is.  Are you showing me all the output from the compiz --replace command?
Make sure you do, and also show me
```
cat /etc/X11/xorg.conf
```
It seems compiz is at least running, but it's just really really slow.
Run and post the output of
```
metacity --replace &
glxgears -info
```
and then
```
compiz --replace &
glxgears -info
```
You can then disable compiz again with the metacity command.  You may have to press Enter after running metacity or compiz to get back to a prompt.  The & will allow the command to run in the background so you can keep using the terminal.  I need to see how many FPS you are getting with glxgears.

---

### Post by Cpuboye11 on 2008-04-28
I believe i got everything...

**Command : compiz --replace  Information**
```

kyle@KylesLaptop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

kyle@KylesLaptop:~$ 
```
[B]
Command : cat /etc/x11/xorg.conf information[/B]
```

kyle@KylesLaptop:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```
[B]
Command: metacity --replace &          glxgears -info[/B]
```

kyle@KylesLaptop:~$ metacity --replace &
[1] 10177
kyle@KylesLaptop:~$ glxgears -info
GL_RENDERER   = Mesa GLX Indirect
GL_VERSION    = 1.2 (2.1 Mesa 7.0.3)
GL_VENDOR     = Mesa project: www.mesa3d.org
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATIX_texture_env_combine3 GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_point_sprite GL_NV_texgen_reflection GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays 
298 frames in 5.3 seconds = 55.737 FPS
254 frames in 5.1 seconds = 50.062 FPS
300 frames in 5.1 seconds = 58.387 FPS
300 frames in 5.2 seconds = 58.145 FPS
300 frames in 5.3 seconds = 56.678 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1.0"
      after 3143 requests (522 known processed) with 0 events remaining.
kyle@KylesLaptop:~$ 
```

**Command: Compiz --replace & glxgears -info**

```

kyle@KylesLaptop:~$ compiz --replace &
Checking for Xgl: [1] 10305
kyle@KylesLaptop:~$ present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

kyle@KylesLaptop:~$ glxgears -info
GL_RENDERER   = Mesa GLX Indirect
GL_VERSION    = 1.2 (2.1 Mesa 7.0.3)
GL_VENDOR     = Mesa project: www.mesa3d.org
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATIX_texture_env_combine3 GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_point_sprite GL_NV_texgen_reflection GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays 
176 frames in 6.6 seconds = 26.581 FPS
134 frames in 5.2 seconds = 25.780 FPS
200 frames in 5.5 seconds = 36.275 FPS
220 frames in 5.4 seconds = 40.578 FPS
220 frames in 5.4 seconds = 40.657 FPS
200 frames in 5.0 seconds = 39.710 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1.0"
      after 2499 requests (384 known processed) with 0 events remaining.
kyle@KylesLaptop:~$ 
```

---

### Post by Rocket2DMn on 2008-04-28
For some reason, it's back to using restricted drivers.  Can you please go to System->Administration->Hardware Drivers and make sure any ati restricted drivers are unchecked.  
Do:
```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh
```
Then open System->Administration->Synaptic Package Manager and search for "fglrx" - make sure you uninstall anything that is installed for this.
Reconfigure X again
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Restart X with CTRL+ALT+BACKSPACE
Now try to run
```
compiz --replace
```

---

### Post by Cpuboye11 on 2008-04-28
> **Rocket2DMn said:**
> For some reason, it's back to using restricted drivers.  Can you please go to System->Administration->Hardware Drivers and make sure any ati restricted drivers are unchecked.  
Do:
```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh
```
Then open System->Administration->Synaptic Package Manager and search for "fglrx" - make sure you uninstall anything that is installed for this.
Reconfigure X again
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Restart X with CTRL+ALT+BACKSPACE
Now try to run
```
compiz --replace
```


Yea that was odd.. I didn't reinstall them... Or at least i didn't mean to.... okay.. well sorry to say but no cigar..... Still no improvement....

I think it has gotten a little faster as i look at it, but still nothing like it was in 7.10........


But i would like to thank you for staying up or w/e and trying to help.. if any other ideas, that would be great....:-k

Thank You!

---

### Post by Rocket2DMn on 2008-04-28
I'm running out of ideas, I think you might need to consider reinstalling.  Did you install the restricted drivers in Gutsy and use Envy to do it?  If so, it's a known issue that you can run into problems if you don't remove the drivers and envy before upgrading distributions.  It seems like your card and drivers just don't want to play nice.
Alternatively, you can just live without Compiz...  It really is just eye candy and loses its glamor after awhile, but it's up to you.  Again, reinstalling may be the simplest fix for this at this point, we've tried pretty much everything else.

---

### Post by Cpuboye11 on 2008-04-28
I'm not going to lie to you... And maybe i didn't post this before... I bet i didn't... And i guess i should have...

I never installed Gutsy and Envy.....


Unless that is what was on the Ubuntu cd from 7.04 -- updated to 7.10 then to 8.05 or w/e....  I never installed any of those... 

I'm really a noob when it comes to this.. That is why i'm trying to learn Python and a bunch of other computer langs.. 

Would installing Gutsy or Envy help me solve this driver problem for the 7500m? 

And if so which one is better or is eaisyer to install..

---

### Post by Rocket2DMn on 2008-04-28
No, you don't want Envy, that is for restricted drivers which you DON'T want.  That seems to be the source of the problem, it thinks you are using restricted drivers (that's what fglrx is).  Gutsy = Gutsy Gibbon = 7.10 version of Ubuntu.
You were right not to use Envy.  I just feel like we're running in circles right now.  Essentially, you need to figure out how to purge the fglrx drivers from your system (if even possible) and have X use the open source "ati" drivers.  Once you have that, Compiz should run ok.

---

### Post by Cpuboye11 on 2008-04-28
> **Rocket2DMn said:**
> No, you don't want Envy, that is for restricted drivers which you DON'T want.  That seems to be the source of the problem, it thinks you are using restricted drivers (that's what fglrx is).  Gutsy = Gutsy Gibbon = 7.10 version of Ubuntu.
You were right not to use Envy.  I just feel like we're running in circles right now.  Essentially, you need to figure out how to purge the fglrx drivers from your system (if even possible) and have X use the open source "ati" drivers.  Once you have that, Compiz should run ok.


Well...... When you say open source drivers. Are you talking about the ones that i have to go to App- Add and Remove and find the ATI Binrys.. I just want to make sure. Because those are not installed... ( Just checked again )


The only problem i'm finding hard to understand is why the 7500 is no longer supported or runs like it did in 7.10.. in 7.10 there were no issues or errors.. All i did was install it let it update... And go to system then where ever apperence is and click Extra.. or w/e... And it worked.. I didn't have to change anything or type in any commands... Then i updated.. And then it doesn't work :(....

Just to ask.. Is there any easy way to figure out if you machine is running the X driver.. not the Flgx or w/e driver?



Edit: Man thanks for the help.. I don't know what time it is where you are.. but it is 2:01 am here and i have been up since 4:30..... So no rush on answering this time... I'm going to bed.. have to go to school in a few hours.. Well thanks again... for everything!

---

### Post by Rocket2DMn on 2008-04-28
The ATI binaries are the restricted drivers, that is what you DON'T want.
Compiz dropped support for cards using the open source ati drivers in Hardy because of a bug in the driver, and I suppose they didn't have the time or manpower to go test all different types of cards, so they blacklisted all of them.
You can post the output of
```
lsmod | grep radeon
lsmod | grep ati
lsmod | grep fglrx
```
The second command will probably return stuff we don't care about, but I included it just in case.  Open source driver = "ati" or "radeon".

Good night and good luck.

---

### Post by Cpuboye11 on 2008-04-28
```
lsmod | grep radeon
lsmod | grep ati
lsmod | grep fglrx
```



Got :

kyle@KylesLaptop:~$ lsmod | grep radeon
radeon                124192  3 
drm                    82580  4 radeon
kyle@KylesLaptop:~$ lsmod | grep ati
snd_atiixp_modem       17544  0 
cpufreq_conservative     8712  0 
snd_ac97_codec        101028  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
snd_pcm                78596  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    56996  28 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11400  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
kyle@KylesLaptop:~$ lsmod | grep fglrx
kyle@KylesLaptop:~$ lsmod | grep fglrx
kyle@KylesLaptop:~$ 

Lsmod |grep fglrx : Got nothing- i gess that is a good thing...

Kyle

---

### Post by Rocket2DMn on 2008-04-28
It would seem you are back to the open source drivers.  I would think that your card may just be too old to effectively run Compiz which is why it's lagging, but you and others have reported at least half decent results in Gutsy. One last time, post
```
compiz --replace
```
If I dont' see anything useful, I'm basically out of ideas.

---

### Post by Cpuboye11 on 2008-04-28
> **Rocket2DMn said:**
> It would seem you are back to the open source drivers.  I would think that your card may just be too old to effectively run Compiz which is why it's lagging, but you and others have reported at least half decent results in Gutsy. One last time, post
```
compiz --replace
```
If I dont' see anything useful, I'm basically out of ideas.


```
kyle@KylesLaptop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Starting gtk-window-decorator
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

Just sits there with a blinking icon or w/e...

I just close the termanial.. Screen flashes.. But it appears the effects are still running.... I will Edit back after a restart to see if they stick...



Edit: After Restart:

Hmm.. Effects are gone :(...

One thing i have noticed is that when the effects are off and on, my display has random lines every where... What is that from??

Edit again:

Could this have anything to do with Wine, and having the direct x dll or w/e installed...?

---

### Post by Rocket2DMn on 2008-04-28
Programs in wine might run a little weird with compiz enabled, but the rest of the system should be OK.
I ran across a suggestion earlier that might suit you.  A user had something similar, and they said that uninstall restricted-modules from previous kernels helped.  I want you test it out for me, run
```
sudo apt-get remove linux-restricted-modules-*
sudo apt-get autoremove
sudo apt-get install linux-restricted-modules-`uname -r`
```
Then reboot the computer and let me know what if compiz --replace works.

---

### Post by Cpuboye11 on 2008-04-28
> **Rocket2DMn said:**
> Programs in wine might run a little weird with compiz enabled, but the rest of the system should be OK.
I ran across a suggestion earlier that might suit you.  A user had something similar, and they said that uninstall restricted-modules from previous kernels helped.  I want you test it out for me, run
```
sudo apt-get remove linux-restricted-modules-*
sudo apt-get autoremove
sudo apt-get install linux-restricted-modules-`uname -r`
```
Then reboot the computer and let me know what if compiz --replace works.

Hmmm.. Small problem...

```

kyle@KylesLaptop:~$ sudo apt-get remove linux-restricted-modules
[sudo] password for kyle: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
kyle@KylesLaptop:~$ sudo apt-get remove linux-restricted-modules-*
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
kyle@KylesLaptop:~$ sudo apt-get autoremove
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
kyle@KylesLaptop:~$ sudo apt-get install linux-restricted-modules-`uname -r`
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
kyle@KylesLaptop:~$ 
```

Hmm... small problem.. If i remove the drivers away from the Hardware Drives menu and then uninstall... I won't have my Wireless or Ethernet...  Or modem... So i won't have any internet.. Should i still try it?

---

### Post by Rocket2DMn on 2008-04-28
You can't have Synaptic or any other package manager open when you run those commands.  You aren't uninstalling drivers, you are removing some modules, but the last command is reinstalling the ones for the kernel that you are currently in, so you shouldn't be missing anything.
If you know you don't have another package manager open, try rebooting the computer then running
```
sudo dpkg --configure -a
```
After that you should be able to run the commands I listed above.  If not, let me know and we will delete the lock file.

---

### Post by Cpuboye11 on 2008-04-28
Hmmmm... After doing this- 

I did Compiz --replace or w/e..

It seems to run a lot better... Just that.. Compiz --replace doesn't stay... I still get: 

```
kyle@KylesLaptop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

Hmmm.. The cursor or line is still blinking... And it doesn't stop.... And if i close it- it reverts back....

---

### Post by Rocket2DMn on 2008-04-29
It's OK that it doesn't take you back to the prompt.  You can run it with
```
compiz --replace &
``` to do that.  You are going to want to create launchers for it anyway (for compiz --replace and metacity --replace).

Now I need some serious feedback.  You said it runs a lot better... when did it start running better exactly?  After you removed the restricted-modules and reinstalled the one for your kernel (the 3 commands I gave above)?  Some other time?
I know there are other users getting
```
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
``` but if compiz is running OK, then you can probably ignore that line.  I need to know what worked so I can pass the word on.

---

### Post by Cpuboye11 on 2008-04-29
When i say it runs better- it runs little faster then before.. There is still glitch's and lines left after you move a program or window.... Overall it is better.... But it is not as good as it was in 7.10...

This happened after the 3 commands- and compiz --replace and then i restarted... Then it seemed to work a little better..... 

But yet again not perfect....

Hope that helps.. I thank you for the help, but i don't want to run but i gtg..... 
BED!!!!!! 

Any more questions feel free... Just wish they didn't black list it.. They should just fix the problem.. Lot of computers still have the older ATI cards.. I alone know 8 people with the same graphic card... Being the ATI 7500m.....

Oh well..

---

### Post by Rocket2DMn on 2008-04-29
Alright, why don't you post the output of all these commands for me, just for the record (you've run them all before).  Let the glxgears commands run for a few cycles, then you can exit.
```
lspci | grep VGA
cat /etc/X11/xorg.conf
metacity --replace &
glxgears -info
compiz --replace &
glxgears -info
```
This will be a last ditch effort to clear up the weird line problem.  That sounds like it X may not like your monitor very much.  If it only happens with compiz, it could be a result of one of the plugins for it.

---

### Post by Cpuboye11 on 2008-04-29
> **Rocket2DMn said:**
> Alright, why don't you post the output of all these commands for me, just for the record (you've run them all before).  Let the glxgears commands run for a few cycles, then you can exit.
```
lspci | grep VGA
cat /etc/X11/xorg.conf
metacity --replace &
glxgears -info
compiz --replace &
glxgears -info
```
This will be a last ditch effort to clear up the weird line problem.  That sounds like it X may not like your monitor very much.  If it only happens with compiz, it could be a result of one of the plugins for it.

```
kyle@KylesLaptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
kyle@KylesLaptop:~$ cat /etc/x11/xorg.conf
cat: /etc/x11/xorg.conf: No such file or directory
kyle@KylesLaptop:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
kyle@KylesLaptop:~$ metacity --replace &
[1] 6680
kyle@KylesLaptop:~$ glxgears -info
GL_RENDERER   = Mesa GLX Indirect
GL_VERSION    = 1.2 (2.1 Mesa 7.0.3)
GL_VENDOR     = Mesa project: www.mesa3d.org
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATIX_texture_env_combine3 GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_point_sprite GL_NV_texgen_reflection GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays 
418 frames in 5.2 seconds = 80.381 FPS
400 frames in 5.3 seconds = 76.094 FPS
400 frames in 5.2 seconds = 76.397 FPS
400 frames in 5.2 seconds = 76.278 FPS
360 frames in 5.3 seconds = 68.107 FPS
354 frames in 5.2 seconds = 67.632 FPS
380 frames in 5.0 seconds = 75.984 FPS
380 frames in 5.0 seconds = 75.328 FPS
380 frames in 5.0 seconds = 75.922 FPS
380 frames in 5.1 seconds = 74.763 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1.0"
      after 8383 requests (3944 known processed) with 0 events remaining.
kyle@KylesLaptop:~$ compiz --replace &
Checking for Xgl: [2] 6718
kyle@KylesLaptop:~$ present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

[1]-  Done                    metacity --replace
kyle@KylesLaptop:~$ 1
bash: 1: command not found
kyle@KylesLaptop:~$ compiz --replace &
Checking for Xgl: [3] 6737
kyle@KylesLaptop:~$ present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

[2]-  Done                    compiz --replace
kyle@KylesLaptop:~$ glxgears -info
GL_RENDERER   = Mesa GLX Indirect
GL_VERSION    = 1.2 (2.1 Mesa 7.0.3)
GL_VENDOR     = Mesa project: www.mesa3d.org
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATIX_texture_env_combine3 GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_point_sprite GL_NV_texgen_reflection GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays 
256 frames in 5.4 seconds = 47.407 FPS
220 frames in 5.4 seconds = 40.742 FPS
220 frames in 5.4 seconds = 40.810 FPS
220 frames in 5.2 seconds = 42.536 FPS
220 frames in 5.3 seconds = 41.844 FPS
220 frames in 5.4 seconds = 40.853 FPS
220 frames in 5.3 seconds = 41.703 FPS
220 frames in 5.4 seconds = 40.755 FPS
220 frames in 5.3 seconds = 41.542 FPS
220 frames in 5.4 seconds = 40.682 FPS
220 frames in 5.4 seconds = 40.684 FPS
220 frames in 5.1 seconds = 42.988 FPS
220 frames in 5.1 seconds = 42.896 FPS
220 frames in 5.2 seconds = 42.522 FPS
200 frames in 5.2 seconds = 38.700 FPS
220 frames in 5.3 seconds = 41.836 FPS
220 frames in 5.5 seconds = 39.902 FPS
220 frames in 5.3 seconds = 41.621 FPS
220 frames in 5.4 seconds = 41.014 FPS
220 frames in 5.3 seconds = 41.225 FPS
220 frames in 5.3 seconds = 41.766 FPS
220 frames in 5.3 seconds = 41.352 FPS
220 frames in 5.4 seconds = 40.938 FPS
220 frames in 5.3 seconds = 41.499 FPS
220 frames in 5.3 seconds = 41.223 FPS
220 frames in 5.3 seconds = 41.615 FPS
220 frames in 5.3 seconds = 41.232 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1.0"
      after 12231 requests (38 known processed) with 0 events remaining.
kyle@KylesLaptop:~$ 

```

---

### Post by Rocket2DMn on 2008-04-29
Are those fatal errors with glxgears coming when you kill the program yourself, or does it just suddenly do it after awhile?  If that latter, you have a bigger problem on your hands.  In that case you may consider
1) a reinstall
2) a BIOS upgrade
3) a different video card

Other than that, I am out of ideas.
It could just be that your card is not going to work any more with Compiz Fusion.

---

### Post by Cpuboye11 on 2008-04-29
> **Rocket2DMn said:**
> Are those fatal errors with glxgears coming when you kill the program yourself, or does it just suddenly do it after awhile?  If that latter, you have a bigger problem on your hands.  In that case you may consider
1) a reinstall
2) a BIOS upgrade
3) a different video card

Other than that, I am out of ideas.
It could just be that your card is not going to work any more with Compiz Fusion.

```
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1.0"
      after 12231 requests (38 known processed) with 0 events remaining.

```

I did it on the last one.. and it happened when i hit the X on the gears box...

EDIT: WHEN I CLOSED IT!

---

### Post by Rocket2DMn on 2008-04-29
OK.  Don't do a bug report for compiz since this card is not supported, but if you can't get the regular open source ati drivers to work normally (with metacity - no desktop effects), then you can fill out a bug report.

---

### Post by Cpuboye11 on 2008-04-29
Should I try and reinstall the operating system completely? 

And hope for the best?

---

### Post by Cpuboye11 on 2008-04-29
Something else i have just recently noticed....

When i close my laptop lid... And leave it alone the monitor shuts off.. Like always.. But i open it and click on the mouse or the keyboard, and it won't come back on... I just realized this... It would come back on in 7.10......

This is in compiz and metacity....:(

---

### Post by Rocket2DMn on 2008-04-29
If you are willing to give a reinstall a try, you can go for it and hope for the best.  This sometimes solves problem's but there are no guarantees.
If it doesn't work, you can mention on LP that you tried all the stuff we did earlier in this thread as well as the fresh install.  This can help with your bug report because you can assure them that the bug exists right out of the box.
That monitor problem is not new, many people have had that, you would have to do a forum search to see details.  I would ignore it for now and do the reinstall if possible.  Just make sure you back up all your data first.

---

### Post by Cpuboye11 on 2008-04-29
REINSTALL IS THE KEY.... EVERYTHING WORKS NOW... WELL..... CAN'T GET THE CUBE TO RUN, BUT I DON'T CARE, EVERYTHING ELSE RUNS GREAT... [CENTER]:guitar::guitar::guitar: 
:):):)
:KS:KS[/CENTER]


All the general effects run.

THANK SO MUCH FOR YOUR HELP... 

Reinstall and follow your read me or w/e.. WORKED!

---

### Post by Rocket2DMn on 2008-04-29
booya!
I will start suggesting a reinstall earlier in the process to users who have problems when trying to upgrade.

---

