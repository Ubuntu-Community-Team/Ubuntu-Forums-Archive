---
title: "Make sure you have both the Universe and Multiverse repositories enabled"
date: 2006-12-08
forum: General Help
---

### Post by broekskw on 2006-12-08
trying to install my video driver. in the guide that i am useing the first thing i need to do is 
Make sure you have both the Universe and Multiverse repositories enabled how do i do this

---

### Post by taurus on 2006-12-08
Remove the # sign in front of those lines in /etc/apt/sources.list...

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by yabbadabbadont on 2006-12-08
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Edit: just for some more information.

---

### Post by kerry_s on 2006-12-08
Synaptic> settings> repositores
or
in terminal
gksu gedit /etc/apt/sources.list
uncomment(#) the lines starting with deb

---

### Post by broekskw on 2006-12-08
thanks all for your help. so took out all the # and saved file

---

### Post by taurus on 2006-12-08
Then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by broekskw on 2006-12-08
ok did something wrong. after taking out all the # and then running  sudo aptitude update i get this error

broekskw@broekskw-desktop:~$ sudo aptitude update
E: Type 'Major' is not known on line 5 in source list /etc/apt/sources.list
E: Type 'Major' is not known on line 5 in source list /etc/apt/sources.list
E: The list of sources could not be read.
broekskw@broekskw-desktop:~$ 

help

---

### Post by broekskw on 2006-12-08
here is my screen shopt of my gksu gedit /etc/apt/sources.list

---

### Post by yabbadabbadont on 2006-12-08
You should only have removed the # from the lines that start with "deb".  :D

Edit: or "deb-src" (which starts with deb now that I type it out...  ;))

---

### Post by taurus on 2006-12-08
Don't remove the # from every single line!!!  Some of them are comments which mean they need to have a # in front.  Paste your /etc/apt/sources.list here and I will correct it for you them...

```
cat /etc/apt/sources.list
```

---

### Post by broekskw on 2006-12-08
boy you guys are life savers

broekskw@broekskw-desktop:~$ cat /etc/apt/sources.list

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted

   Major bug fix updates produced after the final release of the
   distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

   Uncomment the following two lines to add software from the 'universe'
   repository.
   N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
   team, and may not be under a free licence. Please satisfy yourself as to
   your rights to use the software. Also, please note that software in
   universe WILL NOT receive any review or updates from the Ubuntu security
   team.
  deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
  deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

   Uncomment the following two lines to add software from the 'backports'
  repository.
   N.B. software from this repository may not have been tested as
   extensively as that contained in the main release, although it includes
   newer versions of some applications which may provide useful features.
   Also, please note that software in backports WILL NOT receive any review
   or updates from the Ubuntu security team.
  deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
  deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
broekskw@broekskw-desktop:~$

---

### Post by yabbadabbadont on 2006-12-08
Just edit the file and add # to the beginning of every line that doesn't start with "deb" or "deb-src".  Then you should be able to update again.

---

### Post by taurus on 2006-12-08
Here's your new /etc/apt/sources.list...

```

deb http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted

#Major bug fix updates produced after the final release of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

#Uncomment the following two lines to add software from the 'universe' repository.
#N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu team,
#and may not be under a free licence. Please satisfy yourself as to
#your rights to use the software. Also, please note that software in
#universe WILL NOT receive any review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy universe

#Uncomment the following two lines to add software from the 'backports' repository.
#N.B. software from this repository may not have been tested as
#extensively as that contained in the main release, although it includes
#newer versions of some applications which may provide useful features.
#Also, please note that software in backports WILL NOT receive any review
#or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```
Save it and run these two commands again...

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by broekskw on 2006-12-08
ok did that and now the first one is updating thanks again and next time if i am not to sure about the commands will ask more questions
again thanks all:mrgreen:

---

### Post by broekskw on 2006-12-08
ok followed the install, but how do i find out if the driver installed and a icon on my decktop:mrgreen:

---

### Post by taurus on 2006-12-08
You only mentioned you needed to install a driver for your graphic card but you never said which graphic card do you have!  Anyway, here is a guide for both nvidia and ati...

[http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

p.s.  Nvidia first and ati after that.

---

### Post by broekskw on 2006-12-08
sorry for this but i have followed that one to the t nvidia gfx5200-t128 agp
looking for a setup on application . i did have that once before before i screwed up my system and had to do 2 reinstalls yes i have nothing better to do on this friday:)

---

### Post by taurus on 2006-12-08
If you want to install an nVidia driver for your card, then do

```
sudo aptitude update
sudo aptitude install nvidia-glx
sudo nvidia-xconfig
```
<Ctrl><Alt>Backspace to re-start X at which point you should see an nVidia logo...

---

### Post by broekskw on 2006-12-08
again taurus thanks for all your help, also how do i get the nvidia program setup in my applications>system tools window so i can tweek the setting
thanks:mrgreen:

---

### Post by taurus on 2006-12-08
```
sudo aptitude install nvidia-settings
```

---

### Post by broekskw on 2006-12-09
ok taurus this is the second time that this has happend to me after running your commands
sudo aptitude install nvidia-settings

i do a restart after this to see if i get a icon under system tool,after the restart before the ubuntu logo (it never comes up)i get a error screen about my display not setup correctly and ask me to see the report to find out how to fix it, witch i have no clue on fixing, so after  this screen i get on a black screen my ubunto login and passord enteries so i log into but all it is,it's like i am stuck in a terminal screen.

now i am not angery with this because this is how i or other find out solutions to problems like this

the other time this happend i did a reinstall,but this time if i can type the correct command into this screen i thing i could get back into it.

so agian thanks for any reply:mrgreen: :mrgreen:

---

### Post by taurus on 2006-12-09
Didn't nvidia work when you restarted X with <Ctrl><Alt>Backspace?

Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

---

### Post by broekskw on 2006-12-09
ok gave that a try but no luck. keeps going to that screen saying my video is corrupt.

3 time install, getting good at install but not at driver install:cool:

---

### Post by kerry_s on 2006-12-09
> **taurus said:**
> ```
sudo aptitude install nvidia-settings
```

You don't need that it's now part of nvidia-glx you run the settings from command line or make the launcher. If install it screws up nvidia.

---

### Post by kerry_s on 2006-12-09
On a fresh install just do->
apt-get install nvidia-glx
Then just edit xorg.conf->
sudo gedit /etc/X11/xorg.conf
	Driver		"nv"
to
	Driver		"nvidia"
save
then
ctrl+alt+backspace
(reboot if it install a new kernel)

---

### Post by broekskw on 2006-12-09
thanks kerry_s ok did that on a new install and loaded the driver no problem, still have no icon in system tools to open nvidia window but thats ok

now in the fresh install after everything is installed it tells you to take out the cd and reboot, after i did that and the system tried to reboot in a diff screen i had 4 errors come up that i did not write down and the only way to get it to reboot was to hit the reset button,then on reboot just before the ubunto logo screen i have another error message "acpi unable to locate rsdp"  can anyone tell me what all this means,

this coud be part of my problem installing my video and my sound card, missing some files.
i also installed this same cd on another computer with no problem,everything worked great,video,sound, all installed right away:mrgreen:

---

### Post by kerry_s on 2006-12-09
Does the system your getting the errors on have acpi or is it a older system that uses apm? You can try adding> noacpi to the boot line.->
in terminal
sudo gedit /boot/grub/menu.lst
add noacpi to the end of the kernel line, looks like this->
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdb1 ro quiet splash noacpi


Also for each new problem can you start a new thread & make sure you include your specs, try to include as much detail as you can. It makes it easier for people who use the search feature to find answers to the same problem, its hard to tell what the answers are in mixed threads that go on for pages. Thanks

---

### Post by broekskw on 2006-12-09
just got home from work. ok first of" acpi or is it a older system that uses apm?" what does the acpi and the apm stand for. yes it is a older system with an adapter on the cpu to make it run like a 1.4 cpu. power leap adapter.
ok will start a new thread about error with all mt specs

thanks:mrgreen:

---

