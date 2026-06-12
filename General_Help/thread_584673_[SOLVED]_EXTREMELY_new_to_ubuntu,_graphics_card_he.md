---
title: "[SOLVED] EXTREMELY new to ubuntu, graphics card help"
date: 2007-10-21
forum: General Help
---

### Post by steve2045 on 2007-10-21
hi

brand new to ubuntu, would love some online help right now.

I have a Nvidia Graphics card in my laptop, but Ubuntu wont install it. It is a Geforce Go 7400

what steps should i take?

sorry if i am vague, im just a complete n00b is all :)

steviedee

---

### Post by PmDematagoda on 2007-10-21
Did you install Ubuntu first?

---

### Post by Nunu on 2007-10-21
The easiest way to get you card going is to install the nvidia package from Synaptic package manager. I would however recommend that you backup the XORG.CONF file before you do this. Just go to you local drive and do a search for it there. it will point you to the location of this file. just copy it to the desktop so that you can replace it in the event of something going wrong. alternatively you can also go to restricted drivers and install it from there. but BACK UP. i spent night trying to get my machine working again after the XORG file went belly up.

---

### Post by Rex_Mundi on 2007-10-21
Get [Envy]("http://albertomilone.com/nvidia_scripts1.html") Nvidia people who are using ubuntu distros < Gutsy Gibbon. Easy piecey.

---

### Post by steve2045 on 2007-10-21
MANY thanks to everyone who responded so quickly. As a windows user intrigued by ubuntu, this gives me hope!!

I have been reading other forums, and envy seems like the best way to go, so i tried to download it and install, however i get this error:

ERROR: Dependency is not satisfiable: xserver-xorg-dev

someone to guide me though this step would be great, i will be online for awhile now :)

---

### Post by steve2045 on 2007-10-21
WAIT! im using gutsy, does that change anything?

---

### Post by PmDematagoda on 2007-10-21
Do:-

```
sudo apt-get install xserver-xorg-dev

```
and try Envy again.

---

### Post by GrammatonCleric on 2007-10-21
Yes.  **[COLOR=Red]do not use Envy if you are running Gutsy[/COLOR]**.  Try installing the following...

```

apt-get install nvidia-glx-new nvidia-glx-new-dev xserver-xorg-video-nv

```There may be other packages you may need to install but start with the above.

-GC

---

### Post by steve2045 on 2007-10-21
ok, i opened up the terminal and pasted what u typed and got this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xorg-dev

---

### Post by steve2045 on 2007-10-21
i tried the other way that isnt to do with envy, this is what i got:

steve@steve:~$ apt-get install nvidia-glx-new nvidia-glx-new-dev xserver-xorg-video-nv
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by Maestro23 on 2007-10-21
> **steve2045 said:**
> ok, i opened up the terminal and pasted what u typed and got this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xorg-dev

Make sure your Universe and Multiverse Repositories are enabled.

System>> Admin>> Software Sources

---

### Post by PmDematagoda on 2007-10-21
That's not possible, it works on mine. Are you sure you tried:-

```
sudo apt-get install xserver-xorg-dev

```

If so, go to Software Sources in Administration and activate all the choices, universe, multiverse, restricted and main.

After you close Software Sources you will be asked to reload all the repos, reload them and try the command again.

---

### Post by steve2045 on 2007-10-21
ok  that seemed to do something

steve@steve:~$ sudo apt-get install xserver-xorg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xorg-dev
steve@steve:~$ sudo apt-get install xserver-xorg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xserver-xorg-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 322kB of archives.
After unpacking 1753kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main xserver-xorg-dev 2:1.3.0.0.dfsg-12ubuntu8 [322kB]
Fetched 322kB in 3s (87.7kB/s)           
Selecting previously deselected package xserver-xorg-dev.
(Reading database ... 90707 files and directories currently installed.)
Unpacking xserver-xorg-dev (from .../xserver-xorg-dev_2%3a1.3.0.0.dfsg-12ubuntu8_i386.deb) ...
Setting up xserver-xorg-dev (2:1.3.0.0.dfsg-12ubuntu8) ...

---

### Post by PmDematagoda on 2007-10-21
You have installed the necessary file, now try to use Envy.

---

### Post by steve2045 on 2007-10-21
ITS...WORKING!!!!!!!!!!!!!!!!!!!!!!!

ubuntu should come with all those boxes ticked in system sources.

but thanks to all

i actually have my mate online now, whos been an ubuntu user for awhile, so i can ask him the rest of the questions :)

thanks again, great community!

---

### Post by Maestro23 on 2007-10-21
> **steve2045 said:**
> ITS...WORKING!!!!!!!!!!!!!!!!!!!!!!!

ubuntu should come with all those boxes ticked in system sources.

but thanks to all

i actually have my mate online now, whos been an ubuntu user for awhile, so i can ask him the rest of the questions :)

thanks again, great community!

Good deal man.:guitar:

Mark this thread SOLVED using the  Thread Tools.

---

### Post by PmDematagoda on 2007-10-21
> **steve2045 said:**
> ITS...WORKING!!!!!!!!!!!!!!!!!!!!!!!

ubuntu should come with all those boxes ticked in system sources.

but thanks to all

i actually have my mate online now, whos been an ubuntu user for awhile, so i can ask him the rest of the questions :)

thanks again, great community!

Great to hear that, happy Ubuntuing:).

---

### Post by alexzzz on 2007-10-21
This helped me also.

Thanks

---

