---
title: "beryl."
date: 2006-11-21
forum: General Help
---

### Post by STREETURCHINE on 2006-11-21
good afternoon all,i decided to give beryl a try so i have done everything in the beryl &compiz guide,been to wiki ,and a couple of outher posts here ,now i think it is in here because i have the icon in the top bar ,
i am using gnome,
my graphics card is an nvidia geforce fx 5200

nvidia is installed and running (thanks to automatix2)
i just dont seem to be able to get beryl to do anything,(like rotating cube)or any of the outher stuff everyone is talking about.:D

---

### Post by catanzag on 2006-11-21
you can start beryl from command line with ```
beryl-manager --replace
```
or from the menu (click in the icon) you can select beryl (or emerald, I'm not at my ubuntu box now) as window manager (to replace metacity, which is the standard one)

let us know

regards

---

### Post by STREETURCHINE on 2006-11-21
yep tried all them,but no cookie .i have been through the drop down menu but just dont seem to want to play the game.](*,)

---

### Post by hellraiser_rob on 2006-11-21
have you got the beta nvidia drivers installed?

---

### Post by STREETURCHINE on 2006-11-21
i have no idea ,just the ones that automatix2 installs

---

### Post by catanzag on 2006-11-21
As I told you, I'm not on my ubuntu box; if I remember well, there should be a menuItem called *Select window manager* (or something like that) with a coupled of option, beryl and metacity.

BTW, did you installed both beryl and emerald? do you use XGL or AIGLX? in any case, are there  any errors/warnings in /var/log/Xorg.*.log  or in the output of dmesg? My question arise from the possibility that something in GL doesn't work correctly.

---

to know nvidia driver version, ```
dpkg -l|grep -i nvidia
```

---

### Post by STREETURCHINE on 2006-11-21
yes they are there but when i click nothing happens,
and yes i used glx but there was an error when i finished,i used this guide first 
[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

then tried a couple of outhers to try to fix the prob .

---

### Post by STREETURCHINE on 2006-11-21
here is the out put fromdpkg -l|grep -i nvidia

ex@Linux:~$ dpkg -l|grep -i nvidia
ii  nvidia-glx                             1.0.8776+2.6.15.12-1   NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-glx-dev                         1.0.8776+2.6.15.12-1   NVIDIA binary XFree86 4.x/X.Org driver devel
ii  nvidia-kernel-common                   20051028+1   NVIDIA binary kernel module common files
rex@Linux:~$

---

### Post by arochester on 2006-11-21
I have managed to install Beryl. I use Edgy, have NVidia and use Kubuntu. I use Automatix2.

I use the instructions at [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA)

I thought I had failed and would stop. Then I noticed that my NVidia screen, which flashes up for a split second, was different from the NVidia screen I was used to as downloaded from the Repositories.NVidia beta!

I checked for direct rendering and got a Yes.

It didn't seem to want to work through the CLI and I put the Beryl Repository into Synaptic. It came up with a lot of Beryl programs as New in the Repository. I downloaded them and it went.

---

### Post by catanzag on 2006-11-21
ok, 8776, so no AIGLX, only Xgl; is it correctly installed and configured? as you got an error, you could uninstall Xgl, beryl and emerald packages and try to reinstall them all; a good guide you can use is this one on beryl site: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL)

which is the same (I noticed now, sorry) of the previous post for Dapper

---

### Post by PriceChild on 2006-11-21
Beryl is not a beginners subject.

*moved*

---

### Post by Random20230808 on 2006-11-21
One thing you should be sure about is that you have Xgl or Aiglx correctly installed and running. I didn't read in your post which enviroment do you use.
I think the following post is helpful enough for all the work you have to do. Follow the instructions and write back if you still have problems.
[https://help.ubuntu.com/community/CommonQuestions#head-23187ff8609335c10dbb55c6cdc4c1f47fddcda0]("https://help.ubuntu.com/community/CommonQuestions#head-23187ff8609335c10dbb55c6cdc4c1f47fddcda0") (Official Ubuntu Support)

---

### Post by STREETURCHINE on 2006-11-21
ok i have beryl working now,but firefox flashes around the edge when it is loaded so do my outher windows ,
cant be a big problem just a setting somewhere ,
can anyone help me here with this,
  thanks;) ;) '

 it is around the whole window so i cant minimise or quit the window

---

### Post by catanzag on 2006-11-22
do you have window decoration? I had the same problem first time I upgrade from Compiz to Beryl, and I had no frame around any window, only some flashes some times. Then I installed emerald-themes, I remove (all) compiz, ctrl-alt-backspace to restart x server and everything now working correct.

hope this can help you

---

### Post by Random20230808 on 2006-11-22
Click on the red diamond (beryl icon) at the upper right on the screen and choose "Reload Window Decorator".
If that doesn't fix your problem right-click on the Firefox button at the taskbar and choose move.  Try to move your windows so that you can see the title bar on the screen.
Tip : Add the application > beryl-manager in "Preferences->Sessions->Startup" so that Beryl manager and Emerald Themes start during gdm startup. Press Alt+Ctrl+Backspace to restart your X session (as catanzag said) and see if it works fine.

---

### Post by STREETURCHINE on 2006-11-28
thanks all this one is resolved  :D

---

### Post by catanzag on 2006-11-28
Glad you solved all your problems and now can finally enjoy beryl!!

---

