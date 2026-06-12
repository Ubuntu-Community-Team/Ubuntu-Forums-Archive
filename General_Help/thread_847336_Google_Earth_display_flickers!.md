---
title: "Google Earth display flickers!"
date: 2008-07-02
forum: General Help
---

### Post by hemajith on 2008-07-02
I just installed Google Earth 4.2 on my Ubuntu. It works fine except for the fact that the display window starts flickering when I get the required images! It is hard to see anything in the window while it flickers.
I have enables mt VGA card which is a ATI from Hardware drivers. There is nothing wrong with the card. Is there anything else I have to adjust or do?

---

### Post by theshadowwithanmp5n on 2008-07-02
for some reason, ATI graphics cards flicker on ubuntu, there's a fix, but i have to ask my friend because he had the same problem. does you card happen to be an ATI Radeon? it's not a fix, more like a workaround, but it should do the trick

---

### Post by rossjman1 on 2008-07-02
You need to disable Compiz before using Google Earth or playing certain video game.

---

### Post by jualin on 2008-07-02
> **rossjman1 said:**
> You need to disable Compiz before using Google Earth or playing certain video game.

Exactly disabling Compiz helps a lot when having two application using 3D, such as Google Earth and Compiz.

---

### Post by hemajith on 2008-07-03
I do have ATI Radeon! It never flickers on anything. Videos and everything else I try on Ubuntu, works fine. Only Google Earth is giving me the problem. Maybe I should disable the compiz? I'm a bit new to Ubuntu, how exactly do I do that?

---

### Post by jualin on 2008-07-04
You can install "fusion-icon" from the synaptic package manager or from the terminal > sudo apt-get install fusion-icon
After you install this package you need to go to Applications, System Tools, Compiz Fusion Icon. This will open a little Compiz Icon in the Notification Bar (next to the clock) and you can right click on it to enable or disable Compiz. To disable compiz just select "Metacity" as a new Window Manager. Hope this helps!

---

### Post by theshadowwithanmp5n on 2008-07-05
or you could just go to system preferences advanced desktop effects settings
you can disable it there without installing any additional software.

---

### Post by hemajith on 2008-07-05
> **jualin said:**
> You can install "fusion-icon" from the synaptic package manager or from the terminal 
After you install this package you need to go to Applications, System Tools, Compiz Fusion Icon. This will open a little Compiz Icon in the Notification Bar (next to the clock) and you can right click on it to enable or disable Compiz. To disable compiz just select "Metacity" as a new Window Manager. Hope this helps!

It worked! Disabling compiz solves the problem in GE. What is the advantage of having Compiz enabled? Do I disable it only when using GE or any other software that gives the same problem?

---

### Post by jualin on 2008-07-05
Compiz is what gives your computer all the eye-candy 3D effects, just like Windows Vista and Leopard. However having Compiz enabled sometimes makes other 3D applications not work correctly. Disabling it Compiz everytime you want to run a 3D applications which is having problems usually solves the problem. If you don't like the 3D effects (Desktop Cube, Minimize Effects) you can disable Compiz entirely, however if you rarely use Google Earth or any other 3D application you can have Compiz enabled so you can enjoy the effects. Linux is about choices, and the choice is yours, you are the only one who can decide what to do. In my personal experience I have Compiz enabled to beautify my desktop and for functionality (Ctrl+Shift+Up effect, 3D Cube), and whenever I want to use Google Earth or Frets on Fire I disable Compiz.

---

### Post by manolomanolo on 2008-07-11
It worked for me too. Disabling Compiz makes Google Earth not flick any more on Ubuntu 8.04 Hardy Eron on Asus F3Ja using ATI Mobility Radeon X1600
Anyone placing a SOLVED on this thread?

---

### Post by Faz1 on 2008-11-10
> **jualin said:**
> You can install "fusion-icon" from the synaptic package manager or from the terminal 
After you install this package you need to go to Applications, System Tools, Compiz Fusion Icon. This will open a little Compiz Icon in the Notification Bar (next to the clock) and you can right click on it to enable or disable Compiz. To disable compiz just select "Metacity" as a new Window Manager. Hope this helps!

Thanks jualin!

My problem wasn't specifically with Google Earth but general video issues as others have experienced.

I knew there had to be a simple, (and quick!) toggle approach.  This reminds me of the Beryl icon.

No more, System, Preferences, Appearance, Visual Effects tab, None.
Then enabling again, launching CompizConfig, and importing my profile... :roll:


The following instructions will load Compiz Fusion Icon after each login:

System, Preferences, Sessions.
Click Add then enter:
 
Name:    Compiz Fusion Icon
Command: fusion-icon --no-start
Comment: Start and manage Compiz Fusion

Click Add then Close.

---

### Post by eitan_a on 2008-11-29
> **manolomanolo said:**
> It worked for me too. Disabling Compiz makes Google Earth not flick any more on Ubuntu 8.04 Hardy Eron on Asus F3Ja using ATI Mobility Radeon X1600
Anyone placing a SOLVED on this thread?


I'm sorry, but this is exactly why Linux will never, ever become mainstream.  If you think a windows or mac user would be o.k. with disabling their desktop effects to run a compatible program, then you've got another thing coming.  

I remember this bug from 1.5 years ago, since Google Earth was released for linux, and I still can't believe they haven't figured this out.  Don't tell me that linux has the same desktop effect razzle-dazzle that mac and windows have, because in those systems you don't need to disable anything to run a program.

---

### Post by charlescarroll1 on 2008-12-20
> **eitan_a said:**
> I'm sorry, but this is exactly why Linux will never, ever become mainstream.  If you think a windows or mac user would be o.k. with disabling their desktop effects to run a compatible program, then you've got another thing coming.  

I remember this bug from 1.5 years ago, since Google Earth was released for linux, and I still can't believe they haven't figured this out.  Don't tell me that linux has the same desktop effect razzle-dazzle that mac and windows have, because in those systems you don't need to disable anything to run a program.

Yes, I completely agree.  Some of these "workarounds" can be quite a nuisance.  I don't want to have to disable my desktop effects every time I want to run certain programs like Google Earth.  The only thing that is keeping me from completely migrating to Ubuntu from Windows is the compatibility issues Ubuntu has.  Don't get me wrong, but I will dual-boot until I feel issues like these are resolved.

That fusion-icon helps though :D

---

### Post by Faz1 on 2008-12-21
> **eitan_a said:**
> I'm sorry, but this is exactly why Linux will never, ever become mainstream.  If you think a windows or mac user would be o.k. with disabling their desktop effects to run a compatible program, then you've got another thing coming.  

I remember this bug from 1.5 years ago, since Google Earth was released for linux, and I still can't believe they haven't figured this out.  Don't tell me that linux has the same desktop effect razzle-dazzle that mac and windows have, because in those systems you don't need to disable anything to run a program.

> **charlescarroll1 said:**
> Yes, I completely agree.  Some of these "workarounds" can be quite a nuisance.  I don't want to have to disable my desktop effects every time I want to run certain programs like Google Earth.  The only thing that is keeping me from completely migrating to Ubuntu from Windows is the compatibility issues Ubuntu has.  Don't get me wrong, but I will dual-boot until I feel issues like these are resolved.

That fusion-icon helps though :D

Agree and Agree!

I would have hoped the community would have addressed such issues by now.

Maybe Ubuntu needs a more streamlined crash / bug reporting system...

---

### Post by sjl127 on 2009-01-21
It may be a nuisance now, but it will be worked out.  I for one am glad that I am not bound by Microsoft anymore to use stuff envisioned in their eyes.  I can do what I want to do, how I want to.  And for that right, those 3 clicks are worth it.

---

### Post by Faz1 on 2009-01-22
> **sjl127 said:**
> It may be a nuisance now, but it will be worked out.  I for one am glad that I am not bound by Microsoft anymore to use stuff envisioned in their eyes.  I can do what I want to do, how I want to.  And for that right, those 3 clicks are worth it.

Agreed!

---

### Post by moster on 2009-01-22
I replace radeon with nvidia and forgot about any problem with video/opengl/compiz. Just a sugestion.

---

### Post by Lektorvis on 2009-02-03
To eitan_a and charlescarroll1 I agree it is 	
annoying to wait years for bugs to be resolved. But don't blame it all on the Linux community. If the Graphic Card manufactures were more cooperative to the Linux project it would be must easier to resolve these problems.

---

### Post by benhur99ph on 2009-02-10
Uhmmm... guys... its free! 
I wouldn't mind turning off my compiz in order to launch Google Earth. A very minor thing to do. 

@Lektorvis - yeah... if only they cooperate with the Linux developers then there will be no video card issue. It will like when you buy a new card and there's that extra option in the driver disc  --  "Linux Driver".

---

### Post by Dr Zin on 2009-02-19
Well I would have to Say Google Earth Kicks As*. yes I am going through a learning here with Ubuntu.  Here the Best FIX for Kubuntu users that have found  is ******<System setting--> Configure desktop effects --> General Tab -->Advanced Options --> Compositing Type: -->[OpenGL][XRender] select XRender this should work for the ATI Radeon cards. It still flickers some but as bad. I an believe that it not ubuntu issue that is a OpenGL issue.

---

### Post by dtsmith1984 on 2009-02-25
I have the same problem with my ATI Radeon X1650 w/ Compiz.


I could not figure out how to get Totem to stop flickering and/or corrupting the picture so I used VLC and set the video output of VLC to X11 and this fixed the video playback issues. 

Is there any way to change the video output mode on GoogleEarth like I did for VLC?

---

### Post by freemath on 2009-03-19
I want to confirm this issue and the solution provided. My laptop has Intel Graphics X3100, running Intrepid. Googleearth display flickers with a lot of static and realistically not usable. Turning off Desktop Effect solves the problem.

Thank you!

---

### Post by SnakeMedia on 2009-03-20
Hello guys, 

i know that problem of flickers....

Please do not forget your backup for windows softwares and windows partitions to big network hard disk or more DVD images with 7zip small bytes....

Than we would to format with one or more hard disks three time formating while your clean installation of Ubuntu Desktop and clean effectives of compiz no flickers. :).

Like this:
1x or 3x and more to format with your hard disk because your hard disk need new start without recovers!!!! Important! 

How do i know about problem of flickers?
If you have installed windows xp or vista with crazy 0-byte-recovers on hard disk than Ubuntu has conflict of recovers by Windows versions. My deaf friend has token that problem and conflict. Do not worry! You want to use with Windows XP or Vista and another Versions...
We need  with using VirtualBox 2.1.x with OpenGL and D3D ( VMGL ).
Important: Do not start with dxdiag!!!!!!!!!!!!!!!!!!!!!
Breatful i have tried with OpenArena on Windows Guest. Work really! No problem with Half-Life 2 and DirectX-10-Games work on VirtualBox Windows Guest powerfully!!!!!!!! A lot of thanks, Cheers from US! Good work! Adresse: [http://www.dedoimedo.com/computers/virtualization-3d-support-virtualbox.html](http://www.dedoimedo.com/computers/virtualization-3d-support-virtualbox.html)
Because VirtualBox Machine Additions happens by dxdiag. Now leave that dxdiag application of Microsoft Windows. Now we change to compiz-effectives. It likes new computer :D.

I hope you because you can 1x or 3x format with clean fresh-non recovering hard disk.

Bist regards, SnakeMedia

---

### Post by DeeMenace on 2009-09-10
> **SnakeMedia said:**
> Hello guys, 

i know that problem of flickers....

Please do not forget your backup for windows softwares and windows partitions to big network hard disk or more DVD images with 7zip small bytes....

Than we would to format with one or more hard disks three time formating while your clean installation of Ubuntu Desktop and clean effectives of compiz no flickers. :).

Like this:
1x or 3x and more to format with your hard disk because your hard disk need new start without recovers!!!! Important! 

How do i know about problem of flickers?
If you have installed windows xp or vista with crazy 0-byte-recovers on hard disk than Ubuntu has conflict of recovers by Windows versions. My deaf friend has token that problem and conflict. Do not worry! You want to use with Windows XP or Vista and another Versions...
We need  with using VirtualBox 2.1.x with OpenGL and D3D ( VMGL ).
Important: Do not start with dxdiag!!!!!!!!!!!!!!!!!!!!!
Breatful i have tried with OpenArena on Windows Guest. Work really! No problem with Half-Life 2 and DirectX-10-Games work on VirtualBox Windows Guest powerfully!!!!!!!! A lot of thanks, Cheers from US! Good work! Adresse: [http://www.dedoimedo.com/computers/virtualization-3d-support-virtualbox.html](http://www.dedoimedo.com/computers/virtualization-3d-support-virtualbox.html)
Because VirtualBox Machine Additions happens by dxdiag. Now leave that dxdiag application of Microsoft Windows. Now we change to compiz-effectives. It likes new computer :D.

I hope you because you can 1x or 3x format with clean fresh-non recovering hard disk.

Bist regards, SnakeMedia



Ummmm HUh ?

---

### Post by johnpap on 2009-10-19
All I did was to select "no visual effects" from the apearence menu and google earth stopped flickering...!

---

### Post by sjpn on 2009-12-17
Does anyone know if there's a way to run google earth with an ati card and also have 3d buildings? (other than starting windows)

---

### Post by vertago1 on 2011-01-05
This is also a problem when using KDE with desktop effects enabled with ATI graphics.

ATI ought to look into this when updating the driver because it isn't an issue on my laptop which uses an intel chipset.

---

