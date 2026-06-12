---
title: "Hardy and the post install mayhem (8 questions remain unsolved)"
date: 2008-04-27
forum: General Help
---

### Post by SpaceTeddy on 2008-04-27
I though this would be easy... installing the new release. After two days of working on it (and one complete reinstall - kept the /home), i finally got it to a stage where it is sort of useable - and that is also my problem ! it is only **sort of** usable :(

so - here are my question. I hope someone out there can answer them (as opposed to most of my other questions here). I am already looking forward to answers

1.) **All my Movies are pixeled.**
I don't know what to do anymore. Compiz on or off, using all possible settings in the gstreamer-properties, using totem, vlc, mplayer and gxine (all with all possible output modes) movies always look bad. I did not have this problem in gutsy... so how come they are pixeled now.
QUESTION:**How do i get good movie quality again ?**

2.) **Movies suck a huge amount of CPU.**
A normal Divx file (700 Mbyte, 90 mins) can be played, but anything that has a higher quality (h264 codec, 4.4Gig, mkv format) will simply be choppy as the cpu is not fast enough. Again, whatever i do, which ever player i use... compiz or not. It does not make a difference.
QUESTION: **How can i put the movies on the Graphics card again ?**

3.) **Any openGL application flickers like crazy when using compiz**
That pretty much describes it... And NO, turning compiz off is NOT an option. I need the widget layer. So unless there is a way to have a widget layer and no compiz, i can turn it off. Otherwise - no way.
QUESTION: **Why does the GL support through Compiz not work anymore ?**

4.) **Alltray does not work anymore.**
I need it to let thunderbird stay in the background. Whenever i run something with alltray, it goes to the tray, but does not overwrite the close button and cannot be "trayed" anymore. kdocker sort of does the job, but the close button is (also) not overwritten and i get very annoying pop-ups at the top-right whenever i click something on thunderbird. I have no tried running this without compiz.
QUESTION: **how do i minimize thunderbird to the tray ?**

5.) **The Emulated PC speaker activated itself.**
This acctually scared the **** out of the when i hit tab twice the first time. How do i turn the thing off permanently. I don't want my computer to beep, whine, bing or make any other sound. I only want it to play music - no other sound.
QUESTION: **How do i shut the PC-Speaker up ?**

6.) **Firefox does not have java support anymore.**
When i tried to download something from IBM, the Website told me that Java cannot be started. I have no idea why ? 
QUESTION: **How do i enable Java in Firefox again ?**

7.) **Tracker makes the system go spastic.**
Whenever i do something in my files, tracker jumps in and runs itself crazy on my CPU. 5-15 minutes of full CPU are happening here. The question is not acctually how i can minimize that, but what is tracker good for anyway ? in gutsy, i just disabled the thing...
QUESTION:**Why should i keep tracker ?**

Bonus Question.) **Install of Lotus Notes 8.0.1 throws errors like crazy**
If anybody could answer that, you'd so make my day. But i know this is probably not going to happen.
QUESTION:**How do i install Lotus Notes 8.0.1 Client on Hardy**

So, if anybody can answer any or all of these questions, PLEASE do so. I've spend the whole weekend trying to solve them, and i am pretty much out of ideas. Also, you don't need to explain it in baby steps to me, just throw me some bones or tutorials and i will try them out. But if you do feel the urge to explain (for documentational reason) you are also quite welcome to do so... maybe these questions help someone else aswell.

Thanks to anybody who answers :)

PS: despite all these problems don't get me wrong - i like the new release :)

---

### Post by rbmorse on 2008-04-27
Issues 1,2 and 3 are doubtlessly the result of a defective or incomplete video driver installation. Do you know which video adapter is installed in the machine?

---

### Post by kavon89 on 2008-04-27
#1, #2, #3: It seems this poor performance, quality, and glitching is related to your graphics card and it's drivers.

Perform this command and let it run for about about 10 seconds and post the results (frames per second) to see how efficiently your graphics are running.

```
glxgears
```

Also, what kind of graphics card do you have? Run this command and post the result:

```
lshw -class display
```

#5, system beep: right click the speaker icon, Open Volume Control. Then goto Edit>Preferences and look for anything like Beep or System Speaker etc and check it on. Then in Playback, or in another tab, look for the volume control for it and mute it.

#6, Java: System>Administration>Synaptic Package Manager

Hit Reload, then Search for sun-java6-plugin and install it.

EDIT: In regards to #5 with the system beep, System>Preferences>Sound has a tab to disable system beep completely. The method I have above probably just mutes it, not disabling it completely.

---

### Post by SpaceTeddy on 2008-04-28
> **kavon89 said:**
> ```
glxgears
```

full output of the thing ( i know been running a little long). Also it still flickers like crazy... But the gears run smooth
> laptop:~$ glxgears
24094 frames in 5.0 seconds = 4818.696 FPS
26552 frames in 5.0 seconds = 5310.362 FPS
26455 frames in 5.0 seconds = 5290.954 FPS
26839 frames in 5.0 seconds = 5367.640 FPS
26682 frames in 5.0 seconds = 5336.282 FPS
25343 frames in 5.0 seconds = 5068.578 FPS
24297 frames in 5.0 seconds = 4859.284 FPS
26092 frames in 5.0 seconds = 5218.363 FPS
24063 frames in 5.0 seconds = 4812.508 FPS
25285 frames in 5.0 seconds = 5056.926 FPS
24486 frames in 5.0 seconds = 4897.117 FPS
25577 frames in 5.0 seconds = 5115.342 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 308556 requests (308555 known processed) with 0 events remaining.


also, my graphics drivers seem to be loaded
> laptop:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.1.7412 Release



> **kavon89 said:**
> ```
lshw -class display
```

Ok, again full output:
> laptop:~$ lshw -class display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: M56P [Radeon Mobility X1600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx


> **kavon89 said:**
> 
#5, system beep: right click the speaker icon, Open Volume Control. Then goto Edit>Preferences and look for anything like Beep or System Speaker etc and check it on. Then in Playback, or in another tab, look for the volume control for it and mute it.

i've already fixed that problem by blacklisting the pcspkr module in the blacklist of modules never to load. Was the quickest way to do it :)

> **kavon89 said:**
> Java
ok, that fixed it - thanks. I installed only the jre - not the plugin. But the java support works now. I can download from IBM :)

---

### Post by kavon89 on 2008-04-28
I'm not too sure, your drivers seem to be working. I did a bit of searching and maybe direct rendering isn't enabled? Is this the same ATI driver version that you had before you upgraded?

---

### Post by SpaceTeddy on 2008-04-29
No, these are not thesame drivers, as the kernel version has updated and so the ATI driver from the restreicted repositories. So i'd *guess* this is a different version. But i cannot be sure...

As for the direct rendering - i am sure it is on:
> laptop:~$ glxinfo 
name of display: :0.0
display: :0  screen: 0
**direct rendering: Yes**
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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


that does not answer the question - unforteunatly... 
i've also done some more testing last night - if i load metacity instead of compiz and then force mplayer to use the OpenGL output layer, the quality of movies improves drasticially and the cpu usage does down. When compiz is enabled, the picture flickers like crazy - being unwatchable... 

that totally confused me...
i'll attach two screens - one with totem and compiz, one with mplayer and metacity...

PS: i don't know why one file is three times the size of the other - both are just done via screenshot in ubuntu... i've not changed or converted anything. (also sorry for the huge size :( )
PPS: the forum scaled them down... hope the difference is still visible...

---

### Post by Kaneda187 on 2008-05-12
I have the same problem with my video quality, ati radeon x1400 so annoying my friend has the same laptop with the same problem, didnt have it in gutsy????:confused: really annoying! gotta be a fix!

---

### Post by SpaceTeddy on 2008-05-12
I use mplayer in gl mode, and turn compiz off. Then the movies are acctually watchable. 
But that is an ugly work around... i have having to unload all screenlets and then force metacity to load.

i found no other player that is even capable of playing movies with decent quality...

---

