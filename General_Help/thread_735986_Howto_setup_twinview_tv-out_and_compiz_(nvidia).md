---
title: "Howto setup twinview tv-out and compiz (nvidia)"
date: 2008-03-26
forum: General Help
---

### Post by Kiri on 2008-03-26
It took a LONG time for me to get this working properly, and a lot of research. So I thought I would post the information here for others who might have problems.



This will probably only work for people running the nvidia-glx-new restricted drivers.



1) Enable the restricted drivers (system>admininstration>hardware drivers)

2) Enable compiz desktop effects (appearance>visual effects) * You may need to install compiz first

3) Install nvidia-settings from synaptic or terminal

4) backup your xorg.conf file

5) from terminal run:
sudo nvidia-settings

6) It should show you your current display and a disabled TV display. Click on the TV display and press configure. Then you should select TwinView (see below for info about separate X window). It doesn't say that you need to restart X, but I had problems when I just tried to apply it, so I recommend doing it this way:
Do NOT click apply. Instead press the button to save the changes to xorg.conf. 
Exit, and restart the computer (this may not be necessary, but I strongly recommend it since this was one of the things which finally got mine working properly).

7) When you load back up, twin view 'should' be working. I had a lot of troubles and tried a lot of different settings before I managed to get it going properly, which is why I'm posting these steps here to hopefully make it as painless as possible.


8) Now you should have TwinView working and can drag windows over to the TV and play fullscreen video on it while still working on your desktop on your main display. 
If you are using the 3D cube in compiz you will notice that rotating the cube now rotates the whole twinview desktop (so you have really big cube sides). I didn't like this, so I changed the cube setting (system>preferences>advanced desktop effects), in the compizconfig settings window click on Desktop Cube then general tab and choose 'multioutput mode>multiple cubes'

Now the cubes rotate separately and are the standard size for each desktop.


----

About separate X windows in nvidia-settings.

I did manage to get this working too. But the only way I could get it going AND keep compiz was not to enable the Xinerama setting in the nvidia-settings. I think the compiz uses its own version of xinerama (?) so perhaps they were conflicting. 
Unfortunately separate X windows didn't perform well on my machine (sluggish minimize / maximize etc)


----


How this helps some people out. I went through a lot for what seems like a fairly simple setup, so if anyone has any questions or needs more info feel free to ask.  
Enjoy the fullscreen movies! :popcorn:

---

### Post by leotemp on 2008-04-30
When i attempt this my second monitor which is plugged into the back of my 8800gts doesn't have any options to configure under nvidia settings, its listed as crt 2 (odd as both monitors are lcd) and when i click it there are no configuration options at all. Any ideas?

---

### Post by Kiri on 2008-05-01
in nvidia settings first you will need to enable it to use twinview, then you should have some options.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-05-04
yes but can you make them rotate independantly of each other

---

### Post by mikko.ohtamaa on 2008-05-10
> **Kiri said:**
> About separate X windows in nvidia-settings.

I did manage to get this working too. But the only way I could get it going AND keep compiz was not to enable the Xinerama setting in the nvidia-settings. I think the compiz uses its own version of xinerama (?) so perhaps they were conflicting. 
Unfortunately separate X windows didn't perform well on my machine (sluggish minimize / maximize etc)


Please see this thread too:

[http://ubuntuforums.org/showthread.php?p=4929055#post4929055](http://ubuntuforums.org/showthread.php?p=4929055#post4929055)

---

### Post by The Radio G on 2008-07-03
I have been tweaking my NVIDIA settings all week and I can't get my TV Out to function properly in conjunction with my widescreen LCD.

I have recently installed Ubuntu 8.04 and have an older NVIDIA GeForce 4000 something-or-other.  I have successfully installed the proper legacy drivers from NVIDIA, and after a battle with 640x480 resolution on my monitor I am functioning at the proper 1440x900.

Now, every time I try to enable the TV display, either as a separate x screen or twinview, I get very unexpected results.  This was indeed what originally triggered the low-res problems; it has also caused the x screen to boot on the tv (in the other room!) and nothing on my monitor, and most recently with the tv disabled again I am unable to run visual effects without loosing the title bar of my windows.

Can anyone offer specific insight on configuring an Acer AL1916W and TV Out on a GeForce 4000 card in an Ubuntu 8.04 environment?

---

