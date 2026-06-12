---
title: "Ubuntu Studio on Soundblaster Live/"
date: 2007-12-26
forum: General Help
---

### Post by Kunks on 2007-12-26
I'm currently running Gutsy with no problems on a Dell Pentium 4,2.6 Ghz, 512 ram 128mb nvidia card,soundblaster live.....I'd like to install Ubuntu Studio & would like to know if I need to create a separate partition & run as a boot option or is it self-contained within Gutsy? Also are my specs good enough to use Ubuntu Studio without major problems(more ram?) I'm currently using Sonar 6 home studio on another box on XP.....Can you install only the audio programs or is it all or none???? I'm more interested in the audio recording aspect as opposed to the video editing......

---

### Post by Mblackwell on 2007-12-27
If you aren't interested in the desktop, and just want the apps it's possible to add the UbuntuStudio repository and get the audio metapackage, and the plugins metapackage. Then your best bet is to grab the realtime kernel package (linux-rt) and edit /etc/security/limits.conf and add something like

```

@audio - rtprio 99
@audio - memlock 250000

```

You can find more instructions on the UbuntuStudio Wiki as far as the exact repos.

You should be able to use Ardour without too many problems, as long as you get the realtime kernel, and remember to check the Realtime box in Ardour (and qjackctrl). You should be good to go with pretty low latency settings (mine is about 13ms) and no Xruns. Be aware though, that when using Ardour, especially with that amount of ram, the settings will cause audio to play and record correctly but the rest of the machine will seem sluggish once you have a lot of tracks. But, that's okay since the thing that matters is the audio.

I hope my post is intelligible. That's what I get for posting when I'm tired and still hopped up on caffeine.

---

### Post by Kunks on 2007-12-27
Hello....I don't know what  Xruns are & please explain in more detail what the real time kernel package is & why if I installed it from the terminal why would I edit it as you suggested....I a noob.......
Thanks for your help

---

### Post by Mblackwell on 2007-12-27
Ahhh, you wouldn't be editing the kernel, you'd be editing (and adding those two lines) to the config file.

Basically the realtime kernel package is a version of the linux kernel which keeps everything on a specific schedule, with the idea that tasks won't be able to bog down the OS, and that any I/O from devices will always get read on time. (note: this is the simple explanation)

By using the realtime kernel you basically allow your system to do tasks with extremely low latency, and by adding those two lines to limits.conf, you do two things:

1) Give audio a high priority when run in real time
2) Lock half of your ram when a real time audio application requests locked (reserved) memory for itself.

When you run something then like Ardour, using the realtime kernel and marking it as Realtime in the options, it will start JACK in the background (a kind of sound server), which will run all audio in real time and lock memory so sound apps won't lag.

Every time there's a lag, stutter, click, or a pop in the audio this is called an XRUN, and if you open up qjackctl (a settings control center for JACK) it will actually show you on a little console window every time they happen.

As for installing UbuntuStudio audio packages, and the kernel, you should be able to install:

```

sudo apt-get update && sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins linux-rt

```

Then you just need to edit that file I mentioned (put those lines at the bottom), restart, and you should be good to go.

Cavat: If you're using the restricted Nvidia driver, remove it before the reboot, and then reinstall it when you're done. This is because it's tied to your kernel, so when you reboot and Gnome/your desktop tries to start it won't be able to and will complain, and you'll have to change a few settings and then do what I just said anyway, so it's just part of making it easier on yourself. :)

---

### Post by Kunks on 2007-12-27
ok, I

---

### Post by Kunks on 2007-12-27
ok, so being a noob, I need the step by step....let me know if i'm off the track....
from the terminal-
sudo apt-get update . sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins linux-rt..
then through the terminal.....
edit /etc/security/limits.conf
and then right after conf (space between?)  type in or paste....
@audio - rtprio 99
@audio - memlock 250000
and then...
disable restricted drivers for nvidia card b/4 reboot,
 after reboot re-install restricted drivers...
then check the Realtime box in Ardour (andqjackctrl).
Anything else????
Thanks again for your time & effort to help... I'll let you know how thingswork ouit but I'm in retail & probably won't get on this untill the Holidaze are over.....

---

### Post by Mblackwell on 2007-12-27
In a console, do the following commands:

[i]sudo apt-get update
sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins linux-rt

sudo gedit /etc/security/limits.conf[/i]

The last will open up that file in a text editor. Scroll to the bottom of the file (which should be short) add a couple new lines, and then put in the text:

[i]@audio - rtprio 99
@audio - memlock 250000[/i]

Save and exit.
Disable/remove the Nvidia driver, reboot

Pick the *rt* kernel from the boot menu if it's not already selected at the top
log in
re-install the Nvidia driver again.

Then it will probably ask you to reboot a second time.

Now you should be on a regular desktop, with the UbuntuStudio audio software set up/installed.

Go to *Applications>Sound & Video* and you should be able to find something called JACK Control. This is qjackctl. Once it's open click *Setup* and check the *Realtime* box. Then you can click *Ok* and close the program down.

After that you're ready to start *Ardour*. Under *Sound & Video* it's listed as *Ardour GTK2*.

It will start up with a little box letting you create a new session and choose where to save it. Before you do that, though click *Audio Setup*. Click *Options*. Check the *Realtime* box. After that you should be ready to start your new session and have fun.

If you have any other problems, let me know.

---

### Post by Kunks on 2007-12-28
I got all the sound applications from Ubuntu Studio installed with no problem thanks to your guidance....
There is no option to check any box in Ardour for Realtime even in advance settings.. there is no box for audio settings/options anywhere
There is in in Jack Control & I checked & enabled it....
When I open Ardour it says that it's not connected to Jack
There was no rt kernel in the boot menu in the boot options to select at bootup after install
 When I open Jack Control these two  screenshot shows what I see....

---

### Post by Mblackwell on 2007-12-29
It's in the opening dialog for Ardour, before you even start a new session.

Also, for the realtime kernel try:

sudo apt-get install linux-rt

and see what you get. 

If it says it's already installed it's weird that when you booted you wouldn't have that option, at which point I'd then have to suggest:

sudo apt-get install linux-image-rt

Remember, if it installs and asks you to reboot, make sure you deal with the Nvidia driver before hand.

---

### Post by Kunks on 2007-12-29
I tried both your suggestions......
Everything seems to be installed properly (see 1st screenshot)
Still can't find the real time box to check in Ardour (see 2nd screenshot)
Any ideas where to go next????

---

